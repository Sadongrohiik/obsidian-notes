# https://qwik.dev/docs/integrations/authjs/

[Original link](https://qwik.dev/docs/integrations/authjs/)

# Auth.js

Auth.js is a well-known library for authentication used by various JS frameworks. With Auth.js, we benefit from reduced complexity. We also have access to a range of authentication providers, such as GitHub, Google, Facebook, among others. Moreover, it can be integrated into multiple frameworks including Qwik.

Auth.js offers several features that enhance simplicity, productivity, flexibility, and provider diversity. Here are the main features of Auth.js:

Be aware that the Auth.js library is still in a pre-1.0 stage and could have bugs.

## Installation

You can add Auth.js easily by using the following Qwik starter script:

```
pnpm run qwik add auth
```

```
npm run qwik add auth
```

```
yarn run qwik add auth
```

```
bun run qwik add auth
```

This command will add a new package:

and create a new file named [email protected] with an example configuration.

Note on Manual Deployments with Node

When deploying applications manually using Node.js, particularly with frameworks like Express, the server or Node process does not inherently know if it's being served under HTTP or HTTPS.
Unlike hosting services like Vercel, Netlify, or Cloudflare, where the ﻿ORIGIN configuration is automatically managed, manual setups require explicit specification. To ensure that your Node.js application recognizes the correct protocol and host it is being served under, set the following environment variables:

### Migrating from @builder.io/qwik-auth

When migrating from @builder.io/qwik-auth to @auth/qwik, there are a couple changes that need to be made.

The routes provided by the auth library are no longer prefixed with /api. If your are using previous guidance for protected routes or calling the auth routes directly, please be sure to update accordingly.

```
export const onRequest: RequestHandler = (event) => {
  const session: Session | null = event.sharedMap.get('session');
  if (!session || new Date(session.expires) < new Date()) {
-    throw event.redirect(302, `/api/auth/signin?redirectTo=${event.url.pathname}`);
+    throw event.redirect(302, `/auth/signin?callbackUrl=${event.url.pathname}`);
  }
};
```

The setup function and and methods exported by it have changed in [email protected]. Be sure to update the imports for the useAuthSession, useAuthSignin, and useAuthSignout methods anywhere you use them in your app.

```
import Auth0Provider from "@auth/core/providers/auth0";
-import { serverAuth$ } from "@builder.io/qwik-auth";
+import { QwikAuth$ } from "@auth/qwik";
 
-export const { onRequest, useAuthSession, useAuthSignin, useAuthSignout } =
-  serverAuth$(({ env }) => ({
+export const { onRequest, useSession, useSignIn, useSignOut } = 
+  QwikAuth$(({ env }) => ({
```

Update your vite.config.ts to include "@auth/qwik" to avoid potentials import issues

```
export default defineConfig(({ command, mode }): UserConfig => {
  return {
    plugins: [qwikCity(), qwikVite(), tsconfigPaths()],
    // This tells Vite which dependencies to pre-build in dev mode.
    optimizeDeps: {
      include: ["@auth/qwik"],
    },
```

## Qwik API

### useSession

A routeLoader$ that returns a session object or an empty object if there is no session. The contents of the session object that is returned are configurable with the session callback. Session data can also be retrieved using the session REST API.

```
import { component$ } from '@builder.io/qwik';
import { useSession } from '~/routes/plugin@auth';
 
export default component$(() => {
  const session = useSession();
  return <p>{session.value?.user?.email}</p>;
});
```

### useSignIn

A routeAction$ used to initiate a signin flow or send the user to the signin page listing all possible providers. The CSRF token is handled internally when signing in using useSignIn.

#### Parameters

NOTE: You can also set the authorizationParams through the provider.authorizationParams configuration

Example using useSignIn with the <Form> component and optional providerId and options.redirectTo:

```
import { component$ } from '@builder.io/qwik';
import { Form } from '@builder.io/qwik-city';
import { useSignIn } from '~/routes/plugin@auth';
 
export default component$(() => {
  const signIn = useSignIn();
  return (
    <Form action={signIn}>
      <input type="hidden" name="providerId" value="github" />
      <input type="hidden" name="options.redirectTo" value="http://qwik-auth-example.com/dashboard" />
      <button>Sign In</button>
    </Form>
  );
});
```

Example using useSignIn programmatically with optional providerId and options.redirectTo:

```
import { component$ } from '@builder.io/qwik';
import { useSignIn } from '~/routes/plugin@auth';
 
export default component$(() => {
  const signIn = useSignIn();
  return (
    <button onClick$={() => signIn.submit({ providerId: 'github', options: { redirectTo: 'http://qwik-auth-example.com/dashboard' } })}>Sign In</button>
  );
});
```

### useSignOut

A routeAction$ used to initiate a signout flow. The user session will be invalidated/removed from the cookie/database, depending on the flow you chose to store sessions.

#### Parameters

The 'redirectTo' must be considered valid by the redirect callback handler. By default, it requires the URL to be an absolute URL at the same host name, or you can also supply a relative URL starting with a slash. If it does not match it will redirect to the homepage. You can define your own redirect callback to allow other URLs.

Example using useSignOut with the <Form> component and optional redirectTo:

```
import { component$ } from '@builder.io/qwik';
import { Form } from '@builder.io/qwik-city';
import { useSignOut } from '~/routes/plugin@auth';
 
export default component$(() => {
  const signOut = useSignOut();
  return (
    <Form action={signOut}>
      <input type="hidden" name="redirectTo" value="/signedout" />
      <button>Sign Out</button>
    </Form>
  );
});
```

Example using useSignOut programmatically with optional redirectTo:

```
import { component$ } from '@builder.io/qwik';
import { useSignOut } from '~/routes/plugin@auth';
 
export default component$(() => {
  const signOut = useSignOut();
  return <button onClick$={() => signOut.submit({ redirectTo: '/signedout' })}>Sign Out</button>;
});
```

## REST API

All the same REST APIs as provided by Auth.js are available.

### signin

GET /auth/signin

Displays the built-in/unbranded sign-in page.

POST /auth/signin/:provider

Starts a provider-specific sign-in flow. In the case of an OAuth provider, calling this endpoint will initiate the Authorization Request to your Identity Provider.  This endpoint is also used by the useSignIn action internally.

### callback

GET/POST /auth/callback/:provider

### signout

GET /auth/signout

Displays the built-in/unbranded sign out page.

POST /auth/signout

Handles signing the user out - this is a POST submission to prevent malicious links from triggering signing a user out without their consent. The user session will be invalidated/removed from the cookie/database, depending on the flow you chose to store sessions. This endpoint is also used by the useSignOut method internally.

### session

GET /auth/session

Returns client-safe session object - or an empty object if there is no session. The contents of the session object that is returned are configurable with the session callback. Session data can also be retrieved using the useSession routerLoader.

### csrf

GET /auth/csrf

Returns object containing CSRF token. In NextAuth.js, CSRF protection is present on all authentication routes. It uses the "double submit cookie method", which uses a signed HttpOnly, host-only cookie. The CSRF token returned by this endpoint must be passed as form variable named csrfToken in all POST submissions to any API endpoint.

### providers

GET /auth/providers

Returns a list of configured OAuth services and details (e.g. sign in and callback URLs) for each service. It is useful to dynamically generate custom sign up pages and to check what callback URLs are configured for each OAuth provider that is configured.

## Examples

### GitHub

```
import { QwikAuth$ } from "@auth/qwik";
import GitHub from "@auth/qwik/providers/github";
 
export const { onRequest, useSession, useSignIn, useSignOut } = QwikAuth$(
  () => ({
    providers: [GitHub],
  }),
);
```

IMPORTANT: Make sure to keep the onRequest export as it is used to handle the OAuth flow redirects. Once the user finished OAuth flow, GitHub (or any other provider) will redirect the user back to the application to /auth/callback/github (or /auth/callback/[otherProvider]). The onRequest middleware function will handle requests to this endpoint and finish the OAuth flow.

```
AUTH_GITHUB_ID=
AUTH_GITHUB_SECRET=
AUTH_SECRET=
```

IMPORTANT: Please read the Qwik documentation about Environment Variables to ensure you are using them safely. Many provider secrets should be kept secure and not exposed to the client/browser.

### Credentials

Warning: This functionality is discourage by Auth.js.

https://next-auth.js.org/providers/credentials

```
import { QwikAuth$ } from "@auth/qwik";
import Credentials from "@auth/qwik/providers/credentials";
 
export const { onRequest, useSession, useSignIn, useSignOut } = QwikAuth$(
  () => ({
    providers: [
      Credentials({
        async authorize(credentials, req) {
          // Add logic here to look up the user from the credentials supplied
          const user = {
            id: 1,
            name: "Mike",
            email: "[email protected]",
          };
 
          return user;
        },
      }),
    ],
  }),
);
```

```
AUTH_SECRET=
```

IMPORTANT: Please read the Qwik documentation about Environment Variables to ensure you are using them safely. Many provider secrets should be kept secure and not exposed to the client/browser.

### Route Protection

Session data can be accessed via the route event.sharedMap.  So a route can be protected and redirect using something like this located in a layout.tsx or page index.tsx:

```
export const onRequest: RequestHandler = (event) => {
  const session: Session | null = event.sharedMap.get('session');
  if (!session || new Date(session.expires) < new Date()) {
    throw event.redirect(302, `/auth/signin?callbackUrl=${event.url.pathname}`);
  }
};
```

Note: If placed in a layout.tsx ensure that the redirect destination does not share the same layout.tsx or a redirection loop could occur.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
