# https://qwik.dev/docs/integrations/storybook/

[Original link](https://qwik.dev/docs/integrations/storybook/)

# Storybook

Storybook is a frontend workshop for building UI components and pages in isolation. Thousands of teams use it for UI development, testing, and documentation. It's open source and free.

Since version 7.0, Storybook supports Vite natively, which means it has first-class support for Qwik too.

## Usage

You can add Storybook to your existing app, or library use:

```
pnpm run qwik add storybook
```

```
npm run qwik add storybook
```

```
yarn run qwik add storybook
```

```
bun run qwik add storybook
```

The previous command installs the necessary dependencies and adds an example component and stories

Now you can serve the Storybook dashboard:

```
pnpm run storybook
```

```
npm run storybook
```

```
yarn run storybook
```

```
bun run storybook
```

## Examples

### Simple component

The following demonstrates a simple story that uses a qwik component:

```
import { component$ } from "@builder.io/qwik";
 
export interface ButtonProps {
  label: string;
}
 
export const Button = component$<ButtonProps>(({label}) => {
  return (
    <button>
      {label}
    </button>
  );
});
```

```
import type { Meta, StoryObj } from "storybook-framework-qwik";
import {Button, type ButtonProps} from "./button";
 
const meta: Meta<ButtonProps>  = {
  component: Button,
};
 
export default meta;
type Story = StoryObj<ButtonProps>; 
 
export const Primary: Story = {
  args: {
    label: "Hello World", 
  }
};
```

### Component That Uses QwikCity

When using Qwikcity, you must pass a context to the story by using the <QwikCityMockProvider>:

```
import { component$ } from "@builder.io/qwik";
import { Link } from "@builder.io/qwik-city";
 
export const WithLink = component$(() => {
  return (
    <Link href="https://google.com">Google Link</Link>
  );
});
```

```
import type { Meta, StoryObj } from "storybook-framework-qwik";
import { QwikCityMockProvider } from "@builder.io/qwik-city";
 
import { WithLink } from "./with-link";
 
const meta: Meta = {
  component: WithLink,
};
 
type Story = StoryObj;
export default meta;
 
export const Primary: Story = {
  render: () =>
    <QwikCityMockProvider>
      <WithLink />
    </QwikCityMockProvider>
};
```

For more information please refer to the storybook documentation.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
