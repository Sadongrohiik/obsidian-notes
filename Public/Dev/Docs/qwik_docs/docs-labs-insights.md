# https://qwik.dev/docs/labs/insights/

[Original link](https://qwik.dev/docs/labs/insights/)

# 🧪 Insights

Stage: prototyping

Insights allow your application to collect real user usage information to optimize the creation of bundles. By observing real user behavior, the Qwik build system can then do a better job prefetching bundles for your application. There are two benefits of this:

## Architecture

The optimization consists of these parts:

NOTE:
To try this new feature please drop a message inside the Qwik Discord server
Currently Insights info is hosted in the Builder database. This information is about the execution of symbols/chunks in the application.
The implementation of the service is open-source and you have the choice to use ours or host your own.
(Please note, that this may become a paid service in the future.)

## <Insights> component

The <Insights> component should be added to your root.tsx file.

```
// ...
import { Insights } from '@builder.io/qwik-labs';
 
export default component$(() => {
  // ...
  return (
    <QwikCityProvider>
      <head>
        // ...
        <Insights
          publicApiKey={import.meta.env.PUBLIC_QWIK_INSIGHTS_KEY}
        />
      </head>
      <body lang="en">
        // ...
      </body>
    </QwikCityProvider>
  );
});
```

You can get PUBLIC_QWIK_INSIGHTS_KEY by visiting Qwik Insight.

The <Insights> component collects this data:

NOTE: The <Insights> component does not collect any user-identifiable information.

The information collected is sent to builder.io database for storage.

## Vite integration

Once the application is running for a while and it collects sufficient information on symbol usage, the stats can be used to improve the bundles of the future version of the application. This is done by connecting the vite build with Insights like so:

file: vite.config.js

```
//..
import { defineConfig, loadEnv } from 'vite';
import { qwikInsights } from '@builder.io/qwik-labs/vite';
 
export default defineConfig(async () => {
  return {
    plugins: [
      qwikInsights({
        publicApiKey: loadEnv('', '.', '').PUBLIC_QWIK_INSIGHTS_KEY,
      }),
      //...
    ],
    // ...
  };
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
