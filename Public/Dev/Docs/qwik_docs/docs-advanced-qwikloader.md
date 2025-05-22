# https://qwik.dev/docs/advanced/qwikloader/

[Original link](https://qwik.dev/docs/advanced/qwikloader/)

# Qwikloader

Qwik is designed for fine-grained lazy loading of your application. To achieve lazy-loading, Qwik requires a tiny piece of JavaScript to load at the beginning that knows how to download the rest of the application on an as-needed basis. We refer to that JavaScript as Qwikloader.

Qwikloader is:

How it is delivered:

Qwikloader's Purpose:

## How does it work

Below you can find simple HTML with Qwikloader and a button with associated behavior.

```
<html>
  <body q:base="/build/">
    <button on:click="./myHandler.js#clickHandler">push me</button>
    <script>
      /* Qwikloader */
    </script>
  </body>
</html>
```

## Events and the Qwikloader

The registration of the listener creates two problems in the context of SSR/SSG that Qwik needs to solve. (For context, remember that Qwik is resumable, that is, it can continue executing the application from where the server paused without being forced to download and execute code eagerly.)

Without the above information, Qwik would be forced to download the component template and execute it so that the listener location and closure can be recovered. This process is known as hydration, and Qwik explicitly tries to avoid hydration.

Qwik serializes the event listeners into the DOM in the form of QRLs. For example:

```
<div>
  <button on:click="./chunk-a.js#Counter_button_onClick[0]">0</button>
</div>
```

The critical thing to notice is that Qwik generated an on:click attribute, containing the value ./chunk-a.js#Counter_button_onClick[0]. In the above example the on:click attribute solves the listener location problem, and the attribute value solves the listener code problem. By serializing the listeners into the HTML Qwik applications do not need to perform hydration on startup.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
