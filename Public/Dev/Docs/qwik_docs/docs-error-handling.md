# https://qwik.dev/docs/error-handling/

[Original link](https://qwik.dev/docs/error-handling/)

# Error handling

When an error is thrown in a loader or server$ function, a 500 error is returned to the client along with the error. This is useful during development but isn't always desirable for production systems. Qwik provides the tools necessary to customise how errors are handled.

Throwing a ServerError instance allows you to return custom errors to the browser with a different status code and serialised data.

Loaders also provide a helper function on the event object to easily create new ServerErrors.

```
// Throw ServerErrors from a routerLoader$
const useProduct = routeLoader$(async (ev) => {
  const product = await fetch('api/product/1')
 
  if (!product) {
    // Throw a 404 with a custom payload
    throw new ServerError(404, 'Product not found')
 
    // Or use the existing helper function
    throw ev.error(404, 'Product not found')
  }
 
  return product
})
 
// Throw ServerErrors from a server$
const getPrices = server$(() => {
  if (!isAuthenticated()) {
    throw new ServerError(401, { code: 401 })
  }
 
  return fetch('api/product/1/prices')
})
 
export default component$(() => {
  const product = useProduct()
 
  useVisibleTask(() => {
    getPrices()
      .then()
      .catch(err => {
        // The payload from a ServerError is deserialised as the error caught in the client
        if (err.code === 401) {
          // Navigate to login page
        }
 
        // Show generic error
      })
  })
 
  return <div>Product page</div>
})
```

## Error interceptor

Intercepting errors with middleware has a few usecases: you might want to hide error details in production systems, add structured error logging, or map the error status codes from RPC API calls to HTTP status codes. This is all achieveable with middleware in a plugin file.

```
// src/routes/[email protected]
import { type RequestHandler } from '@builder.io/qwik-city'
import { RedirectMessage } from '@builder.io/qwik-city/middleware/request-handler'
import { isDev } from '@builder.io/qwik/build'
 
export const onRequest: RequestHandler = async ({ next }) => {
  try {
    return await next();
  } catch (err) {
    // Pass through 3xx redirects
    if (isRedirectMessage(err)) {
      throw err
    }
 
    // Pass through ServerErrors
    if (isServerError(err)) {
      throw err
    }
 
    // Log unknown errors
    console.error('unknown error', err)
 
    if (isDev) {
      throw err
    } else {
      throw new ServerError(500, 'Internal server error');
    }
  }
};
 
function isServerError(err: unknown): err is ServerError {
  return (
    err instanceof ServerError ||
    // This is required for dev environments due to an issue with vite: https://github.com/vitejs/vite/issues/3910
    (isDev && err instanceof Error && err.constructor.name === "ServerError")
  );
}
 
function isRedirectMessage(err: unknown): err is RedirectMessage {
  return (
    err instanceof RedirectMessage ||
    // This is required for dev environments due to an issue with vite: https://github.com/vitejs/vite/issues/3910
    (isDev && err instanceof Error && err.constructor.name === "RedirectMessage")
  );
}
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
