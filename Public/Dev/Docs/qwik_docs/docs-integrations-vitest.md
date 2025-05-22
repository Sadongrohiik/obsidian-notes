# https://qwik.dev/docs/integrations/vitest/

[Original link](https://qwik.dev/docs/integrations/vitest/)

# Vitest

Vitest is a blazing-fast unit test framework powered by Vite. Because Qwik City uses Vite by default, Vitest is our defacto unit test framework.

## Usage

You can add vitest easily by using the following Qwik starter script:

```
pnpm run qwik add vitest
```

```
npm run qwik add vitest
```

```
yarn run qwik add vitest
```

```
bun run qwik add vitest
```

After running the command, vitest will be installed and a new component will be added to your project. The component will be added to the src/components/example directory as well as a new unit test named example.spec.tsx.
If you are looking for an example for a Component with QwikCity checkout QwikCityMockProvider.

```
import { createDOM } from '@builder.io/qwik/testing';
import { test, expect } from 'vitest';
import { ExampleTest } from './example';
 
test(`[ExampleTest Component]: Should render ⭐`, async () => {
  const { screen, render } = await createDOM();
  await render(<ExampleTest flag={true} />);
  expect(screen.outerHTML).toContain('⭐');
  const div = screen.querySelector('.icon') as HTMLElement;
  expect(div.outerHTML).toContain('⭐');
});
 
test(`[ExampleTest Component]: Should render 💣`, async () => {
  const { screen, render } = await createDOM();
  await render(<ExampleTest flag={false} />);
  expect(screen.outerHTML).toContain('💣');
});
 
test(`[ExampleTest Component]: Click counter +1`, async () => {
  const { screen, render, userEvent } = await createDOM();
  await render(<ExampleTest flag={true} />);
 
  expect(screen.outerHTML).toContain('Count:0');
 
  const spanBefore = screen.querySelector('span') as HTMLDivElement;
  await userEvent('.btn-counter', 'click');
  expect(spanBefore.innerHTML).toEqual('Count:1');
 
  const spanAfter = screen.querySelector('span') as HTMLDivElement;
  await userEvent('button', 'click');
  expect(spanAfter.innerHTML).toEqual('Count:2');
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
