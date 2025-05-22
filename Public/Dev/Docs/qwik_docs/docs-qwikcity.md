# https://qwik.dev/docs/qwikcity/

[Original link](https://qwik.dev/docs/qwikcity/)

# Qwik City

While Qwik focuses on the Component API, Qwik City provides APIs that support components with common server-focused features, including the following:

Qwik¹ City²

Qwik¹: Core framework, stable, primitives, component model.

City²: Opinionated file-based router, middleware, endpoints, and data fetching and update.

Qwik City is a meta-framework for Qwik. Qwik City is to Qwik, what Next.js is to React, Nuxt is to Vue, SvelteKit to Svelte, and Analog is to Angular.

Qwik (core) and Qwik City (routing) solve problems at two layers of abstraction. Qwik, focuses on component and state management primitives, while Qwik City brings an opinionated and performant way to build sites at scale. We don't want to lock the ecosystem into a single correct way of building sites; in fact, we encourage the community to build alternative solutions on top of Qwik.

While Qwik City is full of useful functionality, thanks to Qwik's resumability and JavaScript streaming, there is no additional cost to the end user from Qwik City. (zero JavaScript).

Use Qwik City to build an e-commerce website, blog site, or any other website that needs routing, layouts, or data retrieval/updates. Qwik City is built on Qwik, and therefore Qwik City sites are resumable and only download the minimal amount of JavaScript with fine-grained lazy loading.

## Getting Started with Qwik City

Visit Create an app using the CLI to see how to create a new Qwik City starter project. It is as simple as:

```
pnpm create qwik@latest
```

```
npm create qwik@latest
```

```
yarn create qwik
```

```
bun create qwik@latest
```

## High Level API Overview

This table shows which file (index.tsx vs layout.tsx) the respective feature should be implemented in.

## Partytown

Qwik City also comes pre-integrated with Partytown allowing you to execute your third-party code off the main thread.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
