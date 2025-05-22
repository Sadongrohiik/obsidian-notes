# https://qwik.dev/docs/advanced/containers/

[Original link](https://qwik.dev/docs/advanced/containers/)

# Containers

Every Qwik application is contained inside a element, usually the <html> element. This element becomes the container for the application. The container is the root element for the application and all components, state and events are contained within.

```
<html
  q:container="paused"
  q:version="1.9.0"
  q:render="ssr"
  q:base="/build/"
  q:manifest-hash="ggb7b3"
  q:instance="b0yf84vwuup"
>
  ...
</html>
```

## Container Attributes

Since containers are implicitly rendered by the Qwik runtime, it's not possible to define custom HTML attributes using JSX, however, the SSR render APIs, like renderToString and renderToStream, provide the containerAttributes option to define custom attributes:

```
renderToStream(<Root />, {
  containerAttributes: {
    lang: 'en',
  },
});
```

The code above will render the following HTML:

```
<html lang="en" q:container="paused" q:version="1.9.0" q:base="/build/">
  ...
</html>
```

In the example above, the lang attribute is added to the <html> container element.

Note that this attribute will not be reactive, if the app needs to change this value dynamically, it will need to do through manual DOM manipulation.

Along with the custom attributes, Qwik will automatically render the q:container, q:version, q:render and q:base attributes.

q:container - The container state. This attribute is used by the Qwik runtime to determine if the container is in a paused state or not. The value of this attribute is either paused or resumed.

q:version - The version of the Qwik runtime.

q:render - Indicated how the container was rendered. The value of this attribute is either ssr, ssr-dev, dom or dom-dev.

## Properties

Since the runtime ensures isolation across containers, several containers can coexist within the same document, a container can even contain another nested container, this property allows containers to break up an application into smaller parts.

Containers can be nested in a tree and can communicate and share data. The inter-component communication requires that the components have well-defined boundaries, which we call container protocols.

```
<html q:container="paused" q:version="1.9.0" q:base="/build/">
  <head>
    <title>My Qwik Application</title>
  </head>
  <body>
    <header q:container="resumed" q:version="1.8.0" q:base="https://server.a/build">
      <div>
        <h1>This is a header form a container</h1>
      </div>
    </header>
 
    <footer q:container="paused" q:version="0.13.0" q:base="https://footer.server.b/">
      <div>
        <h1>This is a footer</h1>
      </div>
    </footer>
  </body>
</html>
```

## Containers vs. Components

Containers sound very similar to components; what are the differences? You can think of a container as a more restricted component. However, components can do a few things which containers can't.

Components have restrictions:

## What do containers solve?

Containers allow multiple independent Qwik applications to run on the page and behave as a single application to the user. There are two most common use cases:

### Routing

A typical site is composed of two logical parts:

We can model the two parts as two navigation and outlet containers. When the user first navigates to a route, the server responds with HTML, that contains containers for both the navigation and the outlet. Once the user navigates to the second route, there are three ways to solve the navigation:

### Micro-frontend

When an application gets very large, it becomes impractical to think of it as a single application. A better mental model is that many applications work together to give the user the impression of a single application.

For large apps, the teams also become large. Large teams usually have different goals and, as a result, different release schedules.

Containers allow a large team to break up the application into many smaller parts and treat each part as a unit with a separate deployment, testing, and version upgrade schedule.

Teams break up the application into containers and clearly define protocols between the containers. As long as the protocols are satisfied, each team can deploy the two containers independently.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
