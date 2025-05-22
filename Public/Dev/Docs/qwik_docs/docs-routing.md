# https://qwik.dev/docs/routing/

[Original link](https://qwik.dev/docs/routing/)

# Routing

Routing in Qwik City is file-system based like Next.js, SvelteKit, SolidStart or Remix. Files and directories in the src/routes have a role in the routing of your application.

## Directory-based routing

Only the directory names are used to match the incoming requests to pages/endpoint/middleware.

For example, if you have a file at src/routes/some/path/index.tsx, it will be mapped to the URL path https://example.com/some/path.

```
src/
└── routes/
    ├── contact/
    │   └── index.mdx         # https://example.com/contact
    ├── about/
    │   └── index.md          # https://example.com/about
    ├── docs/
    │   └── [id]/
    │       └── index.ts      # https://example.com/docs/1234
    │                         # https://example.com/docs/anything
    ├── [...catchall]/
    │   └── index.tsx         # https://example.com/anything/else/that/didnt/match
    │
    └── layout.tsx            # This layout is used for all pages
```

### Dynamic route segments

Special named directories with square brackets, such as [paramName] and [...catchAll] can be used to match route segments which are dynamic:

```
src/routes/blog/index.tsx → /blog
src/routes/user/[username]/index.tsx → /user/:username (/user/foo)
src/routes/post/[...all]/index.tsx → /post/* (/post/2020/id/title)
```

```
src/
└── routes/
    ├── blog/
    │   └── index.tsx         # https://example.com/blog
    ├── post/
    │   └── [...all]/
    │       └── index.tsx     # https://example.com/post/2020/id/title
    └── user/
        └── [username]/
            └── index.tsx     # https://example.com/user/foo
```

The folder [username] can be any of the thousands of users that you have in your database. It would be impractical to create a route for each user. Instead, you need to define a Route Parameter (a part of the URL) that will be used to extract the [username].

```
import { component$ } from '@builder.io/qwik';
import { useLocation } from '@builder.io/qwik-city';
 
export default component$(() => {
  const loc = useLocation();
  return <div>Hello {loc.params.username}!</div>;
});
```

## index files

Inside the src/routes directory, all files named index are considered pages/endpoint/middleware, Qwik supports the following extensions: .ts, .tsx, .md and .mdx.

Pages/endpoint/middleware are the leaf nodes of the routing tree, i.e., the modules that will handle the request and return an HTTP response.

### Page index.tsx

When an index.tsx or index.ts file exports a Qwik component as the default export, Qwik City will render the component and return an HTML response as a webpage.

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  return <h1>Hello World</h1>;
});
```

### Endpoint index.ts

An index.ts file can access the HTTP request directly and return a raw HTTP response without involving any Qwik Component. This is done by exporting any of the following methods: onRequest, onGet, onPost, onPut or onDelete depending on how you want to handle a specific HTTP request.

```
import type { RequestHandler } from '@builder.io/qwik-city';
 
export const onGet: RequestHandler = ({ json }) => {
  json(200, { message: 'Hello World' });
};
```

Notice that in the last example, there is no default export. This is because you are not rendering a Qwik component, but rather you are handling the request directly and returning a JSON response. This is useful for implementing RESTful APIs or any other type of HTTP endpoint.

### Page + Endpoint

In Qwik City there is no clear separation between pages and endpoints. An index.tsx file handles both and exports a Qwik component or an onRequest method. However, it's possible to combine both approaches. For example, you can export an onRequest method that will handle the request, and then render a Qwik component.

```
import { component$ } from '@builder.io/qwik';
import type { RequestHandler } from '@builder.io/qwik-city';
 
export const onRequest: RequestHandler = ({ headers, query, json }) => {
  headers.set('Cache-Control', 'private');
  if (query.get('format') === 'json') {
    json(200, { message: 'Hello World' });
  }
};
 
