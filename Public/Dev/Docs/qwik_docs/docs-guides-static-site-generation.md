# https://qwik.dev/docs/guides/static-site-generation/

[Original link](https://qwik.dev/docs/guides/static-site-generation/)

# Static Site Generation (SSG) Overview

Static Site Generation, or commonly referred to as "SSG", is the process of pre-rendering site webpages into static HTML files. The benefit is that when a visitor requests the webpage, the response is a pre-generated HTML file (a static file), and doesn't require the webpage's HTML to "rebuild" on the visitor's browser, or dynamically created by your server (more on this later).

Additionally, due to Qwik's underlying architecture, page performance also benefits by not requiring a Javascript "hydration" step, which can significantly lower performance and slow down user interactivity. By pre-rendering static index.html files with SSG, and combined with Qwik's resumability, static site generation offers many performance benefits over legacy solutions.

## SSG vs. Server-Side Rendered (SSR)

Qwik City is capable of taking a Qwik application, no matter if it's a "webapp" or "website", and generate static HTML. Once it's generated as HTML, Qwik is fundamentally able to skip rebuilding the app by using resumability, since the app was already generated as HTML. Both Static Site Generation (SSG) and Server-Side Rendering (SSR) use the same process to generate the HTML. The main difference between the SSG and SSR however, is "when" the HTML is generated.

In a traditional setup, SSG pre-renders each webpage at build-time, while SSR render's each webpage on-demand for each HTTP request. SSG only needs to generate the HTML one time per build, which is great for webpages where multiple visitors should see the same content. In contrast, SSR is great when the webpage may be different for each visitor, and would need to render custom HTML for each individual HTTP request.

For example, SSG is ideal for a blog or docs site, where all the content should be the same for multiple visitors. While SSR may work fine for a blog, it may be an unnecessary strain for your HTTP servers to render the blog content for every visitor, even though they'd all end up seeing the same HTML.

However, an account dashboard would commonly have different content for each signed-in user. In this setup, each user should get their own rendered HTML with their account information, rather than everyone seeing the exact same content. This is where SSR would be preferred.

Ideally, the more you can do with static site generation the better, since that'll have less costs to your servers and faster response times.

With Qwik City however, the decision to use SSG or SSR, does not have to be one or the other decision. Instead, your own implementation can choose to have some route paths use SSG, while some other pages use SSR. It's entirely up to you and your requirements.

## Static Site Generation Config

Static site generation is created from the built in adapter, to create an adapter run:

```
pnpm run qwik add static
```

```
npm run qwik add static
```

```
yarn run qwik add static
```

```
bun run qwik add static
```

Select Adapter: Static site (.html files). Done!

### Changes

Running the above command will make the following changes to your project:

Your build files will be generated into the dist folder.

You can build your static site using:

```
pnpm run build.server
```

```
npm run build.server
```

```
yarn run build.server
```

```
bun run build.server
```

### SSG Config

The adapters/static/vite.config.ts file also includes the SSG config, which would be custom for each implementation.

#### origin

The URL origin, which is a combination of the scheme (protocol) and hostname (domain). For example, https://qwik.dev has the protocol https:// and domain qwik.dev. However, the origin does not include a pathname.

The origin is used to provide a full URL during Static Site Generation (SSG), and to simulate a complete URL rather than just the pathname. For example, in order to render a correct canonical tag URL or URLs within the sitemap.xml, the origin must be provided too.

If the site also starts with a pathname other than /, please use the base option in the Vite config options (the basePathname option in the Qwik City config options is deprecated).

#### outDir

The outDir is a file system output directory where the static files should be written. In the example above, it's using Node's fileURLToPath to create an absolute file system path to write the static HTML files to.

### Javascript Runtimes

For a Javascript project, it's quite common for the build's runtime to be built on top of Node.js. However, the core of Qwik City static site generation isn't tied to using only Node.js, which is why the qwikCityGenerate() function is imported from @builder.io/qwik-city/static/node. By scoping the generate function to a specific runtime, such as Node.js, this gives Qwik City the flexibility to also generate SSG from other runtimes in the future, such as Deno or Bun.

## Dynamic SSG Routes

So far, we've only discussed how to generate static HTML files for a single route path. However, in most cases, you'll want to generate HTML files for multiple route paths that has dynamic params. For example, a product site may have a route path for each product, such as /product/:id. In this case, you'll want to generate HTML files for each product page, which would require generating HTML files for each product ID.

```
import { component$ } from '@builder.io/qwik';
import { useLocation, type StaticGenerateHandler } from '@builder.io/qwik-city';
import { loadProductIds } from './load-product-ids';
 
export default component$(() => {
  const { params } = useLocation();
 
  return <p>Example: {params.id}</p>;
});
 
export const onStaticGenerate: StaticGenerateHandler = async ({ env }) => {
  // example of loading params for this use case
  // every implementation will be different
  const ids = await loadProductIds({
    apiKey: env.get('API_KEY'),
  });
 
  return {
    params: ids.map((id) => {
      return { id };
    }),
  };
};
```

In the above example, the onStaticGenerate() function is loading the product IDs from a loadProductIds() function by requesting an API behind an API key retrieved from an environment variable.
This function would be custom for each implementation, but the general idea is that you'll need to load the data for each product ID, and then generate HTML files for each product ID.

The onStaticGenerate function should be exported from the top-level of the module, and should return an object with a params property. The params property should be an array of objects, where each object is a set of params for the route path. For example, if the route path is /product/:id, then the params array should be an array of objects with an id property.

The directory structure for this example would be:

```
src/
└── routes/
    └── product/
        └── [id]/
            └── index.tsx
```

Notice that the index.tsx file is inside a directory named [id]. This is a special directory name that tells Qwik City to generate HTML files for each id param. The index.tsx file is the default file that Qwik City will use when generating HTML files for a route path.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
