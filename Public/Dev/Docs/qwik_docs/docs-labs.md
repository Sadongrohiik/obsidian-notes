# https://qwik.dev/docs/labs/

[Original link](https://qwik.dev/docs/labs/)

# 🧪 Qwik Labs Overview

Qwik Labs is an incubator for ideas not yet ready for production. It's a place where we can publish our "work in progress" so the community can try it out and provide feedback, without any guarantees that the feature is stable or will make it into production.

Given that these are ideas in their initial stages, chances are they will significantly change over their lifetime, so they should not be relied upon in production.

USE AT YOUR OWN RISK.

DISCLAIMER: Qwik Labs is a place to experiment, as such:

Expect lots of breaking changes as the features are being developed!!!

## Stages

Each Qwik Labs feature can roughly be thought of as going through these stages:

## Installation

There are two ways experimental features are made available to the community:

As an experimental flag.
Some features are distributed under an experimental flag. This means that the feature is already part of the main package but is not enabled by default. To enable the feature you need to set the corresponding flag in the qwikVite experimental[] array.

As a separate node package.
Qwik labs are distributed as a separate node package. Because Qwik Labs is "work in progress" the node package is not published to NPM but instead as a github URL. The package is continually updated and so it will always contains the latest build. (You may read up on installing node packages here.)

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

Or just add this to your package.json

```
{
  ...
  "dependencies": {
    ...
    "@builder.io/qwik-labs": "github:QwikDev/qwik-labs-build#main",
  }
}
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
