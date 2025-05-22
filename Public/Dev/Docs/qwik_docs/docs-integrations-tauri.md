# https://qwik.dev/docs/integrations/tauri/

[Original link](https://qwik.dev/docs/integrations/tauri/)

# Tauri

Tauri is a framework to build desktop applications with any frontend framework and a Rust core.

Learn more on the Tauri website.

## Adapter

Make sure you use the Static Adapter.

Then you can build your app with

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

## Add Tauri

To install Tauri:

```
pnpm install @tauri-apps/cli
```

```
npm install @tauri-apps/cli
```

```
yarn add @tauri-apps/cli
```

```
bun install @tauri-apps/cli
```

In your package.json, add this script:

```
"scripts": {
  "tauri": "tauri"
}
```

Then, to scaffold a minimal Rust project that is pre-configured to use Tauri, open a terminal and run the following command:

```
pnpm run tauri init
```

```
npm run tauri init
```

```
yarn run tauri init
```

```
bun run tauri init
```

This command will walk you through a quick setup:

That's it! Finally you can run this command to start developing your app:

```
pnpm run tauri dev
```

```
npm run tauri dev
```

```
yarn run tauri dev
```

```
bun run tauri dev
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
