# https://qwik.dev/docs/layout/

[Original link](https://qwik.dev/docs/layout/)

# Nested Layouts

Layouts provide nested UI and request handling (middleware) to a set of routes:

## Example

Now, combine all the previously discussed concepts to build a full app.

In the proposed example, you will notice a site with 2 pages: https://example.com and https://example.com/about. The goal is to add a common header and footer to all the pages, the only difference between the pages is the content in the middle.

```
┌───────────────────────────────────────────────────┐
│ Header                                            │
├─────────┬─────────────────────────────────────────┤
│ Menu    │ <ROUTE_SPECIFIC_CONTENT>                │
│ - home  │                                         │
│ - about │                                         │
│         │                                         │
├─────────┴─────────────────────────────────────────┤
│ Footer                                            │
└───────────────────────────────────────────────────┘
```

First, create three components: <Header>, <Footer>, and <Menu>.

The developer could copy-paste these components manually into each page component, but that is repetitive and error-prone. Instead, use layouts to automatically reuse common parts.

### Routes directory

```
src/
├── components/
│   ├── header.tsx         # Header component implementation
│   ├── footer.tsx         # Footer component implementation
│   └── menu.tsx           # Menu component implementation
└── routes/
    ├── layout.tsx         # Layout implementation using: <Header>, <Footer>, and <Menu>
    ├── about/
    │   └── index.tsx      # https://example.com/about
    └── index.tsx          # https://example.com
```

### src/routes/layout.tsx

It will be used for all routes under the src/routes directory. It will render the Header, Menu, and Footer components, and also render the nested routes under the Slot component.

```
import { component$, Slot } from '@builder.io/qwik';
 
export default component$(() => {
  return (
    <>
      <Header />
      <Menu />
      <Slot /> {/* <== This is where the route will be inserted */}
      <Footer />
    </>
  );
});
```

### src/routes/index.tsx

This is the main route for the site. It will be rendered within the Slot component in the src/routes/layout.tsx file. Even though the Header, Menu, or Footer components are not referenced, it will still be rendered with them.

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  return <>Home</>;
});
```

### src/routes/about/index.tsx

Similar to the src/routes/index.tsx file, the about route will also be rendered within the Slot component in the src/routes/layout.tsx file. Even though the Header, Menu, or Footer components are not referenced, it will still be rendered with them.

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  return <>About</>;
});
```

When you run the app, Qwik will render the About nested inside the RootLayout

```
<RootLayout>
  <AboutPage />
</RootLayout>
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
