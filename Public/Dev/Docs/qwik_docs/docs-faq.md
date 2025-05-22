# https://qwik.dev/docs/faq/

[Original link](https://qwik.dev/docs/faq/)

# FAQ

## Is @QwikDev a sentient AI?

Yes, and I am very funny too! follow me

## Why is it called Qwik?

Originally it was called qoot, but we thought it would be too hard to search for. One community member, @PatrickJS__, came up with Qwik and after an internal poll at builder.io, we changed it!

## How is Qwik different from other frameworks?

Qwik is the first framework that has a DX (developer experience) similar to React, Vue, or Svelte when authoring components. It delivers Live HTML that is instantly interactive, Qwik achieves this property by completely removing the need for hydration. Now, Qwik applications immediately execute the event handlers on user interaction, without having to bootstrap all the app states. This technique is called Resumability.

The outcome is that developers write extremely performant applications by default, without even worrying about it. Applications built with Qwik are fast regardless of the number of components or complexity, they are O(1) (constant time) in terms of JS payload.

## Why another framework?

The short answer is that Qwik solves a problem that other frameworks can't solve. Qwik has instant-on startup performance no matter how complex the application is. Qwik apps deliver the same amount of initial JS regardless of the amount of components. Qwik is the first open-source O(1) framework.

## What is Qwik City?

Qwik City is just an extra set of APIs on top of Qwik. Think of it like Qwik as the core, and City as the extra APIs (routing, data loading, endpoints, etc.). We call it a meta-framework for Qwik. Qwik City is to Qwik, what Next.js is to React, what Nuxt is to Vue, or SvelteKit to Svelte.

## Is Qwik hard to learn?

Qwik is designed with React (and other JSX based frameworks) in mind, ensuring it is effortless to learn and promotes rapid productivity. Developing components is pretty much the same as React, and routing is inspired by Nextjs and others.

However, there are fundamentally new concepts to learn, such as Resumability and fine-grained reactivity, but we think the learning curve is not steep.

We also have an interactive tutorial to get you started.

## What are all those $ signs?

You might have noticed there are more $ signs than usual in Qwik apps, such as: component$(), useTask$(), and <div onClick$={() => console.log('click')} />. It serves as a marker for a lazy-load boundary. Qwik breaks your application into small chunks; these pieces are smaller than the component itself. For event handlers, hooks, etc. The $ signals to both the optimizer and the developer when it's happening.

Example:

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  console.log('render');
  return <button onClick$={() => console.log('hello')}>Hello Qwik</button>;
});
```

Thanks to the $ syntax, the component above is split into:

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
  return /*#__PURE__*/ _jsx('p', {
    onClick$: qrl(
      () => import('./app_component_p_onclick_01pegc10cpw'),
      'App_component_p_onClick_01pEgC10cpw'
    ),
    children: 'Hello Qwik',
  });
};
```

```
export const App_component_p_onClick_01pEgC10cpw = () => console.log('hello');
```

Note: The $ is not related to jQuery, Svelte or any other framework.

## Isn't requesting JS on user interaction slow?

Only if you download it on user interaction. Instead, Qwik prefetches the current page's JS modules in a background thread through the service workers and retrieves those modules from the browser's Cache when the user interacts with the application.

This strategy is called Speculative Module Fetching, and it is enabled by Resumability. Hydration frameworks must eagerly download and execute the code on page load to retrieve the event handlers, and therefore can't take advantage of speculative module fetching.

## How does Qwik know what to prefetch, and in which order?

In production, Qwik uses a lot of information generated during SSR (Server-Side Rendering) to start pre-populating the cache as soon as possible, with only the bits of interactivity available on the current page. This way, when the user clicks or interacts, the JS is already in the cache.

In addition, Qwik insights can be used to prioritize the important parts of interactivity before the less important parts.

For example, the "Buy Now" button is more important than the "Add to Cart" button, so Qwik will prefetch the "Buy Now" button first, and then the "Add to Cart" button.

