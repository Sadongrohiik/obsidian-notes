# https://qwik.dev/docs/project-structure/

[Original link](https://qwik.dev/docs/project-structure/)

# Project Structure

A typical Qwik project looks like this:

```
qwik-app-demo
├── README.md
├── package.json
├── public
│   └── favicon.svg
├── src
│   ├── components
│   │   └── router-head
│   │       └── router-head.tsx
│   ├── entry.ssr.tsx
│   ├── global.css
│   ├── root.tsx
│   └── routes
│       ├── flower
│       │   ├── flower.css
│       │   └── index.tsx
│       ├── index.tsx
│       └── layout.tsx
├── tsconfig.json
└── vite.config.ts
```

## Project files

### src/routes/

The src/routes/ directory is a special directory where Qwik City will look for your pages. Folders and files inside this directory have a special meaning and they will be mapped to the URL of your app.

Refer to the Routing section for more information.

### src/components/

The directory named src/components/ follows a standard convention. It's present in all Qwik starters and you can rename it if you prefer. The src/components/ directory is where to put your components (i.e. reusable pieces of code that can be used in multiple places). These components are not routes or layouts, but they can be referenced from within your route or layout code.

For example, a Button component should be inside src/components/button/button.tsx.

### public/

The public/ directory contains static assets such as images, fonts, and icons. When you build your app, these files will be copied to the dist/ directory and served at the root.

Refer to Vite configuration for more information.

### src/entry.ssr.tsx

The SSR entry point is the common entry point in all cases where the application is rendered outside of the browser.

### src/root.tsx

The src/root.tsx file is the root of the application tree.  It is the entry point and is the first component that will be rendered.

### src/global.css

The src/global.css file is a global CSS file, if you need to define some CSS that is used in multiple places in your app, you can define it here.

The root component (src/root.tsx) imports this file by default.

### tsconfig.json

The tsconfig.json file contains the TypeScript compiler configuration. It's standard for any TypeScript project.

### vite.config.ts

Qwik uses Vite to build the project. The vite.config.ts file contains the Vite configuration. It's standard for any Vite project. Please refer to the Vite documentation for more information.

## Utilities

Qwik has a utility command called new that allows developers to easily create new components and routes.

Let's say you wanted to create a new component called Button, you would run the command:

```
pnpm run qwik new Button
```

```
npm run qwik new Button
```

```
yarn run qwik new Button
```

```
bun run qwik new Button
```

Maybe you want to create a new route for the /contact page. To do that, you could use the command:

```
pnpm run qwik new /contact
```

```
npm run qwik new /contact
```

```
yarn run qwik new /contact
```

```
bun run qwik new /contact
```

The following commands are consistent with Qwik's directory file structure, allowing you to scaffold components more quickly.

If we compare our qwik-app-demo from the top of the page, the additional changes would look like this:

```
qwik-app-demo
├── README.md
├── package.json
├── public
│   └── favicon.svg
├── src
│   ├── components
│   │   └── router-head
│   │       └── router-head.tsx
│   │       Button
│   │       └── button.tsx
│   ├── entry.ssr.tsx
│   ├── global.css
│   ├── root.tsx
│   └── routes
│       ├── flower
│       │   ├── flower.css
│       │   └── index.tsx
│       ├── contact
│       │   └── index.tsx
│       ├── index.tsx
│       ├── layout.tsx
│       └── service-worker.ts
├── tsconfig.json
└── vite.config.ts
```

If you prefer to generate the Button component with the Button/index.tsx naming convention, you could use the command:

```
pnpm run qwik new --barrel Button
```

```
npm run qwik new --barrel Button
```

```
yarn run qwik new --barrel Button
```

```
bun run qwik new --barrel Button
```

In that case, the src/components folder would look like this:

```
src
│   ├── components
│   │   └── router-head
│   │       └── router-head.tsx
│   │       Button
│   │       └── index.tsx
```

This feature was added in Qwik v1.2, and those using an older version will not see this functionality.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
