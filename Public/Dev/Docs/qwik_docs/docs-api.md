# https://qwik.dev/docs/api/

[Original link](https://qwik.dev/docs/api/)

# API reference

## useContent()

The useContent() function retrieves the nearest content information for the current route. The returned object includes:

```
headings: ContentHeading[] | undefined;
menu: ContentMenu | undefined;
```

The headings array includes data about a markdown file's <h1> to <h6> html heading elements.

Menus are contextual data declared with menu.md files. See menus file definition for more information on the file format and location.

## useDocumentHead()

Use the useDocumentHead() function to read the document head metadata.

useDocumentHead() retrieves a readonly DocumentHead object that includes:

```
export interface DocumentHead {
  /**
   * Represents the `<title>` element of the document.
   */
  readonly title?: string;
  /**
   * Used to manually set meta tags in the head. Additionally, the `data`
   * property could be used to set arbitrary data which the `<head>` component
   * could later use to generate `<meta>` tags.
   */
  readonly meta?: readonly DocumentMeta[];
  /**
   * Used to manually append `<link>` elements to the `<head>`.
   */
  readonly links?: readonly DocumentLink[];
  /**
   * Used to manually append `<style>` elements to the `<head>`.
   */
  readonly styles?: readonly DocumentStyle[];
  /**
   * Arbitrary object containing custom data. When the document head is created from
   * markdown files, the frontmatter attributes that are not recognized as a well-known
   * meta names (such as title, description, author, etc...), are stored in this property.
   */
  readonly frontmatter?: Readonly<Record<string, any>>;
}
```

All starters include a <RouterHead> component that is responsible for generating the <head> element of the document. It uses the useDocumentHead() function to retrieve the current head metadata and render the appropriate <meta>, <link>, <style> and <title> elements.

```
import { component$ } from '@builder.io/qwik';
import { useDocumentHead } from '@builder.io/qwik-city';
 
/**
 * The RouterHead component is placed inside of the document `<head>` element.
 */
export const RouterHead = component$(() => {
  const head = useDocumentHead();
 
  return (
    <>
      <title>{head.title}</title>
 
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
 
      {head.meta.map((m) => (
        <meta {...m} />
      ))}
 
      {head.links.map((l) => (
        <link {...l} />
      ))}
 
      {head.styles.map((s) => (
        <style {...s.props} dangerouslySetInnerHTML={s.style} />
      ))}
    </>
  );
});
```

## useLocation()

Use the useLocation() function to retrieve a RouteLocation object for the current location.

The useLocation() function provides the current URL and params. It also determines if the app is currently navigating, which is useful for showing a loading indicator.

```
export interface RouteLocation {
  /**
   * Route params extracted from the URL.
   */
  readonly params: Record<string, string>;
  /**
   * The current URL.
   */
  readonly url: URL;
  /**
   * True if the app is currently navigating.
   */
  readonly isNavigating: boolean;
}
```

The return value of useLocation() is similar to document.location, but it is safe to use on the server where there is no global location object, and it's reactive so it can be tracked.

### Path Route Parameters

useLocation() encodes the Route Parameters as params.

Assume you have:

```
import { component$ } from '@builder.io/qwik';
import { useLocation } from '@builder.io/qwik-city';
 
export default component$(() => {
  const loc = useLocation();
 
  return (
    <>
      <h1>SKU</h1>
      {loc.isNavigating && <p>Loading...</p>}
      <p>pathname: {loc.url.pathname}</p>
      <p>skuId: {loc.params.skuId}</p>
    </>
  );
});
```

The above code would generate:

```
<h1>SKU</h1>
<p>pathname: /sku/1234/</p>
<p>skuId: 1234</p>
```

### useLocation in root.tsx is not supported

To access the current url from root.tsx use this pattern:

```
const serverDataUrl = useServerData<string>('url');
const url = new URL(serverDataUrl || 'https://unknown');
```

Notice that useLocation is a read-only API, you should never attempt to mutate the values of the loc object returned. Instead look into the useNavigate() API.

## useNavigate()

The useNavigate() hook returns a function that programmatically navigates to the next page without requiring a user click or causing a full-page reload. This function can be called with a string argument to "push" a new path, or without arguments to cause an SPA refresh of the page. This is the API used by the <Link> component internally to support SPA navigation.

```
import { component$ } from '@builder.io/qwik';
import { useNavigate } from '@builder.io/qwik-city';
 
export default component$(() => {
  const nav = useNavigate();
 
  return (
    <>
      <button
        onClick$={async () => {
          // SPA navigate to /dashboard
          await nav('/dashboard');
        }}
      >
        Go to dashboard
      </button>
 
      <button
        onClick$={async() => {
          // refresh page: call without arguments
          await nav();
        }}
      >
        Refresh page
      </button>
    </>
  );
});
```

This component has a button that when clicked, will navigate to /dashboard without causing a page reload.

Notice that for SEO, and accessibility it's better to use the <Link> component instead of useNavigate() programmatically to navigate to a new page after some user interaction.

### Going back

To programmatically navigate back to the previous page, use the useNavigate and useLocation hooks.

```
import { component$ } from '@builder.io/qwik';
import { useNavigate, useLocation } from '@builder.io/qwik-city';
 
export const BackButton = component$(() => {
  const nav = useNavigate();
  const loc = useLocation();
 
  return (
    <button onClick$={() => loc.prevUrl ? window.history.back() : nav('/')}>
      Go Back
    </button>
  );
});
```

The fallback in the nav function ensures that if the previous URL (loc.prevUrl) is not available, the user is redirected to a default path (eg. the root path /). This is useful in scenarios where the navigation history might not include a previous URL, such as when the user directly lands on a specific page without navigating from another page within the app.

Notice that the loc.prevUrl is only available when the user navigates to a page using the useNavigate() or <Link>. It is not available when the user navigates to a page using the anchor element.

## routeLoader$()

The routeLoader$() function is used to declare a new Server Loader in the given page/middleware or layout. Qwik City will execute all the declared loaders for the given route match. Qwik Components can later reference the loaders by importing them and calling the returned custom hook function in order to retrieve the data.

```
import { component$ } from '@builder.io/qwik';
import { routeLoader$ } from '@builder.io/qwik-city';
 
export const useGetTime = routeLoader$(async () => {
  return { time: new Date() }
});
export default component$(() => {
  const signal = useGetTime(); // Signal<{time: Date}>
  console.log('Date': signal.value.time);
  return (
    <div>{signal.value.time.toISOString()}</div>
  )
});
```

Please refer to the Route Loader section for more information.

## routeAction$()

The routeAction$() function is used to declare a new Server Action in the given page/middleware or layout. Qwik City will execute only the invoked action after some user interaction (such as a button click or a form submission).

Please refer to the Server Actions section for more information.

## <QwikCityProvider>

The QwikCityProvider component initializes Qwik City in the existing document, providing the necessary context for Qwik City to work, such as useContent() and useLocation().

This component is usually located at the very root of your application. In most of the starters, you will find it in the src/root.tsx file:

```
export default component$(() => {
  /**
   * The root of a QwikCity site always start with the <QwikCityProvider> component,
   * immediately followed by the document's <head> and <body>.
   *
   * Don't remove the `<head>` and `<body>` elements.
   */
 
  return (
    <QwikCityProvider>
      <head>
        <meta charSet="utf-8" />
        <link rel="manifest" href="/manifest.json" />
        <RouterHead />
      </head>
      <body lang="en">
        <RouterOutlet />
      </body>
    </QwikCityProvider>
  );
});
```

QwikCityProvider does not render any DOM element, not even the matched route. It merely initializes Qwik City core logic so it should not be used more than once in the same app.

## <QwikCityMockProvider>

The QwikCityMockProvider component initializes a Qwik City context for testing. It provides the necessary context for Qwik City code to work in tests, such as useContent(). Vice versa for useNavigate(), <Link>, useLocation() and so on.
It is recommended that you use this in your test files.

QwikCityMockProvider does not render any DOM elements, meaning it won't be visible in snapshots

If you are looking for a general example on how to integrate vitest into your Qwik look checkout the vitest integration documentation

```
import { createDOM } from '@builder.io/qwik/testing';
import { QwikCityMockProvider } from '@builder.io/qwik-city';
import { test, expect } from 'vitest';
 
// Component with two props. Uses <Link> internally. Omitted for brevity
import { Card } from './card';
 
const cases = [
  {text: 'qwik', link:'https://qwik.dev/docs/api'}, 
  {text: 'vitest', link: 'https://vitest.dev'}
];
 
test.each(cases)('should render card with %s %s', async ({text, link}) => {
  const { screen, render } = await createDOM();
  await render(
    <QwikCityMockProvider>
      <Card text={text} link={link} />
    </QwikCityMockProvider>,
  );
  expect(screen.innerHTML).toMatchSnapshot();
});
```

a goto prop can be passed to customize the navigate behavior during tests

```
import { $ } from '@builder.io/qwik';
import { createDOM } from '@builder.io/qwik/testing';
import { test, expect, vi } from 'vitest';
 
// Component with one prop. Uses useNavigate internally. Omitted for brevity
import { Button } from '../button';
 
const goto = vi.fn(async (path, options) => {
  console.log(`Navigating to ${path} with ${options}`);
});
 
test('should render the button and navigate', async () => {
  const { screen, render, userEvent } = await createDOM();
  const goto$ = $(goto);
  await render(
    <QwikCityMockProvider goto={goto$}>
      <Button id="button" />
    </QwikCityMockProvider>,
  );
  expect(screen.innerHTML).toMatchSnapshot();
  await userEvent('#button', 'click');
  expect(goto).toHaveBeenCalled();
});
```

## <RouterOutlet>

The RouterOutlet component is responsible for rendering the matched route at a given moment, it internally uses the useContent() to render the current page, as well as all of the nested layouts.

This component is usually located as a child of <body>, in most of the starters you will find it in the src/root.tsx file (refer to the example in QwikCityProvider).

## <Form>

The Form component is a wrapper around the native <form> element, and it's designed to work side by side with Server Actions.

Since this component uses the native <form> element, it will work with any browser with and without JavaScript enabled. In addition, it enhances the native <form> element by capturing the submit event and preventing the default behavior, so it will behave like an SPA (Single Page Application) instead of a full page reload.

```
import { component$ } from '@builder.io/qwik';
import { Form, routeAction$ } from '@builder.io/qwik-city';
 
// this action will be called when the form is submitted
export const useLoginAction = routeAction$((data, { cookies, redirect }) => {
  if (validate(data.username, data.password)) {
    cookies.set('auth', getAuthToken(data.username));
    throw redirect(302, '/dashboard');
  }
});
 
export default component$(() => {
  const login = useLoginAction();
 
  return (
    <Form action={login}>
      <input type="text" name="username" />
      <input type="password" name="password" />
      <button type="submit">Login</button>
    </Form>
  );
});
```

## <Link>

The Link component works like the <a> anchor element, but instead of causing a full page to reload, it will navigate as a SPA (Single Page Navigation). This is useful if you need to navigate without losing your current state.

Notice that full-page reloads in Qwik are extremely cheap. Other frameworks abuse SPA links because a full-page reload requires JS to hydrate and re-execute everything. This is not the case for Qwik. Through investigation of internal testing, using <a> usually leads to the most snappy interactions.

Under the hood, the <Link> component uses the useNavigate() API and prevents the default behavior of the native <a>:

```
import { component$ } from '@builder.io/qwik';
import { useNavigate } from '@builder.io/qwik-city';
 
export const Link = component$<LinkProps>((props) => {
  const nav = useNavigate();
 
  return (
    <a
      preventdefault:click
      onClick$={() => {
        nav(props.href);
      }}
      {...props}
    >
      <Slot />
    </a>
  );
});
```

### Usage

```
import { component$ } from '@builder.io/qwik';
import { Link } from '@builder.io/qwik-city';
 
export default component$(() => {
  return (
    <div>
      <a href="/docs" class="my-link">
        full-page reload
      </a>
      <Link href="/docs" class="my-link">
        spa navigation
      </Link>
    </div>
  );
});
```

### Prefetch

Whether Qwik should prefetch and cache the target page of this Link, this includes invoking any routeLoader$, onGet, etc.

This improves UX performance for client-side (SPA) navigations.

Prefetching occurs when a the Link enters the viewport in production (on:qvisible), or with mouseover/focus during dev.

Prefetching will not occur if the user has the data saver setting enabled.

Setting this value to "js" will prefetch only javascript bundles required to render this page on the client, false will disable prefetching altogether.

Warning: if you have a menu with many links, all of them will be loaded immediately when you enter the production page, which may result with too many requests

```
import { component$ } from '@builder.io/qwik';
import { Link } from '@builder.io/qwik-city';
 
export default component$(() => {
  return (
    <div>
      <Link href="/a" prefetch={false}>
        page will not be prefetched
      </Link>
      <Link href="/b" prefetch="js">
        page js will be prefetched
      </Link>
      <Link href="/c">
        page content & js will be prefetched
      </Link>
    </div>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
