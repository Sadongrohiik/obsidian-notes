# https://qwik.dev/docs/advanced/routing/

[Original link](https://qwik.dev/docs/advanced/routing/)

# Advanced Routing

## 404 Page Handling

It's possible for any user to visit a URL that doesn't exist on your site. For example, if a user visits https://example.com/does-not-exist, then the server should respond with a 404 HTTP status code, and the page should have at least some sort of explanation, rather than just a blank page.

For any given route, Qwik City can choose how to best handle the 404 response for the user, whether it's with the default 404 page, a custom 404 page, or a dynamically generated 404 page.

### Default 404 Page

Rather than showing a blank page, by default Qwik City provides a generic 404 page for any route that isn't handled. The default 404 page is rendered as a fallback when a custom 404 page was not found. We recommend providing a custom 404 page for a better user experience. Including the common header and navigation in a custom 404 page would help the user find the page they're looking for.

### Custom 404 Page

Instead of showing the generic (boring) 404 response, it's possible to provide a custom 404 page using the same familiar layouts as the rest of your site.

To create a custom 404 page, add a 404.tsx file to the root src/routes directory.

```
src/
└── routes/
    ├── 404.tsx            # Custom 404
    ├── layout.tsx         # Default layout
    └── index.tsx          # https://example.com/
```

In the example above, the 404.tsx page will also use the layout.tsx layout, since it is a sibling of the layout in the same directory.

Additionally, using Qwik City's directory-based routing allows for custom 404 pages to be created at different paths. For example, if src/routes/account/404.tsx was also added to the structure, then the custom account 404 page would only be applied to the /account/* routes, while all other 404s would use the root 404.tsx page.

Note: During development and in preview mode, the custom 404 pages will not be rendered, but instead the default Qwik City 404 page will show. However, when building the app for production, the custom 404 page will be statically generated as a static 404.html file.

```
src/
└── routes/
    ├── account/
    │   └── 404.tsx        # Custom Account 404
    │   └── index.tsx      # https://example.com/account/
    ├── 404.tsx            # Custom 404
    ├── layout.tsx         # Default layout
    └── index.tsx          # https://example.com/
```

It's worth noting that custom 404 pages are statically generated at build time, resulting in a static 404.html file, rather than individually server-side rendered pages. This strategy reduces the load on your HTTP server, avoiding server-side rendering of 404 pages, and thus preserving resources.

### Dynamic 404 Page

When rendering a page, the default is to always respond with a 200 HTTP status code, which tells the browser all is good and the route exists. However, it's also possible to handle rendering the page, but manually setting the response status code to something other than 200, such as 404.

For example, let's say we have a product page with a URL such as https://example.com/product/abc. The product page would be handled using src/routes/product/[id]/index.tsx directory-based route, and [id] is a dynamic param in the URL.

In this example, id is used as a key to load the product data from the database. When the product data is found, great, we'll correctly render data. However, if the product data is not found in the database, we can still handle rendering the page, but instead respond with a 404 HTTP status code.

```
import { component$ } from '@builder.io/qwik';
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useProductLoader = routeLoader$(async ({ params, status }) => {
  // Example database call using the id param
  // The database could return null if the product is not found
  const data = await productDatabase.get(params.id);
 
  if (!data) {
    // Product data was not found
    // Set the status code to 404
    status(404);
  }
 
  // return the data (which may be null)
  return data;
});
 
export default component$(() => {
  // get the product data from the loader
  const product = useProductLoader();
 
  if (!product.value) {
    // no product data found
    // so render our own custom product 404
    return <p>Sorry, looks like we don't have this product.</p>;
  }
 
  // product data was found, so let's render it
  return (
    <div>
      <h1>{product.value.name}</h1>
      <p>{product.value.price}</p>
      <p>{product.value.description}</p>
    </div>
  );
});
```

## Grouped Layouts

Common purpose routes are often placed into directories so they can share layouts, and so related source files are logically grouped next to each other. However, it may be desirable that the directory, which was used to group similar files and share layouts, is excluded from the public-facing URL. This is where "grouped" layouts come in (also referred to as a "pathless" layout route).

By surrounding any directory name with parentheses, such as (name), then the directory name itself will not be included in the URL pathname.

For example, let's say an app placed all account routes together in a directory.  /account/ could be dropped from the URL for cleaner, shorter URLs. In the example below, notice that the paths are within the src/routes/(account)/ directory, but the URL paths exclude (account)/.

```
src/
└── routes/
    └── (account)/             # Notice the parentheses
        ├── layout.tsx         # Shared account layout
        └── profile/
            └── index.tsx      # https://example.com/profile
        └── settings/
            └── index.tsx      # https://example.com/settings
```

## Named Layout

At times related routes need to have drastically different layouts from their siblings. It is possible to define multiple layouts for different sibling routes by using a single default layout and any number of named layouts. The child route can then request a specific named-layout.

Qwik City defines the convention that layouts are within src/routes and the filename starts with layout. That's why the default layout is named layout.tsx. A named layout also starts with layout followed by a dash - and a unique name, such as layout-narrow.tsx.

To reference a named layout, the route's index.tsx file must be suffixed with @<name>. For example, [email protected] would use the layout-narrow.tsx layout.

```
src/
└── routes/
    ├── contact/
    │   └── [email protected]      # https://example.com/contact (Layout: layout-narrow.tsx)
    ├── layout.tsx                # Default layout
    ├── layout-narrow.tsx         # Named layout
    └── index.tsx                 # https://example.com/ (Layout: layout.tsx)
```

```
┌──────────────────────────────────────────────────┐
│       src/routes/layout.tsx                      │
│  ┌────────────────────────────────────────────┐  │
│  │    src/routes/index.tsx                    │  │
│  │                                            │  │
│  └────────────────────────────────────────────┘  │
│                                                  │
└──────────────────────────────────────────────────┘
```

```
┌──────────────────────────────────────────────────┐
│       src/routes/layout-narrow.tsx               │
│  ┌────────────────────────────────────────────┐  │
│  │    src/routes/contact/[email protected]     │  │
│  │                                            │  │
│  └────────────────────────────────────────────┘  │
│                                                  │
└──────────────────────────────────────────────────┘
```

## Nested Layout

Most times it is desirable to nest layouts within each other. A page's content can be nested in numerous wrapping layouts, which is determined by the directory structure.

```
src/
└── routes/
    ├── layout.tsx           # Parent layout
    └── about/
        ├── layout.tsx       # Child layout
        └── index.tsx        # https://example.com/about
```

In the above example, there are two layouts that apply themselves around the /about page component.

In this case, the layouts will be nested within each other on the page.

```
┌────────────────────────────────────────────────┐
│       src/routes/layout.tsx                    │
│  ┌──────────────────────────────────────────┐  │
│  │    src/routes/about/layout.tsx           │  │
│  │  ┌────────────────────────────────────┐  │  │
│  │  │ src/routes/about/index.tsx         │  │  │
│  │  │                                    │  │  │
│  │  └────────────────────────────────────┘  │  │
│  │                                          │  │
│  └──────────────────────────────────────────┘  │
│                                                │
└────────────────────────────────────────────────┘
```

```
import { component$, Slot } from '@builder.io/qwik';
 
export default component$(() => {
  return (
    <main>
      <Slot /> {/* <== Child layout/route inserted here */}
    </main>
  );
});
```

```
import { component$, Slot } from '@builder.io/qwik';
 
export default component$(() => {
  return (
    <section>
      <Slot /> {/* <== Child layout/route inserted here */}
    </section>
  );
});
```

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  return <h1>About</h1>;
});
```

The above example would render the html:

```
<main>
  <section>
    <h1>About</h1>
  </section>
</main>
```

## Plugin with plugin@<name>.ts

plugin.ts and plugin@<name>.ts files can be created in the root of the src/routes directory to handle any incoming request before even the root layout executes.

You can have multiple plugin.ts files, each with a different name. For example, [email protected] and [email protected]. The @<name> is optional and it's only used for developers to help identify the plugin.

Requests handlers like onRequest, onGet, onPost, etc. are called before server$ functions are executed.

### The order of execution of plugin.ts files

If plugin.ts file exists and if it has exported request handlers, then they are executed first.

Then exported request handlers from plugin@<name>.ts files are executed in alphabetical order of the file names. For example, onGet from [email protected] is executed before onGet from [email protected] because auth is alphabetically before security.

Finally, if a server$ function exists, it's executed last.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
