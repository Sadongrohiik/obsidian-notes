# https://qwik.dev/docs/integrations/icons/

[Original link](https://qwik.dev/docs/integrations/icons/)

# Icons

Icons are an important part of any application. There are already more than 180.000 icons you can add to your Qwik app.

## qwikest/icons

This package allows for a streamlined way to add icons to your Qwik app from a variety of icon sets.

Simply install the package with your package manager of choice:

```
pnpm install @qwikest/icons
```

```
npm install @qwikest/icons
```

```
yarn add @qwikest/icons
```

```
bun install @qwikest/icons
```

### Usage

```
import { LuRocket } from "@qwikest/icons/lucide";
 
export const MyComponent = component$(() => {
  // Icon size and color are inherited by default ⬇️
  return (
    <div style={{ color: "red", fontSize: "40px" }}>
      <LuRocket />
    </div>
  );
});
```

Please refer to the official docs for more details.

## icones.js.org

icones.js.org is a collection of icon collections. More than 180.000 public domain icons are available, ready to be used in your Qwik app.

Icones is powered by iconify which allows to easy add icons from Material Design, Phosphor, Remix, Carbon, Bootstrap, Tabler, Feather, Fluent, IconPark, Octicons and many other icon sets. Twitter Emoji, Fluent Emoji, EmojiOne, Noto Emoji... to any Qwik app.

Click the Qwik button to copy the icon code to your clipboard, then paste it into your project.

```
import type { PropsOf } from '@builder.io/qwik'
 
export function OcticonAlertFill12(props: PropsOf<'svg'>, key: string) {
  return (
    <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 12 12" {...props} key={key}><path fill="#888888" d="M4.855.708c.5-.896 1.79-.896 2.29 0l4.675 8.351a1.312 1.312 0 0 1-1.146 1.954H1.33A1.313 1.313 0 0 1 .183 9.058ZM7 7V3H5v4Zm-1 3a1 1 0 1 0 0-2a1 1 0 0 0 0 2Z"></path></svg>
  )
}
export default OcticonAlertFill12
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
