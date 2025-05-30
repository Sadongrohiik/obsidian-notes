# https://qwik.dev/docs/cookbook/theme-management/

[Original link](https://qwik.dev/docs/cookbook/theme-management/)

# Theme management

In modern website we have seen that it has the feature of dark and light theme that creates a good impact on the users. They can change the theme according to their preferences.

To achieve this we are also using tailwindcss for styling.

First we have to install tailwindcss in our website. To add tailwind in Qwik project is very simple. You have to just run this command in terminal.

```
pnpm run qwik add tailwind
```

```
npm run qwik add tailwind
```

```
yarn run qwik add tailwind
```

```
bun run qwik add tailwind
```

You have to enable the darkmode from your tailwind.config.js file. It should look like this.

```
module.exports = {
  content: ["./src/**/*.{js,ts,jsx,tsx,mdx}"],
  darkMode: "class",
  theme: {},
  plugins: [],
};
```

Then we have to add this code in the head tag of our root.tsx file.

```
<script
          dangerouslySetInnerHTML={`
        (function() {
          function setTheme(theme) {
            document.documentElement.className = theme;
            localStorage.setItem('theme', theme);
          }
          const theme = localStorage.getItem('theme');
 
          if (theme) {
            setTheme(theme);
          } else {
            if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
              setTheme('dark');}
              else {
                setTheme('light');}}
        })();
        window.addEventListener('load', function() {
          const themeSwitch = document.getElementById('hide-checkbox');
          themeSwitch.checked = localStorage.getItem('theme') === 'light'? true: false;
        }
        );
      `}
        ></script>
```

You can change the variable name "hide-checkbox" to any name that you want. It need to be same as we have in our html file.

Then in any component you can add your theme toggle code.

```
import { component$, useStylesScoped$ } from "@builder.io/qwik";
import styles from "./style.css?inline";
 
export const ThemeSwitch = component$(() => {
  useStylesScoped$(styles);
  return (
    <div class="flex items-center gap-3">
      <label class="switch">
        <input
          type="checkbox"
          id="hide-checkbox"
          onClick$={() => {
            const theme = document.documentElement.className;
            if (theme === "light") {
              document.documentElement.className = "dark";
              localStorage.setItem("theme", "dark");
            } else {
              document.documentElement.className = "light";
              localStorage.setItem("theme", "light");
            }
          }}
        />
        <span class="slider round"></span>
      </label>
    </div>
  );
});
```

For styling of theme switch.

```
.switch{
  position: relative;
  display: inline-block;
  width: 50px;
  height: 30px;
  background-color: red;
  border-radius: 100px;
  cursor: pointer;
}
 
.switch input{
  display: none;
}
 
.slider{
  width: 50px;
  height: 25px;
  border-radius: 25px;
  background-color: #ccc;
  position: relative;
  cursor: pointer;
  transition: all .3s linear;
}
 
.slider:before{
  content: "";
  position: absolute;
  width: 25px;
  height: 25px;
  background-size: cover;
  border-radius: 50%;
  background-color: #fff;
  top: 15px;
  left: 5px;
  bottom: 0;
  margin: auto;
  transition: all .3s linear;
}
 
input:checked + .slider{
  background-color: #2196F3;
}
 
input:checked + .slider:before{
  left: 22px;
}
```

Then run the code. You have the functionality of dark and light theme.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
