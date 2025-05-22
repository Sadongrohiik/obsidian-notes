# https://qwik.dev/docs/html-attributes/

[Original link](https://qwik.dev/docs/html-attributes/)

# HTML attributes

Occasionally, it is necessary to add attributes to a website to enable specific functionalities, such as controlling the application's theme, determining text direction with the ﻿dir attribute, or setting the page language with the ﻿lang attribute. Typically, adding these attributes to the HTML tag is practical since it generally serves as the application's container.

To apply these attributes in Qwik city, add them to containerAttributes in the src/entry.ssr.tsx file:

```
export default function (opts: RenderToStreamOptions) {
  return renderToStream(<Root />, {
    manifest,
    ...opts,
    // Use container attributes to set attributes on the html tag.
    containerAttributes: {
      lang: "en-us",
      ...opts.containerAttributes,
    },
  });
}
```

In addition, the opts.serverData object and nested objects allow you to access information about the request, including ﻿request headers, url, route params, and more. Leveraging this information enables you to do the following:

```
export default function (opts: RenderToStreamOptions) {
  // With this route structure src/routes/[locale]/post/[id]/index.tsx
  const isRTL = opts.serverData?.qwikcity.params.locale === 'ar';
 
  return renderToStream(<Root />, {
    manifest,
    ...opts,
    containerAttributes: {
      dir: isRTL ? 'rtl' : 'ltr'
      ...opts.containerAttributes,
    },
  });
}
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
