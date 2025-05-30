# https://qwik.dev/docs/cookbook/portals/

[Original link](https://qwik.dev/docs/cookbook/portals/)

# Portals

In front-end development, sometimes we need to display a component (like a modal or tooltip) in a different place from where it was triggered. The issue is that the UI element needs to be rendered in a different part of the DOM tree, and the component that triggers the element needs to have a way to affect the location of rendering.

In other frameworks, this is often solved by a dedicated API such as createPortal(). However such APIs don't work well with server-side rendering and so an alternative approach is needed.

Luckily, there is native behavior that handles this for us, called the top layer. It is supported in all major browsers.

## Qwik UI

The Qwik UI team has done an awesome job of filling in the gaps, and allowing us to use this behavior in production across all browsers.

### Modals

We use modals when we do not want the user to interact with the rest of the page. The rest of the content is inert, or unable to be interacted with.

Qwik UI's modal component uses the dialog element's showModal method, which is well-supported in browsers and automatically handles placing UI outside of the HTML Document.

It also includes behavior such as focus and scroll locking, alert dialogs, automatic entry and exit animation support, and backdrop animations.

### Popovers

If the UI element can interact with the rest of the page, then it is not modal.

Some examples of non-modal components are:

MDN's popover API replaces the need for portals in non-modal components. Support is also in every major browser.

Qwik UI has taken it upon themselves by providing a polyfill with feature parity to the native spec. You can use the Popover API's behavior in production today with Qwik UI's Popover component.

In the case of components like a select or combobox, Qwik UI also provides the ability to opt-in to "floating" behavior. For example, when a listbox anchors to an input element. You can do so by adding floating={true} to your Popover component. This will execute a bit of extra javascript needed for floating behavior.

It is intentionally opt-in, at some point the CSS Anchor API will provide a native solution, and so there should be an easy migration path when that receives more general support.

Because these solutions are built on top of the native specs, that also means there's less javascript we need to prefetch, and therefore less work that needs to be done!

Both Qwik UI's popover and modal components can be used regardless of meta-framework or microfrontend, as long as there is support for Qwik.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
