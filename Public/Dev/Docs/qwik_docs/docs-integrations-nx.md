# https://qwik.dev/docs/integrations/nx/

[Original link](https://qwik.dev/docs/integrations/nx/)

# Nx and enterprise scale monorepos

Nx is a robust and extensible development platform designed to simplify the management
of large-scale monorepos containing multiple applications and libraries by offering powerful tools for code generation,
build orchestration, dependency management, and code sharing.

Qwik integrates with nx beautifully by using the qwik-nx plugin.

## Main features

## Usage

You can generate a new workspace by running:

```
pnpm dlx create-nx-workspace@latest org-workspace --preset=qwik-nx
```

```
npx create-nx-workspace@latest org-workspace --preset=qwik-nx
```

```
yarn dlx create-nx-workspace@latest org-workspace --preset=qwik-nx
```

```
bunx create-nx-workspace@latest org-workspace --preset=qwik-nx
```

Or add a new Qwik application to an existing workspace by running:

```
pnpm install qwik-nx
```

```
npm install qwik-nx
```

```
yarn add qwik-nx
```

```
bun install qwik-nx
```

and then

```
nx generate qwik-nx:app
```

For further reference, please check the qwik-nx documentation.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
