# https://qwik.dev/docs/endpoints/

[Original link](https://qwik.dev/docs/endpoints/)

# Endpoints

A middleware function that returns a response is called an endpoint. Endpoints are useful for returning data such as  RESTful API, GraphQL API, JSON, XML, reverse proxy or any other type of API where you need to control all aspects of the HTTP response. Returning a response (using json for example) will stop the execution of subsequent middleware functions past this point in the middleware chain.

All endpoints receive a RequestEvent API for controlling the response of the endpoint.

For example, when navigating to /greet/ URL this endpoint will return {"hello":"world"}.

File: src/routes/greet/index.tsx

```
import { type RequestHandler } from '@builder.io/qwik-city';
 
export const onGet: RequestHandler = async ({ json }) => {
  json(200, { hello: 'world' });
};
```

Sending a response is what differentiates an endpoint from a middleware. Sending a response (using json() for example) will therefore implicitly halt the middleware chain.

## Create a reverse proxy using a fetch

A reverse proxy can be created by using the fetch() method to request another server. Then use the send() method to send the response back to the client.

```
import type { RequestHandler } from '@builder.io/qwik-city';
 
export const onGet: RequestHandler = async ({ send, url }) => {
  const response = await fetch(
    new URL('/demo/qwikcity/middleware/json/', url)
  );
  send(response.status, await response.text());
};
```

## Create a stream response manually

Endpoints can manually write to the HTTP response stream, using the getWritableStream() method. This can be useful for creating a streaming endpoint, such as a server-sent events endpoint.

```
import type { RequestHandler } from '@builder.io/qwik-city';
 
export const onGet: RequestHandler = async (requestEvent) => {
  const writableStream = requestEvent.getWritableStream();
  const writer = writableStream.getWriter();
  const encoder = new TextEncoder();
 
  writer.write(encoder.encode('Hello World\n'));
  await wait(100);
  writer.write(encoder.encode('After 100ms\n'));
  await wait(100);
  writer.write(encoder.encode('After 200ms\n'));
  await wait(100);
  writer.write(encoder.encode('END'));
  writer.close();
};
 
const wait = (ms: number) => new Promise((resolve) => setTimeout(resolve, ms));
```

## Endpoint vs server$

Endpoints are low level APIs that give developers full control over the HTTP response. They are only recommended when you need to create an API to be consumed by an external entity such as a mobile app or a third-party service.

The server$ functions are usually a better option when you need to run some code on the server and return a response back to the app. The server$ is strongly typed and provides a more convenient API for returning data.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
