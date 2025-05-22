# https://qwik.dev/docs/labs/typed-routes/

[Original link](https://qwik.dev/docs/labs/typed-routes/)

# 🧪 Typed Routes

Stage: prototyping

Provides type safe way of building URLs within the application.

## Installation

```
pnpm install github:QwikDev/qwik-labs-build#main
```

```
npm install github:QwikDev/qwik-labs-build#main
```

```
yarn add github:QwikDev/qwik-labs-build#main
```

```
bun install github:QwikDev/qwik-labs-build#main
```

```
// ...
import { qwikTypes } from '@builder.io/qwik-labs/vite';
 
export default defineConfig(() => {
  return {
    plugins: [
     // ...
     qwikTypes() // <== Add `qwikTypes()` to the list of plugins
    ],
    // ...
  };
});
```

```
import { AppLink } from '~/routes.config';
 
export default component$(() => {
  // ...
  return (
    // ...
    <AppLink route="/your/[appParam]/link/" param:appParam={"some-value"}>
      Link text
    </AppLink>
  );
});
```

# Declarative Routing

This is a package originally created by Jack Herrington aka "The Blue Collar Coder" for type safe routing inside NextJS applications and has been adapted for use inside QwikCity

## Installation

```
pnpm dlx declarative-routing init
```

```
npx declarative-routing init
```

```
yarn dlx declarative-routing init
```

```
bunx declarative-routing init
```

## Setup

The initialization process will create some important files for you.

### .src/declarativeRoutes

### Each of your route directories

## Usage

### Declare Route Details

```
import { z } from "zod";
 
export const Route = {
  name: "PokemonDetail",
  params: z.object({
    pokemonId: z.coerce.number(),
  }),
};
```

### Inside Component

There are a few different ways you can use Declarative Routes inside your component.

```
import { PokemonDetail } from "~/declarativeRoutes";
 
export default component$(() => {
  // ...
  return (
    // ...
    <PokemonDetail.Link pokemonId={1}>Bulbasaur</PokemonDetail.Link>
  );
});
```

```
import { Link } from "@builder.io/qwik-city";
import { PokemonDetail } from "~/declarativeRoutes";
 
export default component$(() => {
  // ...
  return (
    // ...
    <Link href={PokemonDetail({ pokemonId: 1 })}>Bulbasaur</Link>
  );
});
```

```
import { PokemonDetail } from "~/declarativeRoutes";
 
export default component$(() => {
  // ...
  return (
    // ...
    <PokemonDetail.ParamsLink params={{ pokemonId: 1 }}>Bulbasaur</PokemonDetail.ParamsLink>
  );
});
```

```
import { PokemonDetail } from "~/declarativeRoutes";
 
export default component$(() => {
  // Typescript will know the correct params and their types
  const { pokemonId } = useParams(PokemonDetail);
  // ...
  return (
    // ...
  );
});
```

## Add or Change Routes

If you add a new route, or move an existing route, simply run

```
pnpm dlx declarative-routing build
```

```
npx declarative-routing build
```

```
yarn dlx declarative-routing build
```

```
bunx declarative-routing build
```

and this will rerun the process and update any changes needed

## Links

### Contributors

Thanks to all the contributors who have helped make this documentation better!
