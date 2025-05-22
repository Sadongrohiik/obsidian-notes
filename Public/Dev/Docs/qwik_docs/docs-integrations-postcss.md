# https://qwik.dev/docs/integrations/postcss/

[Original link](https://qwik.dev/docs/integrations/postcss/)

# PostCSS

PostCSS allows developers to write modern CSS while still maintaining backwards compatibility and improving performance. It parses CSS code and passes it through a series of plugins that can modify, optimize, and extend the CSS before outputting the final result.

## Usage

You can add PostCSS to your project by using the following Qwik starter script:

```
pnpm run qwik add postcss
```

```
npm run qwik add postcss
```

```
yarn run qwik add postcss
```

```
bun run qwik add postcss
```

This will create a new postcss.config.js file at the root of the project with following dependencies and configuration.

```
module.exports = {
  plugins: {
    autoprefixer: {},
    "postcss-preset-env": {
      stage: 3,
      features: {
        "nesting-rules": true,
      },
    },
  },
}
```

If you wish to add a new plugin like CssNano run the following command and update the postcss.config.js.

```
pnpm install cssnano
```

```
npm install cssnano
```

```
yarn add cssnano
```

```
bun install cssnano
```

```
module.exports = {
  plugins: {
    /* previous plugin configuration */
    "cssnano": {
      preset: "default"
    }
  },
}
```

For further documentation, checkout PostCSS Docs

### Contributors

Thanks to all the contributors who have helped make this documentation better!
