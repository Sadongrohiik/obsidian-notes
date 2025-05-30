# https://qwik.dev/docs/guides/mdx/

[Original link](https://qwik.dev/docs/guides/mdx/)

# MDX

An alternative way to author content is using .mdx files (Markdown JSX). These files are authored as Markdown, but they are compiled down to Qwik components. In addition to Markdown syntax, .mdx files can also refer to other components.

Let's assume you have your routes set up like this:

```
src/
└── routes/
    └── some/
        └── path/
            └── index.mdx    # https://example.com/some/path
```

```
---
title: Hello World Title
---
 
This is a simple hello world component.
```

The above component will be rendered at https://example.com/some/path.

## Importing other components.

MDX is a creative opportunity for you to come up with new content quickly ("Qwikly" 🙂) and if you need more interaction on your page you can seamlessly integrate your Qwik components like so:

```
src/
├── components/
|   └── counter
│       └──  counter.tsx
└── routes/
    └── some/
        └── path/
            └── index.mdx    # https://example.com/some/path
```

```
---
title: Hello World Title
---
import { Counter } from "../../../components/counter/counter";
 
This is a simple hello world component.
 
<Counter />
```

```
import { component$, useSignal } from '@builder.io/qwik';
 
export const Counter = component$(() => {
  const count = useSignal(0);
 
  return (
    <button class="counter" type="button" onClick$={() => count.value++}>
      Increment {count.value}
    </button>
  );
});
```

Note: A key difference between Qwik City and many current meta-frameworks is directory-based routing. Every route needs to be defined as a-directory/index.(tsx,ts,js,jsx,md,mdx).

In other meta-frameworks you're used to about.mdx will render a route http://example.com/about. However, this will not work in Qwik City. You must rename the file to about/index.mdx for Qwik City to know to render it.

## Disabling default MDX plugins included.

Qwik City includes 3 plugins by default.

These plugins can be disabled independently in the following way:

```
import { defineConfig } from 'vite';
import { qwikCity } from '@builder.io/qwik-city/vite';
// See below
import rehypeAutolinkHeadings from 'rehype-autolink-headings';
export default defineConfig(() => {
  return {
    plugins: [
      qwikCity({
        mdxPlugins: {
          remarkGfm: false,
          rehypeSyntaxHighlight: false,
          rehypeAutolinkHeadings: false,
        },
        mdx: {
          rehypePlugins: [
            // Plugins can now be added manually to use a different configuration
            [rehypeAutolinkHeadings, { behavior: 'wrap' }],
          ],
        },
      }),
      /* the rest of the configuration */
    ],
  };
});
```

## Open Graph Properties

You can use og or opengraph property to define Open Graph protocol metadata.

```
title: My Title
description: My Description
og:
  - title: My Custom Title
    description: true
  - image: https://example.com/rock.jpg
    image:alt: A shiny red apple with a bite taken out
  - image: https://example.com/rock2.jpg
```

Setting og:title or og:description to true will check and use outside title and description property instead. Thus, you can avoid writing a same title and description twice.

The above example will generate the following HTML code.

```
<title>My Title</title>
<meta name="description" content="My Description" />
 
<meta property="og:title" content="My Custom Title" />
<meta property="og:description" content="My Description" />
 
<meta property="og:image" content="https://example.com/rock.jpg" />
<meta property="og:image:alt" content="A shiny red apple with a bite taken out" />
 
<meta property="og:image" content="https://example.com/rock2.jpg" />
```

## Reading frontmatter data

Frontmatter keys are accessible by leveraging the useDocumentHead() hook.

```
---
title: Hello World Title
tags:
  - super
  - exiting
  - docs
---
import { Tags } from "../../../components/tags/tags";
 
This is a simple hello world component.
 
<Tags />
```

```
import { component$ } from '@builder.io/qwik';
import { useDocumentHead } from '@builder.io/qwik-city';
 
export const Tags = component$(() => {
  const { frontmatter } = useDocumentHead();
  
  if (frontmatter.tags.length === 0) {
    return null;
  }
  
  return (
    <ul>
      {frontmatter.tags.map((tag: string) => (
        <li key={`tag-${tag}`}>{tag}</li>
      ))}
    </ul>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
