# https://qwik.dev/docs/cookbook/combine-request-handlers/

[Original link](https://qwik.dev/docs/cookbook/combine-request-handlers/)

# Combine Request Handlers

## Problem

In a Qwik application we often have several request handlers to perform middleware functions.
In fact, according to the principle of single responsibility middleware functions are developed to perform only one task (e.g. to create a database connection).
With these premises, it can be complex to combine multiple request handlers while maintaining the order in which they are called.
For example, you have one request handler to connect to a database, and another to load the current user record, the latter depends on the former, so they must be called in order.

## Solution

If you want to chain multiple request handlers together you can use this utility function.

```
import type { RequestHandler } from '@builder.io/qwik-city';
 
/**
 * Combines multiple request handlers into a single request handler.
 *
 * The handlers will be called in order:
 *
 * 1. Handler1 before next()
 * 2. Handler2 before next()
 * 3. Handler3 before next()
 * 4. Next()
 * 5. Handler3 after next()
 * 6. Handler2 after next()
 * 7. Handler1 after next()
 *
 * @public
 */
 
export const combineRequestHandlers = (...handlers: RequestHandler[]): RequestHandler =>
  async (originalContext) => {
    let lastNext = originalContext.next;
    for (let i = handlers.length - 1; i >= 0; i--) {
      const currentHandler = handlers[i];
      const nextInChain = lastNext;
      lastNext = async () => {
        await currentHandler({ ...originalContext, next: nextInChain });
      };
    }
 
    await lastNext();
  };
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
