# https://qwik.dev/docs/advanced/dollar/

[Original link](https://qwik.dev/docs/advanced/dollar/)

# The dollar $ sign

Qwik splits up your application into many small pieces we call symbols. A component can be broken up into many symbols, so a symbol is smaller than a component. The splitting up is performed by the Qwik Optimizer.

The $ suffix is used to signal both the optimizer and the developer when this transformation occurs. As a developer, you need to understand that special rules apply whenever you see $ (not all valid JavaScript is a valid Qwik Optimizer transform.)

## Compiler-time implications

The optimizer runs as a Vite plugin during bundling. The purpose of the Optimizer is to break up the application into many small lazy-loadable chunks. The Optimizer moves expressions (usually functions) into new files and leaves behind a reference pointing to where the expression was moved from.

The $ tells the optimizer which functions to extract into a separate file and which ones to leave untouched. The optimizer does not keep an internal list of magic functions, instead, it solely relies on the $ suffix to know which functions to transform. The system is extendable and developers can create their own $ functions, such as myCustomFunction$().

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  console.log('render');
  return <button onClick$={() => console.log('hello')}>Hello Qwik</button>;
});
```

The component above is split into multiple chunks thanks to the $ syntax:

```
import { componentQrl, qrl } from '@builder.io/qwik';
 
const App = /*#__PURE__*/ componentQrl(
  qrl(() => import('./app_component_akbu84a8zes.js'), 'App_component_AkbU84a8zes')
);
 
export { App };
```

```
import { jsx as _jsx } from '@builder.io/qwik/jsx-runtime';
import { qrl } from '@builder.io/qwik';
export const App_component_AkbU84a8zes = () => {
  console.log('render');
  return /*#__PURE__*/ _jsx('button', {
    onClick$: qrl(
      () => import('./app_component_button_onclick_01pegc10cpw'),
      'App_component_button_onClick_01pEgC10cpw'
    ),
    children: 'Hello Qwik',
  });
};
```

```
export const App_component_button_onClick_01pEgC10cpw = () => console.log('hello');
```

## Rules

The Optimizer uses $ as a signal to extract the code. The developer needs to understand that the extraction comes with constraints and therefore special rules apply whenever the $ is present. (Not all valid JavaScript code is valid code for the Optimizer.)

The worst kind of code magic is the kind that's invisible to the developer.

### Allowed expressions

The first argument of any function that ends with $ has certain restrictions:

#### Literals without local identifiers

```
const bar = 'bar';
const foo = 'foo';
 
// Invalid expressions
foo$({ value: bar }); // it contains a local identifier "bar"
foo$(`Hello, ${bar}`); // it contains a local identifier "bar"
foo$(count + 1); // it contains a local identifier "count"
foo$(foo); // foo is not exported, so it's not importable
 
// Valid expressions
foo$(`Hello, bar`); // string literal without local identifiers
foo$({ value: 'stuff' }); // object literal without local identifiers
foo$(1 + 3); // expression without local identifiers
```

#### Importable identifiers

```
// Invalid
const foo = 'foo';
foo$(foo); // foo is not exported, so it's not importable
 
// Valid
export const bar = 'bar';
foo$(bar);
 
// Valid
import { bar } from './bar';
foo$(bar);
```

#### Closures

For closures, the rules are a bit relaxed, and local identifiers can be referenced and captured.

RULE: If a function lexically captures a variable (or parameter), that variable must be:

Invalid

```
component$(() => {
  let foo = 'value'; // variable is not a const
  return <div onClick$={() => console.log(foo)}/>
});
```

Valid

```
component$(() => {
  const foo = 'value';
  return <div onClick$={() => console.log(foo)}/>
});
```

```
// Invalid
component$(() => {
  const foo = new MyCustomClass(12); // MyCustomClass is not serializable
  return <div onClick$={() => console.log(foo)}/>
});
 
// Valid
component$(() => {
  const foo = { data: 12 };
  return <div onClick$={() => console.log(foo)}/>
});
```

If a function that is being extracted by the Optimizer refers to a top-level symbol, that symbol must either be imported or exported.

```
// Invalid
const foo = new MyCustomClass(12);
component$(() => {
  // Foo is declared at the module level, but it's not exported
  console.log(foo);
});
 
// Valid
export const foo = new MyCustomClass(12);
component$(() => {
  console.log(foo);
});
 
