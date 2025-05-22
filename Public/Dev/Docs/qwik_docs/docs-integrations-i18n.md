# https://qwik.dev/docs/integrations/i18n/

[Original link](https://qwik.dev/docs/integrations/i18n/)

# Internationalization

Internationalization is a complex problem. Qwik does not solve the internationalization problem directly instead it only provides low-level APIs to allow other libraries to solve it.

## Runtime vs compile time translation

At a high level there are two ways in which the translation problem can be solved:

Both of the above approaches have trade-offs that one should take into consideration.

The advantages of runtime approaches are:

Disadvantages of the runtime approach are:

The advantages of compile-time approaches are:

Disadvantages of compile time approaches are:

## Recommendation

With the above in mind, Qwik recommends that you use a tool that best fits your constraints. To help you make a decision there are three different considerations: Browser, Server, and Development.

### Browser

Qwik's goal is to deliver the best possible user experience. It achieves this by deferring the loading of code to later so that the initial startup performance is not overwhelmed. Because the runtime approach requires eager loading of all translations, we don't recommend this approach. We think that the compile-time approach is best for the browser.

### Server

The server does not have the constraint of lazy loading. For this reason, the server can use either the runtime or compiled approach. The disadvantage of compile time approach on the server is that we need to have a separate deployment for each translation. This complicates the deployment process as well as puts greater demand on the number of servers. For this reason, we think the runtime approach is preferable on the server.

### Development

During development, fewer build steps will result in a faster turnaround. For this reason, runtime translation should result in a simpler development workflow.

### Our Recommendation

Our recommendation is to use a tool that would provide a runtime approach on the server, and runtime or compile time on the client depending on whether we are in development or production. This way it is possible to prove the best user experience and development experience, and use the least server resources.

## Internationalization Libraries

### $localize

$localize the translation system is based on the $localize system from Angular. The translations can be extracted in xmb, xlf, xlif, xliff, xlf2, xlif2, xliff2, and json formats.

NOTE: The $localize system is a compile-time translation system and is completely removed from the final output. $localize is a sub-project of Angular, and including its usage does not mean that Angular is used for rendering of applications.

The easiest way to add $localize to Qwik is using the Qwik CLI command. This will install the required dependencies and create a new public route /src/routes/[locale] showcasing i18n $localize integration.

```
pnpm run qwik add localize
```

```
npm run qwik add localize
```

```
yarn run qwik add localize
```

```
bun run qwik add localize
```

For further reference, please check this example repo.

#### Extract translations

When you are done with your changes, you can use the i18n-extract command to extract the translations from the code.
This will update the file you see in package.json.

```
pnpm run i18n-extract
```

```
npm run i18n-extract
```

```
yarn run i18n-extract
```

```
bun run i18n-extract
```

#### Auto translations for $localize with deepl

For auto translations, you can use the deepl-localize package. It will automatically translate your strings using the deepl.com API.

Use the deepl-localize command to translate your strings with:

```
pnpm dlx deepl-localize translate -b src/locales/message.en.json -l de-DE fr-FR -a "YOUR-DEEPL-API-KEY"
```

```
npx deepl-localize translate -b src/locales/message.en.json -l de-DE fr-FR -a "YOUR-DEEPL-API-KEY"
```

```
yarn dlx deepl-localize translate -b src/locales/message.en.json -l de-DE fr-FR -a "YOUR-DEEPL-API-KEY"
```

```
bunx deepl-localize translate -b src/locales/message.en.json -l de-DE fr-FR -a "YOUR-DEEPL-API-KEY"
```

Alternatively, you can use the deepl-localize command to translate your strings within your script section:

```
{
  "scripts":{
    "translate":"deepl-localize translate -b src/locales/message.en.json -l de-DE fr-FR -a 'your-deepl-api-key'"
  }
}
```

### compiled-i18n

compiled-i18n is inspired by the $localize system from Angular. It only requires a plugin to be added to the Vite configuration.

It supports both runtime and compile-time translations.

See the Qwik-specific instructions.

Automatic translation is supported via deepl-localize.

### qwik-speak

qwik-speak library to translate texts, dates and numbers in Qwik apps.

The easiest way to add qwik-speak to Qwik is following the official guide.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
