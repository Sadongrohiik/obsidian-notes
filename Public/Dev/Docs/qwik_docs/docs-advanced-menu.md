# https://qwik.dev/docs/advanced/menu/

[Original link](https://qwik.dev/docs/advanced/menu/)

# Menu

Menus allow you to describe the site navigation structure in a simple declarative way. Menus come in two steps:

## File Structure

First layout files as follows:

```
src/
└── routes/
    └── some/
        ├── menu.md
        ├── layout.tsx
        └── path/
            └── index.tsx  # https://example.com/some/path
```

Navigating to https://example.com/some/path activates:

## Declaring Menu Structure

Use menu.md to declare the menu structure.

```
# Docs
 
## Getting Started
 
- [Introduction](introduction/index.md)
 
## Components
 
- [Basics](/docs/(qwik)/components/basics/index.mdx)
```

## Retrieving Menu Structure

At runtime, any component can retrieve the menu with useContent() hook. The type returned is ContentMenu.

The example above will return:

```
{
  text: "Docs",
  items: [
    {
      text: "Getting Started",
      items: [
        {
          text: "Introduction",
          href: "/docs/introduction"
        }
      ],
    },
    {
      text: "Components",
      items: [
        {
          text: "Basics",
          href: "/docs/(qwik)/components/basics"
        }
      ],
    },
  ],
}
```

## Using ContentMenu in a layout

While useContent() can be invoked from any component that is part of the current route, it is typically used in a layout component (or a component used by layout) to render the menu. An example usage is shown here:

```
import { component$ } from '@builder.io/qwik';
import { useLocation, useContent } from '@builder.io/qwik-city';
export default component$(() => {
  const { menu } = useContent();
  const { url } = useLocation();
 
  return (
    <nav class="menu">
      {menu
        ? menu.items?.map((item, index) => (
            <div key={index}>
              <h5>{item.text}</h5>
              <ul>
                {item.items?.map((item, subIndex) => (
                  <li key={`item-${index}-${subIndex}`}>
                    <a
                      href={item.href}
                      class={{
                        'is-active': url.pathname === item.href,
                      }}
                    >
                      {item.text}
                    </a>
                  </li>
                ))}
              </ul>
            </div>
          ))
        : null}
    </nav>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
