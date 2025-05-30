# https://qwik.dev/docs/pages/

[Original link](https://qwik.dev/docs/pages/)

# Pages

Pages are created by adding a new index.tsx file in the src/routes directory. Pages export a default Qwik component, which will be rendered as the content of the page.

```
import { component$ } from '@builder.io/qwik';
 
// Notice the default export
export default component$(() => {
  return <h1>Hello World!</h1>;
});
```

The only difference between a page and an endpoint is that an endpoint only exports an onRequest, onGet, onPost, onPut, onDelete, onPatch, or onHead function, which will be used to handle the incoming request.

## head export

Every page can export a head property (or function) that returns a DocumentHead object. The DocumentHead object is used to resolve the title of the page, as well as the meta, links and styles.

This API allows you to set the title of the page, as well as the meta, open graph, twitter tags and links. This is useful for SEO and social sharing.

```
import { component$ } from '@builder.io/qwik';
import type { DocumentHead } from '@builder.io/qwik-city';
 
export default component$(() => {
  return <h1>About page</h1>;
});
 
export const head: DocumentHead = {
  // This will be used to resolve the <title> of the page
  title: 'About page',
  meta: [
    {
      name: 'description',
      content: 'This is the about page',
    },
    // Open graph
    {
      property: 'og:title',
      content: 'About page',
    },
    {
      property: 'og:description',
      content: 'This is the about page',
    },
  ],
  links: [
    {
      rel: 'canonical',
      href: 'https://example.com/about',
    },
  ],
};
```

The example above sets the title, as well as some Open Graph meta and the canonical link.

HTML places the <head> tag as the first element within <html> (at the very top of the HTML content). The <head> section is not something that your route component renders directly because it would break the HTML streaming.

Look into useDocumentHead() to read and consume the DocumentHead object from within your component.

### Dynamic Head

You can also export a function that returns a DocumentHead object, allowing you to programmatically set the <title>, <meta> or <link> tags.

This allows you to configure the <head>, including the title, meta or links using data from routeLoader$() or routeAction$().

We can use the resolveValue method to get the value of a routeLoader$() or routeAction$() within the head function.

```
import { component$ } from '@builder.io/qwik';
import { routeLoader$ } from '@builder.io/qwik-city';
import type { DocumentHead } from '@builder.io/qwik-city';
 
export const useJoke = routeLoader$(async (requestEvent) => {
  // Fetch a joke from a public API
  const jokeId = requestEvent.params.jokeId;
  const response = await fetch(`https://api.chucknorris.io/jokes/${jokeId}`);
  const joke = await response.json();
  return joke;
});
 
// Now we can export a function that returns a DocumentHead object
export const head: DocumentHead = ({resolveValue, params}) => {
  const joke = resolveValue(useJoke);
  return {
    title: `Joke "${joke.title}"`,
    meta: [
      {
        name: 'description',
        content: joke.text,
      },
      {
        name: 'id',
        content: params.jokeId,
      },
    ],
  };
};
```

### Nested Layouts and Head

In an advanced case, a layout may want to modify the document title of an already resolved document head. In the example below, the page component returns the title of Foo. The containing layout component can read the value of the page's document head and modify it. In this example, the layout component is adding MyCompany -  to the title, so that when rendered, the title will be MyCompany - Foo. Every layout in the stack has the opportunity to return a new value.

```
──src/
  └─routes/
    ├─index.tsx
    └─layout.tsx
```

```
export const head: DocumentHead = {
  title: `Foo`,
};
```

```
export const head: DocumentHead = ({ head }) => {
  return {
    title: `MyCompany - ${head.title}`,
  };
};
```

### Google Structured Data

This example integrates Google Structured Data
which helps by providing explicit clues about the meaning of a page to Google.
If you want to embed custom JavaScript code, it would be ideal to do it lazily with Partytown.
Sometimes, however, you are forced to load them immediately. The following example illustrates this.

```
import { component$ } from '@builder.io/qwik';
import type { DocumentHead } from '@builder.io/qwik-city';
 
export default component$(() => {
  return <h1>About page</h1>;
});
 
export const head: DocumentHead = {
  scripts: [
    {
      props: {
        type: "application/ld+json",
      },
      script: JSON.stringify({
        "@context": "https://schema.org",
        "@type": "ItemList",
      }),
    },
  ],
};
```

The example above sets some Structured Data Markup.

Note: You need to change router-head component to render head.scripts.

```
import { component$ } from "@builder.io/qwik";
import { useDocumentHead, useLocation } from "@builder.io/qwik-city";
 
export const RouterHead = component$(() => {
  const head = useDocumentHead();
  const loc = useLocation();
 
  return (
    <>
      <title>{head.title}</title>
 
      {/* add this  */}
      {head.scripts.map((s) => (
        <script key={s.key} {...s.props} dangerouslySetInnerHTML={s.script} />
      ))}
    </>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
