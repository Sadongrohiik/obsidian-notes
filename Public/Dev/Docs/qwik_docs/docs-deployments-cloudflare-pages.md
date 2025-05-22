# https://qwik.dev/docs/deployments/cloudflare-pages/

[Original link](https://qwik.dev/docs/deployments/cloudflare-pages/)

# Cloudflare Pages Adapter

Qwik City Cloudflare Pages adapter allows you to connect Qwik City to Cloudflare Pages.

## Installation

To integrate the cloudflare-pages adapter, use the add command:

```
pnpm run qwik add cloudflare-pages
```

```
npm run qwik add cloudflare-pages
```

```
yarn run qwik add cloudflare-pages
```

```
bun run qwik add cloudflare-pages
```

The adapter will add a new vite.config.ts within the adapters/ directory, and a new entry file will be created, such as:

```
└── adapters/
    └── cloudflare-pages/
        └── vite.config.ts
└── src/
    └── entry.cloudflare-pages.tsx
```

Additionally, within the package.json, the build.server and deploy scripts will be updated.

Take note of your nodejs version in your local environment by running the node -v command:

```
node -v
v20.11.1
```

When using

```
pnpm create qwik@latest
```

```
npm create qwik@latest
```

```
yarn create qwik
```

```
bun create qwik@latest
```

to setup your Qwik app it will likely use a different nodejs version than what Cloudflare Pages uses by default (v16.20.2).

## Production build

To build the application for production, use the build command, this command will automatically run build.server and build.client:

```
pnpm run build
```

```
npm run build
```

```
yarn run build
```

```
bun run build
```

Read the full guide here

## Deploy to Cloudflare Pages

After installing the integration the project is ready to be deployed to Cloudflare Pages.

If the nodejs version is different in your environment than Cloudflare Pages (v16.20.2) you'll need to add a NODE_VERSION environment variable and set the value to the version that you got from running the node -v command in your environment:

```
node -v
v20.11.1
```

To do this in Cloudflare go to **Workers & Pages > YOUR_PROJECT > Settings > Environment variables > Production (and Preview) > Add variables > Save **

Please refer to the Cloudflare Pages docs for more information on how to deploy your site.

Note that you will need a Cloudflare account in order to complete this step.

## Static Site Generation (SSG)

The Cloudflare Pages adapter also supports Static Site Generation (SSG) by using the ssg property.
This allows you to generate static HTML files for your application at build time, instead of rendering them at runtime.

```
export default extendConfig(baseConfig, () => {
  return {
    build: {
      ssr: true,
      rollupOptions: {
        input: ['src/entry.cloudflare-pages.tsx', '@qwik-city-plan'],
      }
    },
    plugins: [
      cloudflarePagesAdapter(
       // 👇 THIS IS WHAT YOU NEED TO ADD 👇
       {
         ssg: {
           include: ['/*'],
           exclude: ['/shop/*'],
           origin: 'https://example.com',
       },
      }),
    ],
  };
});
```

#### include

The include array is used to specify which paths should be statically generated. It accepts wildcard behavior.

#### exclude

The exclude array defines routes that should not be static generated and accepts wildcard behavior.
exclude always take priority over include.

#### origin

The URL origin, which is a combination of the scheme (protocol) and hostname (domain). For example, https://qwik.dev has the protocol https:// and domain qwik.dev. However, the origin does not include a pathname.

The origin is used to provide a full URL during Static Site Generation (SSG), and to simulate a complete URL rather than just the pathname.
For example, in order to render a correct canonical tag URL or URLs within the sitemap.xml, the origin must be provided too.

This is important because if you don't set it, cloudflare will use the specific deployment url instead.

## Advanced

### Cloudflare Pages Entry Middleware

When the cloudflare-pages adapter is added, a new entry file will be created at src/entry.cloudflare-pages.tsx. Below is an example of using the built-in middleware within the entry file.

```
import {
  createQwikCity,
  type PlatformCloudflarePages,
} from '@builder.io/qwik-city/middleware/cloudflare-pages';
import qwikCityPlan from '@qwik-city-plan';
import render from './entry.ssr';
 
const fetch = createQwikCity({ render, qwikCityPlan });
 
export { fetch };
```

The compiled middleware will be built in the server/ directory. Such directory also contains a _worker.js file which implements the application's request handling as per the Cloudflare Pages Advanced Mode.
The file simply re-exports the produced fetch handler as shown below.

```
import { fetch } from "../server/entry.cloudflare-pages";
export default { fetch };
```

### Cloudflare Pages Function Invocation Routes

Cloudflare Page's function-invocation-routes config can be used to include, or exclude, certain paths to be used by the worker functions. Having a _routes.json file gives developers more granular control over when your Function is invoked.

This is useful to determine if a page response should be Server-Side Rendered (SSR) or if the response should use a static-site generated (SSG) index.html file instead.

By default, the Cloudflare Pages adapter does not include a public/_routes.json config, but rather it is auto-generated from the build by the Cloudflare adapter. An example of an auto-generated dist/_routes.json would be:

```
{
  "include": ["/*"],
  "exclude": [
    "/_headers",
    "/_redirects",
    "/build/*",
    "/favicon.ico",
    "/manifest.json",
    "/service-worker.js",
    "/about"
  ],
  "version": 1
}
```

In the above example, it's saying all pages should be SSR'd. However, the root static files such as /favicon.ico and any static assets in /build/* should be excluded from the Functions, and instead treated as a static file.

In most cases the generated dist/_routes.json file is ideal. However, if you need more granular control over each path, you can instead provide your own public/_routes.json file. When the project provides its own public/_routes.json file, then the Cloudflare adapter will not auto-generate the routes config and instead use the committed one within the public directory.

### Context

You may access Cloudflare Page's environment variables in the endpoint method's platform param:

```
export const onRequest = async ({ platform }) => {
  const secret = platform.env['SUPER_SECRET_TOKEN'];
};
```

Additionally, you may import the RequestHandler and PlatformCloudflarePages types to have type completions in your editor.

```
import { type RequestHandler } from '@builder.io/qwik-city';
import { type PlatformCloudflarePages } from '@builder.io/qwik-city/middleware/cloudflare-pages';
 
export const onGet: RequestHandler<PlatformCloudflarePages> = ({ platform }) => {
  //...
};
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