## Are Qwik apps slow on slow networks?

Quite the opposite.

Qwik does not need to prefetch everything to start running, while other frameworks do need to download the whole critical path to become interactive because of hydration.

In fact, thanks to Qwik's ability to reduce network waterfalls, it is likely that the requested modules have already been downloaded and stored in the browser's cache at the time of interaction. And even if they haven't yet been cached, Qwik can avoid duplicating the requests and can instead keep fetching the modules that are being requested to start executing them as soon as possible.

As a result, Qwik apps get to be responsive much faster, especially on slow networks.

## Does Qwik generate too many small files?

In dev mode, Qwik generates a lot of small files because it uses the Dev Vite.js server, but in production mode, Qwik bundles files more efficiently.

## Why does Qwik use JSX? Is it React under the hood?

Nope, React is not used at all. Qwik uses JSX as the template syntax.

Notice that JSX is not React. In fact, JSX is only syntax without semantics. We chose JSX for several reasons:

## Does Qwik use a vDOM (Virtual DOM)?

Qwik uses vDOM only sometimes, and other times it does what SolidJS does (direct DOM update.)

The way to think about it is as follows:

If the change in state does not have a structural change then Qwik will most likely not use vDOM. For example:

```
export const NoStructuralChange = component$(() => {
  const count = useSignal(0);
 
  return (
    <>
    {/* This will not cause vDOM to activate. (No DOM structure change, only update text value) */}
     <div>Count: {count.value}</div>
     <button onClick$={() => count.value++}>+1</button>
    </>
  );
});
```

When there is a structural change, Qwik utilizes the virtual DOM (vDOM). In the following example, the DOM structure needs to be updated (replace <h1> with <button>), so vDOM will be used for rendering:

```
export const StructuralChange = component$(() => {
  const isLoggedIn = useSignal(false);
  return (
    <div>
      {isLoggedIn.value ? <h1>you are logged in!</h1> : <button>Log in</button>}
    </div>
  )
});
```

The important thing to understand is that vDOM doesn't cause performance issues in Qwik. In React, however, invalidating a root component results in vDOM for the whole tree getting created. In Qwik, the decision is made on a per-component basis.  And only for components that have structural change AND are changing their structure. If a component is structural (vDOM) but no change in structure is detected, then Qwik skips the component. You can think of it as auto-memoization of all components, this means that vDOM is only employed when the view is changing structurally. This is rare because in most cases the view only changes its values.

In short, Qwik uses vDOM, but significantly less than React in comparable situations.

### Why use a vDOM despite its negative reputation?

The question of whether or not to use a vDOM can be seen as a spectrum:

Qwik on the other hand uses a vDOM sparingly for two reasons:

For example:

```
const DynamicList = [ CompA, CompB, ...];
export const DynamicExample = component$(() => {
  const idx = Math.floor(Math.random() * DynamicList.length);
  const Component = DynamicList[idx];
  {/* Dynamically chose which component to render */}
  return <Component/>; 
})
```

The above code <Component/> is super easy to understand. We are dynamically choosing a component to place there. But in Solid, Svelte, Vue, and Angular, this gets complex (see links).

We have the best of both worlds by using a vDOM sparingly. During creation, we employ SSR, and most client updates are non-structural. When structural updates are necessary, they are localized to the specific component without affecting its children, thus containing any potential slowdown caused by vDOM.

## Is there a Router for Qwik?

Yes! Qwik City includes a directory-based router, inspired by Next.js and others.

## Do I need a server to deploy Qwik apps?

You can easily deploy a Qwik app in any serverless environment thanks to our adapters. We also support a vanilla-node adapter for Node.js-based servers, such as Express.

If there is no need for SSR, you can deploy your Qwik app as a static site thanks to our SSG (Static Site Generation) adapter.

## Which is faster: SPAs (Single-Page Application) or MPAs (Multi-Page Application)?

