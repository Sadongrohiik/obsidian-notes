# https://qwik.dev/docs/advanced/qrl/

[Original link](https://qwik.dev/docs/advanced/qrl/)

# QRL

QRL (Qwik URL) is a particular form of URL that Qwik uses to lazy load content.

QRLs:

## QRL Encoding

```
./path/to/chunk.js#SymbolName
```

In its simplest form, the QRL contains a URL (such as ./path/to/chunk.js) that the browser can use to lazy-load a resource, and a SymbolName to retrieve from the lazy-loaded chunk.

Qwik uses q:base to resolve a QRL into an absolute URL if the URL is relative. (If no q:base attribute is present, then document.baseURI is used as a base.)

## Encoding lexically scoped captured variables

QRLs can also restore lexically scoped variables. In that case, the variables are encoded in the QRL at the end in the form of an array of indexes into the q:obj attribute.

```
./path/to/chunk.js#SymbolName[0,1]
```

The array is used by useLexicalScope() to restore the variables.

### Example

Let's look at an example of how all of the pieces of the QRL tie together.

The developer writes code for a simple component.

```
export const Counter = component$((props: { step: number }) => {
  const count = useSignal(0);
 
  return <button onClick$={() => (count.value += props.step || 1)}>{count.value}</button>;
});
```

The optimizer breaks above code into pieces like so:

```
const Counter = component(qrl('./chunk-a.js', 'Counter_onMount'));
```

```
export const Counter_onMount = (props) => {
  const count = useSignal(0);
  return qrl('./chunk-b.js', 'Counter_onRender', [count, props]);
};
```

```
const Counter_onRender = () => {
  const [count, props] = useLexicalScope();
  return (
    <button onClick$={qrl('./chunk-c.js', 'Counter_onClick', [count, props])}>{count.value}</button>
  );
};
```

```
const Counter_onClick = () => {
  const [count, props] = useLexicalScope();
  return (count.value += props.step || 1);
};
```

### Rendered HTML

After the above code gets executed, it produces this HTML.

Assume: http://localhost/index.html

```
<html>
  <body q:base="/build/">
    <button q:obj="456, 123" on:click="./chunk-c.js#Counter_onClick[0,1]">0</button>
    <script>
      /*Qwikloader script*/
    </script>
    <script type="qwik/json">
      {...json...}
    </script>
  </body>
</html>
```

The main thing to note is the on:click attribute. This attribute gets read by the Qwikloader when the user clicks on the button.

```
const Counter_onClick = () => {
  const [count, props] = useLexicalScope();
  return (count.value += props.step || 1);
};
```

NOTE: For performance reasons the q:obj and <script type="qwik/json"> are only updated when the application is deserialized into HTML. When the application is running, these attributes may have stale values.

## Why not just dynamic import()?

Browsers already have dynamic import mechanisms available from import(). Why not use that instead of inventing a new QRL format?

There are several reasons:

Because of the above differences, Qwik introduces QRLs as a mechanism for lazy loading closures into a Qwik application.

## See Also

### Contributors

Thanks to all the contributors who have helped make this documentation better!
