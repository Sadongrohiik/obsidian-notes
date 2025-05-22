# https://qwik.dev/docs/deployments/deno/

[Original link](https://qwik.dev/docs/deployments/deno/)

# Deno Middleware

Qwik City Deno middleware allows you to hook up Qwik City to a Deno server which uses the standard Request/Response that's well supported by Deno. Some Deno server implementations include:

## Installation

To integrate the deno adapter, use the add command:

```
pnpm run qwik add deno
```

```
npm run qwik add deno
```

```
yarn run qwik add deno
```

```
bun run qwik add deno
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

## Serve

To start the Deno server after a build:

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

Since you are choosing Deno, here you are in your own, after running the build command:

By default, SSG mode is activated. If you want to change this behavior, you can edit the vite.config.ts file inside the adapters/deno folder. In this file you can configure the behavior of the SSG or remove the SSG part to switch to a complete SSR.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