// Valid
import { foo } from './foo';
component$(() => {
  console.log(foo);
});
```

## Deep dive

Let's look at the hypothetical problem of acting on a scroll event. You may be tempted to write the code like so:

```
function onScroll(fn: () => void) {
  document.addEventListener('scroll', fn);
}
onScroll(() => alert('scroll'));
```

The problem with this approach is that the event handler is eagerly loaded, even if the scroll event never triggers. What is needed is a way to refer to code in a lazy loadable way.

The developer could write:

```
export scrollHandler = () => alert('scroll');
 
onScroll(() => (await import('./some-chunk')).scrollHandler());
```

This works but is a lot of work. The developer is responsible for putting the code in a different file and hard coding the chunk name. Instead, we use the Optimizer to perform the work for us automatically. But we need a way to tell the Optimizer that we want to perform such a refactoring. We use $() as a marker function for this purpose.

```
function onScroll(fnQrl: QRL<() => void>) {
  document.addEventListener('scroll', async () => {
    const fn = await fnQrl.resolve();
    fn();
  });
}
 
onScroll($(() => alert('scroll')));
```

The Optimizer will generate:

```
onScroll(qrl('./chunk-a.js', 'onScroll_1'));
```

```
export const onScroll_1 = () => alert('scroll');
```

However, wrapping code in $() is a bit inconvenient. For this reason, one can use implicit$FirstArg() to automatically perform the wrapping and type matching of the function taking the QRL. The function passed into implicit$FirstArg() should have a suffix of Qrl, and the result of that function should be set to a value with a suffix of $;

```
const onScroll$ = implicit$FirstArg(onScrollQrl);
 
onScroll$(() => alert('scroll'));
```

Now the developer has an easy syntax for expressing that a particular function should be lazy-loaded.

## Symbol extraction

Assume that you have this code:

```
export const MyComp = component$(() => {
  /* my component definition */
});
```

The Optimizer breaks the code up into two files:

The original file:

```
const MyComp = component(qrl('./chunk-a.js', 'MyComp_onMount'));
```

and a chunk

```
export const MyComp_onMount = () => {
  /* my component definition */
};
```

The result of Optimizer is that the MyComp's onMount method was extracted into a new file. There are a few benefits to doing this:

## Capturing the lexical scope

The Optimizer extracts expressions (usually functions) into new files and leaves behind a QRL pointing to the lazy-loaded location.

Let's look at a simple case:

```
export const Greeter = component$(() => {
  return <div>Hello World!</div>;
});
```

this will result in:

```
const Greeter = component(qrl('./chunk-a.js', 'Greeter_onMount'));
```

```
const Greeter_onMount = () => {
  return qrl('./chunk-b.js', 'Greeter_onRender');
};
```

```
const Greeter_onRender = () => <span>Hello World!</span>;
```

The above is for simple cases where the extracted function closure does not capture any variables. Let's look at a more complicated case where the extracted function closure lexically captures variables.

```
export const Greeter = component$((props: { name: string }) => {
  const salutation = 'Hello';
 
  return (
    <div>
      {salutation} {props.name}!
    </div>
  );
});
```

The naive way to extract functions will not work.

```
const Greeter = component(qrl('./chunk-a.js', 'Greeter_onMount'));
```

```
const Greeter_onMount = (props) => {
  const salutation = 'Hello';
  return qrl('./chunk-b.js', 'Greeter_onRender');
};
```

```
const Greeter_onRender = () => (
  <div>
    {salutation} {props.name}!
  </div>
);
```

The issue can be seen in chunk-b.js. The extracted function refers to salutation and props, which are no longer in the lexical scope of the function. For this reason, the generated code must be slightly different.

```
const Greeter_onMount = (props) => {
  const salutation = 'Hello';
  return qrl('./chunk-b.js', 'Greeter_onRender', [salutation, props]);
};
```

```
const Greeter_onRender = () => {
  const [salutation, props] = useLexicalScope();
 
  return (
    <div>
      {salutation} {props.name}!
    </div>
  );
};
```

Notice two changes:

The ability for the Optimizer (and Qwik runtime) to capture lexically scoped constants significantly improves which functions can be extracted into lazy-loaded resources. It is a powerful tool for breaking up complex applications into smaller lazy-loadable chunks.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
