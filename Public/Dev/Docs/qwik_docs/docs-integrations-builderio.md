# https://qwik.dev/docs/integrations/builderio/

[Original link](https://qwik.dev/docs/integrations/builderio/)

# Builder.io

Builder.io is a Visual Headless CMS. Think about it as a drag-and-drop CMS that integrates into your existing Qwik codebase, allowing you and your team to edit content without having to write code.

## Setup

You can add builder.io easily by using the following add script:

```
pnpm run qwik add builder.io
```

```
npm run qwik add builder.io
```

```
yarn run qwik add builder.io
```

```
bun run qwik add builder.io
```

After running the command, @builder.io/sdk-qwik will be installed, and a new sample component and catchall route will be created in src/components and src/routes respectively.

Create a free Builder.io account (only takes a couple minutes), and paste your public API key into .env

```
- BUILDER_PUBLIC_API_KEY=YOUR_API_KEY
+ BUILDER_PUBLIC_API_KEY=abc123
```

Then run the development server:

```
pnpm run dev
```

```
npm run dev
```

```
yarn run dev
```

```
bun run dev
```

Now, go set your preview URL to http://localhost:5173/

Now, let's create a page in Builder.io and see it live in Qwik!

Now, try out the visual editor! You can find a custom Qwik components
in the Custom Components section of the insert tab.

You may also limit visual editing to only your custom components with components-only mode.

## Register your components

One of the killer features of a Visual Headless CMS, is that you can expose your components to the CMS, ie, your Qwik components can be used as blocks in Builder.io.

```
import { MyFunComponent } from './fun/fun';
 
export const CUSTOM_COMPONENTS: RegisteredComponent[] = [
  {
    component: MyFunComponent,
    name: 'MyFunComponent',
    inputs: [
      {
        name: 'text',
        type: 'string',
        defaultValue: 'Hello world',
      },
    ],
  },
];
 
export default component$(() => {
  const content = useBuilderContent();
  return (
    <RenderContent
      customComponents={CUSTOM_COMPONENTS}
    />
  );
});
```

## Next Steps

See our full integration guides here

Also, when you push your integration to production, go back and update your preview URL to your production URL so now anyone on your team can visually create content in your Qwik app!

Also, to integrate structured data, see this guide

### Contributors

Thanks to all the contributors who have helped make this documentation better!
