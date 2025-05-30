# https://qwik.dev/docs/cookbook/glob-import/

[Original link](https://qwik.dev/docs/cookbook/glob-import/)

# Glob Import & Dynamic Import

As you probably know, Qwik takes care of lazy-loading for you in order to make your app performant and scalable by default.

As a consequence of this automatic optimization, you don't need to and shouldn't use vite's dynamic imports feature as it conflicts with the optimizer.

But there are still some cases where you may need to import a lot of files from a directory and you may not want to type out all the file paths. For that kind of situation, you can use import.meta.glob.

## import.meta.glob

The goal of using import.meta.glob is to allow you to create a wrapper component to which you can pass a name prop to chose which component you want to import:

```
<MetaGlobComponent name="file-name" />
<MetaGlobComponent name="another-file-name" />
<MetaGlobComponent name="etc." />
```

As written in the Vite documentation, import.meta.glob comes with a few features that allow you to specify how to import your files.

By default you can simply use pattern matching to specify which files should be imported from which folder:

```
const metaGlobComponents: any = import.meta.glob('/src/components/*');
```

But you can also pass in additional options like import, as, or eager:

```
const metaGlobComponents: any = import.meta.glob('/src/components/*', {
  import: 'default',
  as: 'raw',
  eager: true, // defaults to false
});
```

## How to

The problem with import.meta.glob in Qwik, is that it currently either works in development and doesn't in preview/production, or it works in preview/production but gets slower and slower in development as the number of imported files increases.

The reason for this behavior, is that import.meta.glob with eager.false breaks the production bundle as it creates lazy-loadable chunks that Qwik doesn't know how to handle. On the other hand, eager:true seemingly fixes the issue as it allows Qwik to normally bundle the files, but it also slows down the development server - especially when you import a lot of heavy components with it.

As a workaround for now, you can use the build time isDev boolean from "@builder.io/qwik":

```
import {
  type Component,
  component$,
  useSignal,
  useTask$,
} from '@builder.io/qwik';
import { isDev } from '@builder.io/qwik';
 
const metaGlobComponents: Record<string, any> = import.meta.glob(
  '/src/examples/*',
  {
    import: 'default',
    eager: isDev ? false : true,
  }
);
 
export default component$(() => {
  return (
    <div>
      <MetaGlobExample name="example1" />
      <MetaGlobExample name="example2" />
      <MetaGlobExample name="example3" />
    </div>
  );
});
 
export const MetaGlobExample = component$<{ name: string }>(({ name }) => {
  const MetaGlobComponent = useSignal<Component<any>>();
  const componentPath = `/src/examples/${name}.tsx`;
 
  useTask$(async () => {
    MetaGlobComponent.value = isDev
      ? await metaGlobComponents[componentPath]()
      // We need to call `await metaGlobComponents[componentPath]()` in development as it is `eager:false`
      : metaGlobComponents[componentPath];
      // We need to directly access the `metaGlobComponents[componentPath]` expression in preview/production as it is `eager:true`
  });
 
  return <>{MetaGlobComponent.value && <MetaGlobComponent.value />}</>;
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
