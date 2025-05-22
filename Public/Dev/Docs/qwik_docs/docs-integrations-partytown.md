# https://qwik.dev/docs/integrations/partytown/

[Original link](https://qwik.dev/docs/integrations/partytown/)

# Partytown

Third party scripts slow down your initial page load substantially by blocking the main thread.

Partytown is a tool that allows you to defer third party scripts like Google Analytics, Facebook Pixel, etc off the main thread by using a web worker.
For more information about this tool visit the Partytown docs.

## Usage

You can add Partytown easily by using the following Qwik starter script:

```
pnpm run qwik add partytown
```

```
npm run qwik add partytown
```

```
yarn run qwik add partytown
```

```
bun run qwik add partytown
```

The previous command updates your app and sets the correct configuration in vite.config.ts.

It also adds new files to your components folder.

```
import { QwikPartytown } from './components/partytown/partytown';
 
export default component$(() => {
  return (
    <QwikCityProvider>
      <head>
        <meta charSet="utf-8" />
        <QwikPartytown forward={['gtag','dataLayer.push']} />
        <script
          async
          type="text/partytown"
          src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXX"
        />
        <script
          type="text/partytown"
          dangerouslySetInnerHTML={`
            window.dataLayer = window.dataLayer || [];
            window.gtag = function() {
              dataLayer.push(arguments);
            }
            gtag('js', new Date());
            gtag('config', 'G-XXXXXX');
          `}
        />
      </head>
      <body lang="en"></body>
    </QwikCityProvider>
  );
});
```

## Advanced

To further configure Partytown with more options, please visit the Partytown Documentation

### Contributors

Thanks to all the contributors who have helped make this documentation better!
