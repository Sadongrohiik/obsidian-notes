# https://qwik.dev/docs/integrations/og-img/

[Original link](https://qwik.dev/docs/integrations/og-img/)

# OG Image (og-img)

With og-img you can easily add dynamic Open Graph images to your Qwik website. These are displayed, for example, when your website is shared on social media or via messenger services.

og-img is a framework agnostic package for generating Open Graph images using Satori and resvg.

To get started, install the og-img package:

```
pnpm install og-img
```

```
npm install og-img
```

```
yarn add og-img
```

```
bun install og-img
```

## How it works

To generate an image, all you need to do is return an ImageResponse via a server endpoint. To create one, add a new route to your Qwik website and export a function called onGet in the index file. To easily define the content of your image, you can use the html tagged template literal.

To get proper syntax highlighting for the tagged template literal in Visual Studio Code, you can install the lit-html extension.

```
import type { RequestHandler } from '@builder.io/qwik-city';
import { fetchFont, ImageResponse, html } from 'og-img';
 
export const onGet: RequestHandler = async ({ send }) => {
  send(
    new ImageResponse(
      // Use Tailwind CSS or style attribute
      html`
        <div tw="text-4xl text-green-700" style="background-color: tan">
          Hello, world!
        </div>
      `,
      {
        width: 1200,
        height: 600,
        fonts: [
          {
            name: 'Roboto',
            // Use `fs` (Node.js only) or `fetch` to read font file
            data: await fetchFont(
              'https://www.example.com/fonts/roboto-400.ttf'
            ),
            weight: 400,
            style: 'normal',
          },
        ],
      }
    )
  );
};
```

Then all you need to do is point to this API endpoint with a meta tag in the head of your Qwik website to embed the Open Graph image.

```
<head>
  <title>Hello, world!</title>
  <meta property="og:image" content="https://www.example.com/og-image" />
</head>
```

You can also generate the meta tag dynamically by export a head object in your routes.

```
import { component$ } from '@builder.io/qwik';
import type { DocumentHead } from '@builder.io/qwik-city';
 
export default component$(() => {
  return <h1>Hello, world!</h1>;
});
 
export const head: DocumentHead = {
  title: 'Hello, world!',
  meta: [
    {
      property: 'og:image',
      content: 'https://www.example.com/og-image',
    },
  ],
};
```

You can use URL parameters to dynamically change the content of your Open Graph image. Take a look at Valibot's Open Graph image. You can find the source code here.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
