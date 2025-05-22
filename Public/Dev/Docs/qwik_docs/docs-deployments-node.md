# https://qwik.dev/docs/deployments/node/

[Original link](https://qwik.dev/docs/deployments/node/)

# Node Middleware

Qwik City Node middleware allows you to connect Qwik City to a Node.js server which uses the common middleware functionality. Some Node servers include:

## Installation

To integrate the node adapter, use the add command:

```
pnpm run qwik add express
```

```
npm run qwik add express
```

```
yarn run qwik add express
```

```
bun run qwik add express
```

```
pnpm run qwik add fastify
```

```
npm run qwik add fastify
```

```
yarn run qwik add fastify
```

```
bun run qwik add fastify
```

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

## Dev serve

To deploy the application for development:

```
pnpm run serve
```

```
npm run serve
```

```
yarn run serve
```

```
bun run serve
```

## Production deploy

Since you are choosing Node, here you are in your own, after running the build command:

In order to deploy the server, you need to run the server/entry.[server].js file in the server of your choice, where [server] can be express or fastify.

It's very important to correctly configure the ORIGIN env variable, which is used to check against CSRF attacks. The origin must match the origin of the client application.

For example, if you plan to deploy your application to https://example.com/app, then you need to set the ORIGIN environment variable to https://example.com.

```
ORIGIN=https://example.com node server/entry.express
```

You can check how to deploy with Docker here.

### CSRF Protection

By default, all Qwik City applications are protected against CSRF attacks for all POST, PATCH, DELETE form submits.

This protection is enabled by default and it's the reason why you need to set the ORIGIN environment variable when deploying your application for production.

If you want to disable CSRF protection, you can set checkOrigin: false in the createQwikCity() options in src/entry.preview.tsx or src/entry.[server].tsx:

```
// ...
const { router, notFound, staticFile } = createQwikCity({
  render,
  qwikCityPlan,
  manifest,
  checkOrigin: false,
});
// ...
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
