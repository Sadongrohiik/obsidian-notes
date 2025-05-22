# https://qwik.dev/docs/integrations/astro/

[Original link](https://qwik.dev/docs/integrations/astro/)

# Astro

Astro is a flexible meta-framework that accommodates a wide range of tools and integrations, enabling you to leverage numerous ecosystems.

It also allows you to write components using your favorite UI framework (or no framework at all) and renders your pages to static HTML at build time, or dynamically on the server using Server-Side Rendering (SSR).

This results in a fast, SEO-friendly output that can be deployed to any static hosting environment or server.

For more details on the integration and to view the source code, check out the QwikDev Astro Integration on GitHub.

## Astro instead of Qwik City

When integrating Astro with Qwik, it's important to note that Qwik City APIs are not compatible with Astro.

Astro is a meta-framework that provides its own set of APIs and features for handling these concerns.
These include but are not limited to:

When using Qwik with Astro, use Astro's APIs instead of Qwik City's. This ensures your Qwik components work correctly in Astro. See the Astro documentation for more details.

## @qwikdev/astro 💜

This integration leverages the power of JavaScript Streaming inside of Astro, using Qwik components.

## Installation

### The @qwikdev/astro CLI 🦾

To start a new Qwik Astro project, you can run the following command:

```
pnpm create @qwikdev/astro
```

```
npm create @qwikdev/astro
```

```
yarn create @qwikdev/astro
```

```
bun create @qwikdev/astro
```

For more advanced CLI configuration options, see the @qwikdev/astro CLI documentation.

### Existing projects

Astro comes with a command-line tool for incorporating built-in integrations: astro add. This command will:

To install @qwikdev/astro, run the following from your project directory and follow the prompts:

```
pnpm dlx astro add @qwikdev/astro
```

```
npx astro add @qwikdev/astro
```

```
yarn dlx astro add @qwikdev/astro
```

```
bunx astro add @qwikdev/astro
```

### Setting up the TypeScript Config

When using Astro's integration CLI or manually adding the integration, Qwik needs the following in tsconfig.json for typescript to recognize Qwik's JSX types.

```
"compilerOptions": {
  "jsx": "react-jsx",
  "jsxImportSource": "@builder.io/qwik"
}
```

If you face any issues, please post them on Github and attempt the manual installation below.

### Manual Installation

First, install the @qwikdev/astro integration like so:

```
pnpm install @qwikdev/astro
```

```
npm install @qwikdev/astro
```

```
yarn add @qwikdev/astro
```

```
bun install @qwikdev/astro
```

Typically, package managers install peer dependencies. However, if you get a Cannot find package '@builder.io/qwik' warning when starting Astro, install Qwik.

```
pnpm install @builder.io/qwik
```

```
npm install @builder.io/qwik
```

```
yarn add @builder.io/qwik
```

```
bun install @builder.io/qwik
```

Now, add the integration to your astro.config.* file using the integrations property:

```
// astro.config.mjs
  import { defineConfig } from 'astro/config';
+ import qwikdev from '@qwikdev/astro';
 
  export default defineConfig({
    // ...
    integrations: [qwikdev()],
    //             ^^^^^
  });
```

### Learn More

For more documentation on using Qwik and Astro, the integration README is a great place to start.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
