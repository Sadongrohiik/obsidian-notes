# https://qwik.dev/docs/advanced/content-security-policy/

[Original link](https://qwik.dev/docs/advanced/content-security-policy/)

# Content Security Policy

## What is CSP?

Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross-Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft, to site defacement, to malware distribution.

## Steps to integrate

These steps only work for SSR approach. If you are using the Server Side Generation approach, you don't have an up and running server, so this code will not run during the page request.

### Add a route plugin

To add the middleware plugin to your application, simply add a file named [email protected] to the routes folder.
This file will be loaded with every request, allowing you to add headers, modify the response, and more.

```
src/
└── routes/
    ├── [email protected]         # The plugin which runs on every request (route middleware)
    ├── contact/
    │   └── index.mdx         # https://example.com/contact
    ├── about/
    │   └── index.md          # https://example.com/about
    ├── index.mdx             # https://example.com/
    │
    └── layout.tsx            # This layout is used for all pages
```

#### Example

This template provides very permissive backward-compatible defaults.
It is highly recommended that you customize it to better suit your specific use case.
As this is an advanced topic, you should take a closer look at MDN or web.dev to get a better understanding of CSP.
Please note that in dev mode the Vite scripts have no nonce and will report. For this reason, the example will not add csp in dev mode.

```
import type { RequestHandler } from "@builder.io/qwik-city";
import { isDev } from "@builder.io/qwik";
 
export const onRequest: RequestHandler = event => {
  if (isDev) return; // Will not return CSP headers in dev mode
  const nonce = Date.now().toString(36); // Your custom nonce logic here
  event.sharedMap.set("@nonce", nonce);
  const csp = [
    `default-src 'self' 'unsafe-inline'`,
    `font-src 'self'`,
    `img-src 'self' 'unsafe-inline' data:`,
    `script-src 'self' 'unsafe-inline' https: 'nonce-${nonce}' 'strict-dynamic'`,
    `style-src 'self' 'unsafe-inline'`,
    `frame-src 'self' 'nonce-${nonce}'`,
    `object-src 'none'`,
    `base-uri 'self'`,
  ];
 
  event.headers.set("Content-Security-Policy", csp.join("; "));
};
```

### Custom scripts

If you have custom script tags that you need to add the nonce to, you can use the useServerData hook to get the nonce from the server and add it to your script tags.

```
export default component$(() => {
  const nonce = useServerData<string | undefined>("nonce");
  return (
    <div>
      <script nonce={nonce}>alert("Hello world")</script>
    </div>
  );
});
```

## Validate your CSP

There is a great tool to validate your CSP: https://csp-evaluator.withgoogle.com/

### Contributors

Thanks to all the contributors who have helped make this documentation better!
