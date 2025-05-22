# https://qwik.dev/docs/integrations/supabase/

[Original link](https://qwik.dev/docs/integrations/supabase/)

# Supabase

The Supabase JS library plays nicely with the server-side APIs from Qwik such as routeLoader$, routeAction$ or server$.

First, install supabase in your Qwik project:

```
pnpm install @supabase/supabase-js supabase-auth-helpers-qwik
```

```
npm install @supabase/supabase-js supabase-auth-helpers-qwik
```

```
yarn add @supabase/supabase-js supabase-auth-helpers-qwik
```

```
bun install @supabase/supabase-js supabase-auth-helpers-qwik
```

The second step would be to add the PUBLIC_SUPABASE_URL and PUBLIC_SUPABASE_ANON_KEY environment variables to .env file, the "anon" key is safe to be exposed in the client-side.

```
PUBLIC_SUPABASE_URL=https://xxxxxxx.supabase.co
PUBLIC_SUPABASE_ANON_KEY=eyJhb.......
```

You should be able to get these values from the Supabase dashboard, create a new .env.local file at the root of the project and paste them there.

Note: It's possible to use Supabase with Qwik completely client-side, however, you would lose some of the performance benefits that you can achieve with leveraging the server. For a working example and code head over to this repository.

## Server-side

The Supabase client can now be used server-side - in routeLoaders and routeActions - by calling the createServerClient function.

```
import { routeLoader$ } from '@builder.io/qwik-city';
import { createServerClient } from 'supabase-auth-helpers-qwik';
 
export const useDBTest = routeLoader$(async (requestEv) => {
  const supabaseClient = createServerClient(
    requestEv.env.get("PUBLIC_SUPABASE_URL")!,
    requestEv.env.get("PUBLIC_SUPABASE_ANON_KEY")!,
    requestEv
  );
  const { data } = await supabaseClient.from('test').select('*')
  return { data };
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
