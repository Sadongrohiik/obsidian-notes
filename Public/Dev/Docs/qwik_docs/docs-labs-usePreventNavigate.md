# https://qwik.dev/docs/labs/usePreventNavigate/

[Original link](https://qwik.dev/docs/labs/usePreventNavigate/)

This feature is EXPERIMENTAL. We invite you to try it out and provide feedback via the RFC issue.

To use it, you must add experimental: ['preventNavigate'] to your qwikVite plugin options.

# Preventing navigation

If the user can lose state by navigating away from the page, you can use usePreventNavigate(callback) to conditionally prevent the navigation.

The callback will be called with the URL that the user is trying to navigate to. If the callback returns true, the navigation will be prevented.

You can return a Promise, and qwik-city will wait until the promise resolves before navigating.

However, in some cases the browser will navigate without calling qwik-city, such as when the user reloads the tab or navigates using <a/> instead of <Link />. When this happens, the answer must be synchronous, and user interaction is not allowed.

You can tell the difference between qwik-city and browser navigation by looking at the provided URL. If the URL is undefined, the browser is navigating away, and you must respond synchronously.

Examples:

```
export default component$(() => {
  const okToNavigate = useSignal(true);
  usePreventNavigate$((url) => {
    if (!okToNavigate.value) {
      // we we didn't get a url, the browser is navigating away
      // and we must respond synchronously without dialogs
      if (!url) return true;
 
      // Here we assume that the confirmDialog function shows a modal and returns a promise for the result
      return confirmDialog(
        `Do you want to lose changes and go to ${url}?`
      ).then(answer => !answer);
      // or simply using the browser confirm dialog:
      // return !confirm(`Do you want to lose changes and go to ${url}?`);
    }
  });
 
  return (
    <div>
      <button onClick$={() => (okToNavigate.value = !okToNavigate.value)}>
        toggle user state
      </button>
      application content
    </div>
  );
});
```

```
export default component$(() => {
  const okToNavigate = useSignal(true);
  const navSig = useSignal<URL | number>();
  const showConfirm = useSignal(false);
  const nav = useNavigate();
  usePreventNavigate$((url) => {
    if (!okToNavigate.value) {
      if (url) {
        navSig.value = url;
        showConfirm.value = true;
      }
      return true;
    }
  });
 
  return (
    <div>
      <button onClick$={() => (okToNavigate.value = !okToNavigate.value)}>
        toggle user state
      </button>
      application content
      {showConfirm.value && (
        <div>
          <div>
            Do you want to lose changes and go to {String(navSig.value)}?
          </div>
          <button
            onClick$={() => {
              showConfirm.value = false;
              okToNavigate.value = true;
              nav(navSig.value!);
            }}
          >
            Yes
          </button>
          <button onClick$={() => (showConfirm.value = false)}>No</button>
        </div>
      )}
    </div>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
