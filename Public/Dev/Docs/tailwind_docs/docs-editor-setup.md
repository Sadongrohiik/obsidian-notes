# https://tailwindcss.com/docs/editor-setup

[Original link](https://tailwindcss.com/docs/editor-setup)

## Syntax support

Tailwind CSS uses custom CSS syntax like@theme,@variant, and@source, and in some editors this can trigger warnings or errors where these rules aren't recognized.

If you're using VS Code, our officialTailwind CSS IntelliSenseplugin includes a dedicated Tailwind CSS language mode that has support for all of the custom at-rules and functions Tailwind uses.

In some cases, you may need to disable native CSS linting/validations if your editor is very strict about the syntax it expects in your CSS files.

## IntelliSense for VS Code

The officialTailwind CSS IntelliSenseextension for Visual Studio Code enhances the Tailwind development experience by providing users with advanced features such as autocomplete, syntax highlighting, and linting.

Check out the projecton GitHubto learn more, oradd it to Visual Studio Codeto get started now.

## Class sorting with Prettier

We maintain an officialPrettier pluginfor Tailwind CSS that automatically sorts your classes following ourrecommended class order.

It works seamlessly with custom Tailwind configurations, and because it’s just a Prettier plugin, it works anywhere Prettier works—including every popular editor and IDE, and of course on the command line.

```
<!-- Before --><button class="text-white px-4 sm:px-8 py-2 sm:py-3 bg-sky-700 hover:bg-sky-800">Submit</button><!-- After --><button class="bg-sky-700 px-4 py-2 text-white hover:bg-sky-800 sm:px-8 sm:py-3">Submit</button>
```

Check out the pluginon GitHubto learn more and get started.

## JetBrains IDEs

JetBrains IDEs like WebStorm, PhpStorm, and others include support for intelligent Tailwind CSS completions in your HTML.

Learn more about Tailwind CSS support in JetBrains IDEs →
