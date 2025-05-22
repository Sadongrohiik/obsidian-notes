# https://qwik.dev/docs/cookbook/nav-link/

[Original link](https://qwik.dev/docs/cookbook/nav-link/)

# NavLink Component

If you want to add active state to your links you can use this solution.
The NavLink component enhances Qwik <Link> component by adding:

This allows styling the active state for navigation.

## How it Works

Under the hood, NavLink uses the useLocation hook to get navigation status.
It checks if the link href matches the current URL pathname to set activeClass.
This allows NavLink to know the active state automatically based on navigation.

```
import { Slot, component$ } from '@builder.io/qwik';
import { Link, useLocation, type LinkProps } from '@builder.io/qwik-city';
 
type NavLinkProps = LinkProps & { activeClass?: string };
 
export const NavLink = component$(
  ({ activeClass, ...props }: NavLinkProps) => {
    const location = useLocation();
    const toPathname = props.href ?? '';
    const locationPathname = location.url.pathname;
 
    const startSlashPosition =
      toPathname !== '/' && toPathname.startsWith('/')
        ? toPathname.length - 1
        : toPathname.length;
    const endSlashPosition =
      toPathname !== '/' && toPathname.endsWith('/')
        ? toPathname.length - 1
        : toPathname.length;
    const isActive =
      locationPathname === toPathname ||
      (locationPathname.endsWith(toPathname) &&
        (locationPathname.charAt(endSlashPosition) === '/' ||
          locationPathname.charAt(startSlashPosition) === '/'));
 
    return (
      <Link
        {...props}
        class={[props.class, isActive && activeClass ? activeClass : ""]}
        
      >
        <Slot />
      </Link>
    );
  }
);
```

## Usage

You can use NavLink with the addition of activeClass props:

```
import { component$ } from '@builder.io/qwik';
import { NavLink } from '..';
 
export default component$(() => {
  return (
    <>
      Links
      <div>
        <NavLink href="/docs" activeClass="text-green-600">
          /docs
        </NavLink>
      </div>
      <div>
        <NavLink
          href="/demo/cookbook/nav-link/example/"
          activeClass="text-green-600"
        >
          /demo/cookbook/nav-link/example/
        </NavLink>
      </div>
    </>
  );
});
```

## Tailwind

If you are using Tailwind CSS make sure to edit your tailwind config file, and add important=true to your export, then add ! before the CSS classes you're using activeClass="!text-green-600" to make them important when the link is active.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