export default component$(() => {
  return <h1>Hello World</h1>;
});
```

In this example, a request handle will always set the Cache-Control header to private and the page will be rendered as an HTML page, but if the request contains a format=json query param, the endpoint will return a JSON response instead.

## layout.tsx files

Layout modules are very similar to index files. Both can handle requests and render Qwik components. However, layouts are designed to work like middleware, allowing to share UI and request handling (middleware) to a set of routes.

Usually, different pages need some common request handling and share some UI. For example, picture a dashboard site where all the pages are under the /admin/* directory:

Instead of repeating the same code in each route, use layouts to automatically reuse common parts. Layouts also support adding middleware to the route.

Take this src/routes directory as an example:

```
src/
└── routes/
    ├── admin/
    │   ├── layout.tsx  <-- This layout is used for all pages under /admin/*
    │   └── index.tsx
    ├── layout.tsx      <-- This layout is used for all pages
    └── index.tsx
```

### Middleware Layouts

Layouts can implement request handling using any of the following methods: onRequest, onGet, onPost, onPut or onDelete. This means they can be used to implement middleware.  For example, they can be used to validate the request cookies before rendering the page.

For the route https://example.com/admin, the onRequest methods will be executed in the following order:

An onRequest handler in src/routes/index.tsx doesn't get executed.

### Full Execution order

```
1 --> [entry.express.ts or entry.preview.ts]
2 --> [[email protected]] #Alphabetical order
3 --> [server$]
4 --> [entry.ssr.ts]
5 --> [root.tsx]
6 --> [layout.tsx onRequest  ->  onGet/onHttpVerb]
7 --> [globalLoaders]
8 --> [routeLoaders]
9 --> [jsx/components on a route]
```

### Nested Layouts

Layouts also provide a way to add common UI to the rendered page. For example, if you want to add a common header to all of the routes, add a Header component to the root layout.

For the given example, the Qwik components will be rendered in the following order:

```
<RootLayout>
  <AdminLayout>
    <AdminPage />
  </AdminLayout>
</RootLayout>
```

## SPA Navigation

With Qwik, the distinction between MPA and SPA disappears; every app can be both at the same time.
The choice is no longer an architectural design determined at the beginning of the project,
instead, this decision can be made for every link.

Qwik provides a <Link> component and useNavigate() hook.
These can be used to initiate an SPA refresh or navigation between pages.

The Link component is the recommended way to navigate as it uses the HTML <a> tag,
which is the most accessible way to move between pages.
However, if you need to navigate programmatically, you can use the useNavigate() hook.

```
import { component$ } from '@builder.io/qwik';
import { Link, useNavigate } from '@builder.io/qwik-city';
 
export default component$(() => {
  const nav = useNavigate();
  return (
    <div>
      <Link href="/about">About (preferred)</Link>
      <button onClick$={() => nav('/about')}>About</button>
    </div>
  );
});
```

The Link component uses the useNavigate() hook internally.

### Preventing navigation

We have an experimental API to prevent navigation while your app's state is unsaved. See the usePreventNavigate documentation for more information.

### <Link reload>

The Link component with the reload prop can be used together to refresh the current page.
You can also call the nav() function from the useNavigate() hook, without arguments.

```
import { component$ } from '@builder.io/qwik';
import { Link, routeLoader$, useNavigate } from '@builder.io/qwik-city';
 
export const useServerTime = routeLoader$(() => {
  // This will re-execute in the server when the page refreshes.
  return Date.now();
});
 
export default component$(() => {
  const nav = useNavigate();
  const serverTime = useServerTime();
 
  return (
    <div>
      <Link reload>Refresh (better accessibility)</Link>
      <button onClick$={() => nav()}>Refresh</button>
      <p>Server time: {serverTime.value}</p>
    </div>
  );
});
```

When the page refreshes, all the matching routeLoader$ and server handlers (onRequest) will re-execute in the server and the UI will re-render accordingly.

While refreshing the page, the isNavigating boolean from useLocation() will be true until the page is fully rendered.

### <Link prefetch>

By default, a Link component will start prefetching the next page as soon as the user hovers over the corresponding link in the UI. So if the application is done prefetching when the user clicks on the link, the next page will appear instantly. Although Qwik applications already excel at lazy loading javascript, this behavior can come in handy for content-heavy pages or SSR pages that need to wait for database or API calls.

If this is not your desired behavior, you can set the prefetch prop to false.

```
<Link prefetch={false} href="/about">About</Link>
```

### Scroll Restoration

Qwik provides best-in-class scroll restoration for SPA's that closely mimics the native browser experience.
Your users should receive the exact same experience they've come to expect natively from an MPA,
except with all the added benefits of an SPA.

After you use one of the above methods to navigate, the user is automatically upgraded to an SPA.
This means that the current page, and the page they came from, now have an SPA context associated with them.

If a user then clicks a regular <a> tag, they will perform a regular navigation. This new page will have no SPA context,
and is effectively downgraded back to an MPA. You can swap between these as necessary,
and the user's experience will seamlessly switch between MPA and SPA as if it were all the same.

When a user re-visits the SPA-enabled history entries, such as with a refresh, back/forward button, browser session restarts, etc.,
Qwik will automatically restore their scroll position and bootstrap itself back into the SPA context as needed.

The script required to provide this robust experience never loads, nor is it ever even sent to the user's browser,
unless the history entry has had an SPA context. Pure MPA pages never load this script. This is the magic of Qwik.

Scroll restoration in Qwik always occurs synchronously with render. When combined with Qwik's resumable and
first-class SSR/MPA nature, the user should never experience scroll flashing.

Qwik's scroll restoration is entirely history based. This is different from many other frameworks
which rely on things like sessionStorage.

Qwik's ability to remember and restore scroll positions is extremely robust
and will survive everything from browser session restarts to users clearing their browser data,
which is not the case for many other frameworks.

Notes on using pushState() and replaceState() during SPA:

On a page with an SPA context, Qwik will patch the pushState() and replaceState() functions on the global history.
This is to ensure that any custom states you add as a developer, also receive the SPA context.

While these are patched, states you push or replace should always be an actual Object type.
This is because Qwik needs to be able to automatically append the SPA context to the state as a property.

If you provide a value that is not an object, Qwik will create a new object for state and add your provided
value to a new key: { _data: <your_value> }

Qwik will also warn you in the browser's console in dev mode when this occurs.

## Request Event

Each request handler, such as onRequest, onGet, onPost, etc., are passed in a RequestEvent object as the first argument to the handler. The RequestEvent object contains utility functions and properties to get and set values to the server's request and response. This object contains the following properties:

## Rewrite Routes

You can rewrite your pathnames in order to reuse one single page component with its own middlewares and layouts for multiple pages.
This could be useful for SEO purposes or to translate your pages in different languages.

Translate localized urls with prefix:

For localization purposes you may want to translate your routes from /products to /it/prodotti
or to /fr/produits and /products/product-name to /it/prodotti/nome-prodotto or /fr/produits/nom-du-produit
without having multiple routes files for each locale but reusing the same page component, layouts, middlewares and so on.

The parameters name will not be changed so if the route file is /products/[slug]/index.tsx and the url is /products/product-name,
/it/prodotti/nome-prodotto or /fr/produits/nom-du-produit you will receive the same path parameter slug with
the values product-name, nome-prodotto or nom-du-produit.

Rewrite urls without prefix:

It's rare but you may want to have aliases for the same path.
For example you may want both /docs and /documents to be rendered from the same page component or
you may want to translate /products to /prodotti without adding the /it prefix.

In each folder within the routes directory where there are instances of the paths keys in the pathname, the route node will be duplicated, and all occurrences of paths keys will be replaced with their corresponding paths values.
All path parameters will preserve the same name. If there is a prefix it will be added at the beginning of the rewritten pathname.

You can set the rewrite rules as follows in your vite.config.ts:

```
import { defineConfig } from 'vite';
import { qwikCity } from '@builder.io/qwik-city/vite';
 
export default defineConfig(async () => {
  return {
    plugins: [
      qwikCity({
        rewriteRoutes: [
            {
              paths: {
                  'docs': 'documentation'
              },
            },
            {
              prefix: 'it',
              paths: {
                'docs': 'documentazione',
                'getting-started': 'per-iniziare',
                'products': 'prodotti',
              },
            },
          ],
      }),
    ],
  };
});
```

## Advanced routing

Qwik City also supports:

## Typesafe Routing

These are discussed later.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
