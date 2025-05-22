# https://qwik.dev/docs/advanced/plugins/

[Original link](https://qwik.dev/docs/advanced/plugins/)

# Qwik Plugins

Qwik plugins, named as plugin.ts or plugin@<name>.ts, handle incoming requests prior to root layout execution and are located in the src/routes directory. Request handlers like onRequest, onGet, onPost in these plugins are called before server$ functions. For multiple plugins, plugin.ts handlers execute first, followed by plugin@<name>.ts handlers in alphabetical order. Middleware functions should be defined in plugin.ts to ensure execution for all requests.

### The order of execution of plugin.ts files

If plugin.ts file exists and if it has exported request handlers, then they are executed first.

Then exported request handlers from plugin@<name>.ts files are executed in alphabetical order of the file names. For example, onGet from [email protected] is executed before onGet from [email protected] because auth is alphabetically before security.

Finally, if a server$ function exists, it's executed last.

## Middleware and server$

When using server$, it's important to understand how middleware functions are executed. Middleware functions defined in layout files do not run for server$ requests. This can lead to confusion, especially when developers expect certain middleware to be executed for both page requests and server$ requests.

To ensure that a middleware function runs for both types of requests, it should be defined in the plugin.ts file. This ensures that the middleware is executed consistently for all incoming requests, regardless of whether they are normal page requests or server$ requests.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
