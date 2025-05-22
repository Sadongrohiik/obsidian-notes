# https://qwik.dev/docs/guides/env-variables/

[Original link](https://qwik.dev/docs/guides/env-variables/)

# Environment Variables

Environment variables are a way to store configuration values or sensitive data that should not be included directly in your application code. These variables are typically used for things like API keys, database connection strings, or other environment-specific settings.

## Types of Environment Variables

### Build-time

### Server-side

IMPORTANT! DO NOT use build-time environment variables, (ie. variables that start with PUBLIC_) to store any sensitive information, such as API keys, secrets, passwords, etc. These variables are accessible in the browser ONLY PUBLIC DATA.

```
# This will only be available when run on the server
API_KEY=secretApiKeyHere
# This will be available everywhere
PUBLIC_API_URL=https://api.example.com
```

## Default Environment Variables

QwikCity includes a few environment variables out of the box

The preferred method for accessing environment variables in QwikCity is via import.meta.env.* (client side) or through the Request object when run server side.

process.env is a Node.js only API, and should be avoided at all costs.

## Build-time variables

Build-time variables are powered by Vite. They are defined in .env files and are available in the browser and in the server-side code.

Notice that build-time variables should be considered as public, since they will be hardcoded in the browser build, which can be easily read by anyone.

Build-time variables are prefixed by default with PUBLIC_ and can be accessed with with import.meta.env.PUBLIC_*.

### Defining Variables

```
PUBLIC_API_URL=https://api.example.com
```

### Usage

```
import { component$ } from '@builder.io/qwik';
 
export default component$(() => {
  // `import.meta.env.PUBLIC_*` variables can be read anywhere, including browser
  return <div>PUBLIC_API_URL: {import.meta.env.PUBLIC_API_URL}</div>
})
```

import.meta.env.PUBLIC_* variables can be read anywhere, but do not put any sensitive information in them, since they will be visible to the client.

## Server-side Variables

Server-side variables are fundamentally runtime variables that are only available in the server-side code.

They are not known at build-time and are not available in the browser, so they can be considered as private.

During production, setting server-side variables is very platform specific. Most of the platforms allow you to set environment variables from their dashboard, or CLI. Please, refer to your platform (cloudflare, vercel, netlify) documentation for more information.

Special Considerations for Docker and Fastify:

```
version: '3.8'
services:
 your-service:
   image: your-image-name
   environment:
     - FOO=BAR
```

### Defining Variables

```
DB_PRIVATE_KEY=123456789
```

Make sure you never commit .env.local files to git.

### Usage Examples

Server-side variables can only be accessed in server-only APIs that expose the RequestEvent object, such as routeLoader$(), routeAction$(), server$() and endpoint handlers such as onGet, onPost, onRequest etc.

```
import {
  routeLoader$,
  routeAction$,
  server$,
  type RequestEvent,
} from '@builder.io/qwik-city';
 
export const onGet = (requestEvent: RequestEvent) => {
  console.log(requestEvent.env.get('DB_PRIVATE_KEY'));
};
 
export const onPost = (requestEvent: RequestEvent) => {
  console.log(requestEvent.env.get('DB_PRIVATE_KEY'));
};
 
export const useAction = routeAction$(async (_, requestEvent) => {
  console.log(requestEvent.env.get('DB_PRIVATE_KEY'));
});
 
export const useLoader = routeLoader$(async (requestEvent) => {
  console.log(requestEvent.env.get('DB_PRIVATE_KEY'));
});
 
export const serverFunction = server$(function () {
  // `this` is the `RequestEvent` object
  console.log(this.env.get('DB_PRIVATE_KEY'));
});
```

### Usage in serverfull architecture (Example:Express)

For accessing the .env variables in serverfull architecture you need to use singleton design pattern, initialize the db in a plugin, and access it with getDB wherever it is needed.

```
let _db!: AppDatabase;
 
export function getDB() {
  // eslint-disable-next-line
  if (!_db) {
    throw new Error('DB not set');
  }
  return _db;
}
 
export async function initializeDbIfNeeded(factory: () => Promise<AppDatabase>) {
  // eslint-disable-next-line
  if (!_db) {
    _db = await factory();
  }
}
```

```
export const onRequest: RequestHandler = async ({ env }) => {
  const url = env.get('PRIVATE_LIBSQL_DB_URL')!;
  const authToken = env.get('PRIVATE_LIBSQL_DB_API_TOKEN')!;
  await initializeDbIfNeeded(initLibSql(url, authToken));
};
```

### Managing Environment Variables Throughout the Application Lifecycle

In modern applications, environment variables play a crucial role in managing application settings and configurations across various environments without hardcoding sensitive data into the source code.

Qwik City adaptors use the following:

Note:
This is not a comprehensive guide on environment variables, nor does it cover all of the 3rd-Party hosting scenarios. It is meant to give insight that can be applied across various environments.

See this video for a detailed explanation:
https://youtu.be/NPf39RWc8LM

### Contributors

Thanks to all the contributors who have helped make this documentation better!
