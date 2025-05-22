# https://qwik.dev/docs/advanced/request-handling/

[Original link](https://qwik.dev/docs/advanced/request-handling/)

# Request Handling

Each layout.ts and index.ts file inside the src/routes directory has the ability to access the current HTTP request, response, and URL. This allows you to retrieve and modify data, and even respond with custom content.

Qwik City implements a middleware system based on the hierarchy of the src/routes directory. The middleware system is used to handle HTTP requests and responses and is available to pages, layouts, and endpoints.

Each route can add HTTP request and response handlers, allowing developers to retrieve and modify data. The handlers can also be used by endpoints, which only respond with data rather than a page's HTML.

This feature enables you to handle any request event, have side effects on the request pipeline, just before you render the component and respond with custom content. It is available to pages, layouts and endpoint routes, but not on regular components.

## Request and Response Handlers

On pages, layouts, and endpoints, we can access request data by implementing request handler functions such as onGet, onPost, onPut, etc. These functions are executed according to the HTTP method used for this route.

Additionally, an onRequest function can be used to handle any request method, rather than a specific one, in the form of a middleware. For example, if both onGet and onRequest is provided, for a GET request, the onGet will be called. However, in this scenario, if a POST request method came in, then the onRequest handler would be called since an onPost was not provided.
The onRequest is available as a catch-all to any request methods that do not have a specific method.

```
import type { RequestHandler } from '@builder.io/qwik-city';
 
export const onGet: RequestHandler<ProductData> = async ({ params }) => {
  // put your DB access here (hard coding data for simplicity)
  return {
    skuId: params.skuId,
    price: 123.45,
    description: `Description for ${params.skuId}`,
  };
};
```

## Request Event

The request handler functions receive a RequestEvent argument which has the following properties:

### Cookie

```
interface Cookie {
  get: (key: string) => CookieValue | null;
  set: (key: string, value: string | number | Record<string, any>, options?: CookieOptions) => void;
  delete: (key: string) => void;
  has: (key: string) => boolean;
}
```

get
Takes a string with the cookie name and returns the CookieValue, if present and null if not.

```
interface CookieValue {
  value: string;
  json: <T = unknown>() => T;
  number: () => number;
}
```

A cookie value is a simple record with three fields:

getAll
Returns an object with all cookies, if any. This is sometimes required if the names of cookies are unknown and must be parsed through.

set
Takes a key and value and creates a header that will be appended to the response. Value can be a string | number | Record<string, any>

As a third argument, you can optionally provide a CookieOptions record for setting additional fields.

```
export interface CookieOptions {
  domain?: string;
  expires?: Date | string;
  httpOnly?: boolean;
  maxAge?: number | [number, 'seconds' | 'minutes' | 'hours' | 'days' | 'weeks'];
  path?: string;
  sameSite?: 'lax' | 'none' | 'strict';
  secure?: boolean;
}
```

For more information on these attributes and their values, please refer to the MDN article on the Set-Cookie header.

delete
Appends a header with the provided key to the cookie. The new header will have an expired date in the expires field, telling the browsers to remove it.

```
cookie.delete('my-cookie');
// equivalent to
cookie.set('my-cookie', 'deleted', new Date(0));
// or
cookie.set('my-cookie', '');
```

Optionally, you can set the path, sameSite and/or domain when deleting the cookie. If your cookie was created with a path/domain, you must set these fields for the deletion to take effect.

```
cookie.delete('my-cookie', { domain: 'https://qwik.dev', path: '/docs/' });
```

has
A convenience method which returns true or false based on the presence of the provided key in cookie.

```
cookie.has('my-cookie');
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
