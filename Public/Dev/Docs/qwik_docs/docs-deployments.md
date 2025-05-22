# https://qwik.dev/docs/deployments/

[Original link](https://qwik.dev/docs/deployments/)

# Deployments

When it's time to deploy your application, Qwik comes with ready-to-use integration that make this so easy!

```
pnpm run qwik add
```

```
npm run qwik add
```

```
yarn run qwik add
```

```
bun run qwik add
```

## Adapters and Middleware

Qwik City middleware is a glue code that connects server rendering framework (such as Cloudflare, Netlify, Vercel, Express etc.) with the Qwik City meta-framework.

## Production build

When a new integration is added to the project, a build.server script is added to the package.json file. This script is used to build the project for production.

The only thing you need to do is to run the following command:

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

Under the hood, the build script will execute, build.server and build.client scripts.

## Advanced

The requestHandler() utility is what each of the above middleware bundles uses in order to translate their request/response to a standard format for Qwik City to use. This function can be used to provide middleware for specific server frameworks.

If there's middleware missing and you'd like it added, take a look at how the requestHandler() utility is used to handle requests for each of the middleware source-code above. Better yet, we'd love to have your middleware contributions! PR's are welcome!

## Add A New Deployment

Thanks for your interest in adding a deployment integration to Qwik! We're more than happy to help you get started. Before we get too far, if there's already a deployment for what you're looking for, we'd love to have you contribute to it. If the deployment is not already available, let's add it!

To start it's probably best to copy an existing adapters and middleware and modify it to fit your needs. A deployment is made up of a few different parts:

### Add An Adapter

An adapter is the term used to summarize the Vite config that needed for the special build configuration. Each server, whether it's a cloud-service or a custom server, has its own unique build configuration for a specific output the server uses. For example, Cloudflare, Netlify and Node.js Server each have their own build configurations.

The adapter is really a Vite config, that's extending the base config. The base config is the same for all adapters, and the adapter config is the unique part for each server.

### Add Middleware

Middleware is the glue code that connects the server rendering framework (such as Cloudflare, Netlify, Vercel, Express etc.) with the Qwik City meta-framework. Each middleware is responsible for handling the request and response from the server and translating it to a standard format for Qwik City to use.

Luckily Qwik City uses the standardized Request and Response interfaces, so the middleware is usually pretty minimal.

For middleware, you'll notice that each one calls the common @builder.io/qwik-city/middleware/request-handler package. The job of each middleware is to translate the request and response to the standardized format that Qwik City request handler package uses.

### Add To The Starter CLI

The next step is to add the new adapter to the Starter CLI. For this step it's probably best to ping the core team on Discord to help you get started. The CLI is a great place to add the new adapter, because it's a great way to test the new adapter and make sure it's working as expected.

## Cache Headers

To assure proper caching of your built files, you need to serve them with the correct cache headers.

By default, files are generated under dist/build and dist/assets, and they get a content hash in the filename. This means that the name is unique for the contents of those files, and they can be cached indefinitely.

Therefore, we recommend that you serve these files with the following header:

```
Cache-Control: public, max-age=31536000, immutable
```

The various deployment platforms have different ways of configuring this, and the starters should have the correct configuration already set (you can npx qwik add again to update the configuration). However, there is no one-size-fits-all solution, so verify that caching is working as expected.

To verify proper caching, you can visit your site and open the developer tools to inspect the network requests. When you reload the page, you should see that all requests for assets are coming from the browser cache and are not contacting the server. Even a 304 Not Modified response is not good enough, because it means that the browser is still unsure that the content is cached.

⚠️ Note: If your app uses compiled-i18n or qwik-speak, then translated bundles (build/[locale]/*.js) can retain identical filenames between builds even when translations change. Consider how long you want to cache these files for so users get the latest translations.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
