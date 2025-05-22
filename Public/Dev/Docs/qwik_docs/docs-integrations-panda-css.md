# https://qwik.dev/docs/integrations/panda-css/

[Original link](https://qwik.dev/docs/integrations/panda-css/)

# Panda CSS

Panda is a styling engine that generates styling primitives to author atomic CSS and recipes in a type-safe and readable manner.
Panda CSS Website

## Usage

You can add Panda easily by using the following Qwik starter script:

```
pnpm run qwik add pandacss
```

```
npm run qwik add pandacss
```

```
yarn run qwik add pandacss
```

```
bun run qwik add pandacss
```

The previous command updates your app with the necessary dependencies.

It also adds new files to your project folder:

and modifies your src/global.css to include

```
# global.css file
 
@layer reset, base, tokens, recipes, utilities;
 
...stuff...
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
