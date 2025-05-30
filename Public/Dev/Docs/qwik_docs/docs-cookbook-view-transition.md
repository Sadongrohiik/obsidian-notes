# https://qwik.dev/docs/cookbook/view-transition/

[Original link](https://qwik.dev/docs/cookbook/view-transition/)

# View Transition API

By default Qwik will start a view transition when SPA navigation. We can run animation either with CSS or WAAPI.

## CSS

```
export default component$(({ list }) => {
  return (
    <ul>
      {list.map((item) => (
        // Create a name per item
        <li key={item.id} class="item" style={{viewTransitionName: `_${item.id}_`}}>...</li>
      ))}
    </ul>
  )
})
```

```
.item {
  /* Alias to target all .item with a view-transition-name */
  view-transition-class: animated-item;
}
/* Animate when item didn't exist in the previous page */
::view-transition-new(.animated-item):only-child {
  animation: fade-in 200ms;
}
/* Animate when item doesn't exist in the next page */
::view-transition-old(.animated-item):only-child {
  animation: fade-out 200ms;
}
```

Sometime we need to have some specific logic before the animation start. In this case you can listen to the qviewTransition event.

For example if you want to only animate visible element:

```
export default component$(() => {
  // In this case we need the callback to be sync, else the transition might have already happened
  useOnDocument('qviewTransition', sync$((event: CustomEvent<ViewTransition>) => {
    const transition = event.detail;
    const items = document.querySelectorAll('.item');
    for (const item of items) {
      if (!item.checkVisibility()) continue;
      item.dataset.hasViewTransition = true;
    }
  }))
  return (
    <ul>
      {list.map((item) => (
        // Create a name per item
        <li key={item.id} class="item" style={{viewTransitionName: `_${item.id}_`}}>...</li>
      ))}
    </ul>
  )
})
```

```
.item[data-has-view-transition="true"] {
  view-transition-class: animated-item;
}
::view-transition-new(.animated-item):only-child {
  animation: fade-in 200ms;
}
::view-transition-old(.animated-item):only-child {
  animation: fade-out 200ms;
}
```

Note: ViewTransition interface is available with Typescript >5.6.

## WAAPI

With Web Animation API you can get more precise, but for that we need to wait for the ::view-transition pseudo-element to exist in the DOM. To achieve that you can wait the transition.ready promise.

In this example we add some delay for each item :

```
export default component$(() => {
  // Remove default style on the pseudo-element.
  useStyles$(`
    li {
      view-transition-class: items;
    }
    ::view-transition-old(.items) {
      animation: none;
    }
  `);
  useOnDocument('qviewTransition', $(async (event: CustomEvent<ViewTransition>) => {
    // Get visible item's viewTransitionName (should happen before transition is ready)
    const items = document.querySelectorAll<HTMLElement>('.item');
    const names = Array.from(items)
      .filter((item) => item.checkVisibility())
      .map((item) => item.style.viewTransitionName);
 
    // Wait for ::view-transition pseudo-element to exist
    const transition = event.detail;
    await transition.ready; 
 
    // Animate each leaving item
    for (let i = 0; i < names.length; i++) {
      // Note: we animate the <html> element
      document.documentElement.animate({
        opacity: 0,
        transform: 'scale(0.9)'
      }, {
        // Target the pseudo-element inside the <html> element
        pseudoElement: `::view-transition-old(${names[i]})`,
        duration: 200,
        fill: "forwards",
        delay: i * 50, // Add delay for each pseudo-element
      })
    }
  }))
  return (
    <ul>
      {list.map((item) => (
        // Create a name per item
        <li key={item.id} class="item" style={{viewTransitionName: `_${item.id}_`}}>...</li>
      ))}
    </ul>
  )
})
```

Note: For it to work correctly, we need to remove the default view transition animation else it happens on top of the .animate(). I'm using view-transition-class which is only working with Chrome right now.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
