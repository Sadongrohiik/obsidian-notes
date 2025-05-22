# https://tailwindcss.com/docs/dark-mode

[Original link](https://tailwindcss.com/docs/dark-mode)

## Overview

Now that dark mode is a first-class feature of many operating systems, it's becoming more and more common to design a dark version of your website to go along with the default design.

To make this as easy as possible, Tailwind includes adarkvariant that lets you style your site differently when dark mode is enabled:

Light mode

Writes upside-down

The Zero Gravity Pen can be used to write in any orientation,
        including upside-down. It even works in outer space.

Dark mode

Writes upside-down

The Zero Gravity Pen can be used to write in any orientation,
        including upside-down. It even works in outer space.

```
<div class="bg-white dark:bg-gray-800 rounded-lg px-6 py-8 ring shadow-xl ring-gray-900/5">  <div>    <span class="inline-flex items-center justify-center rounded-md bg-indigo-500 p-2 shadow-lg">      <svg class="h-6 w-6 stroke-white" ...>        <!-- ... -->      </svg>    </span>  </div>  <h3 class="text-gray-900 dark:text-white mt-5 text-base font-medium tracking-tight ">Writes upside-down</h3>  <p class="text-gray-500 dark:text-gray-400 mt-2 text-sm ">    The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.  </p></div>
```

By default this uses theprefers-color-schemeCSS media feature, but you can also build sites that supporttoggling dark mode manuallyby overriding the dark variant.

## Toggling dark mode manually

If you want your dark theme to be driven by a CSS selector instead of theprefers-color-schememedia query, override thedarkvariant to use your custom selector:

```
@import "tailwindcss";@custom-variant dark (&:where(.dark, .dark *));
```

Now instead ofdark:*utilities being applied based onprefers-color-scheme, they will be applied whenever thedarkclass is present earlier in the HTML tree:

```
<html class="dark">  <body>    <div class="bg-white dark:bg-black">      <!-- ... -->    </div>  </body></html>
```

How you add thedarkclass to thehtmlelement is up to you, but a common approach is to use a bit of JavaScript that updates theclassattribute and syncs that preference to somewhere likelocalStorage.

### Using a data attribute

To use a data attribute instead of a class to activate dark mode, just override thedarkvariant with an attribute selector instead:

```
@import "tailwindcss";@custom-variant dark (&:where([data-theme=dark], [data-theme=dark] *));
```

Now dark mode utilities will be applied whenever thedata-themeattribute is set todarksomewhere up the tree:

```
<html data-theme="dark">  <body>    <div class="bg-white dark:bg-black">      <!-- ... -->    </div>  </body></html>
```

### With system theme support

To build three-way theme toggles that support light mode, dark mode, and your system theme, use a custom dark mode selector and thewindow.matchMedia()APIto detect the system theme and update thehtmlelement when needed.

Here's a simple example of how you can support light mode, dark mode, as well as respecting the operating system preference:

```
// On page load or when changing themes, best to add inline in `head` to avoid FOUCdocument.documentElement.classList.toggle(  "dark",  localStorage.theme === "dark" ||    (!("theme" in localStorage) && window.matchMedia("(prefers-color-scheme: dark)").matches),);// Whenever the user explicitly chooses light modelocalStorage.theme = "light";// Whenever the user explicitly chooses dark modelocalStorage.theme = "dark";// Whenever the user explicitly chooses to respect the OS preferencelocalStorage.removeItem("theme");
```

Again you can manage this however you like, even storing the preference server-side in a database and rendering the class on the server — it's totally up to you.