It depends. For SPAs, most of the cost is paid upfront by downloading everything at the beginning of the session. So when a user interacts with the app, the cost is minimal.

MPAs are extremely fast to load as they don't need to download as much JS as their SPA counterparts. However, when the user navigates, it usually requires a full page reload. A full-page reload is typically super fast because browsers are extremely fast at downloading and parsing HTML. But, since sometimes, it's ideal to keep state between navigation, the MPA approach is not ideal for every project. In this case, SPA does that very well.

Qwik is a unique framework that is both an MPA and an SPA at the same time.

## Can Qwik do SPA?

Of course! Qwik City includes the <Link> component which triggers an SPA navigation.
With Qwik, developers don't need to choose between an SPA or an MPA, every app is both at the same time.

MPA vs SPA is no longer an architectural decision taken at the beginning of the project, but a decision made for every link.

## Can Qwik do Static Site Generation (SSG)?

Yes! It's part of all Qwik City starters. Learn how to do Static Site Generation here.

## Can't I create an MPA or SPA with other frameworks?

Not quite, other frameworks suggest removing all the <Scripts> at the root to generate an MPA, effectively removing all the interactivity along with the SPA navigation.

And if scripts are not removed, then each full-page reload becomes very expensive, because every page reload means that the framework needs to hydrate the entire page. Qwik, however, does not have a hydration cost for each page load.

## Will migrating to Qwik require a lot of effort?

It depends. If you are coming from React, porting your components to Qwik should be straight forward. But on top of that, thanks to Qwik React, you can use all of the React ecosystem, so you can use any of your React components, and any React library in a Qwik app.

## Can I enjoy the rich React ecosystem?

Yes! Qwik can run React components natively, check out the docs.

You will be amazed!

## Does Qwik do partial hydration?

No. Partial hydration (or island architecture), popularized by Astro, is about breaking the app into islands of interactivity to avoid full-page hydration, where all existing components in the page need to be downloaded and executed.

For this to work, developers need to manually define the islands, and then manually describe in which situations they should be hydrated. The islands also cannot communicate with each other.

Instead, Qwik components do not hydrate at all. Qwik achieves this through a powerful serialization system that serializes only the necessary state in the reactivity graph. This way, the app can resume without eagerly running any JS.

We think resumability scales without the negative trade-offs of partial hydration.

## In which languages is Qwik written?

Most of Qwik is written in TypeScript, a superset of JavaScript that adds optional static typing and other features. However, the Qwik compiler (or optimizer) is written in Rust, a language that is very fast and memory efficient.

## Does Qwik have a community?

Yes! there is a growing community of Qwik developers at Discord and GitHub. They are making amazing contributions to the framework, building sites at scale, and helping each other. Join us.

## Is Qwik an "Alex Russell Approved" framework?

Yes! Alex Russell (@slightlylate), known for his contributions to PWAs, W3C TAG, WC, TC39 & ES6, Chrome Frame, Dojo, and more, is often highly critical of JavaScript frameworks. Nonetheless, he approves of Qwik.

## Is Qwik production ready?

Yes! Qwik is already at version 1.1. Qwik has been in development for 3 years now. We are confident that Qwik is ready for production, and there are no expected breaking changes.

Builder.io and a lot of teams are already using Qwik in production, so you will not be alone.

## Is it true that Qwik serializes too much data in the HTML?

False. Qwik serializes only the data that is needed for the current page. If a page has 1000 components but only one is interactive the amount of data serialized is proportional to the amount of interactivity, not the amount of components.

## Who builds Qwik?

An amazing team of contributors around the world living in Discord, and a few full time developers at Builder.io: Misko, Adam and Manu Almeida.

## Is Qwik open source?

Yes, MIT and dependency-free, installing Qwik will not bloat your node_modules nor your lawyers.

## Does Qwik have any downsides?

Yes. Every framework, possessing its own strengths and weaknesses, involves a trade off.

We are constantly working on improving the developer experience and capabilities to make Qwik more delightful to use for any use case, so stay tuned.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
