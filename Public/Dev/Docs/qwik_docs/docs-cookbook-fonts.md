# https://qwik.dev/docs/cookbook/fonts/

[Original link](https://qwik.dev/docs/cookbook/fonts/)

# Fonts

A memorable typeface can be a great way to make your site stand out. However, it's important to be mindful of the performance implications of using custom fonts.

Unlike system fonts, that come pre-installed on a user's machine, custom fonts need to be downloaded.

## FOIT vs. FOUT

When a user visits a website, the browser will request the font files from the server. The browser will then use the font files to render the text on the page.

There are two main strategies:

Both methods have drawbacks. FOIT withholds text from the user, while FOUT can cause a disruptive visual experiences. Both cause CLS issues. As long as web fonts need to be downloaded, these issues persist.

### Font Display

Luckily, we can make use of the font-display property to control how the browser handles font loading. This allows us to strike a balance between the two strategies.

We suggest playing around with the different loading strategies, as well as how the font display timeline works.

The two most common values for the font-display property are swap and fallback.

## Google Fonts

Google Fonts is a popular open source library, offering over 1500 font families.

While they are easy to use, they involve downloading a CSS file and fonts from different domains, causing a noticeable delay and switch in font loading despite using swap.

Here's what happens:

To mitigate this, we can self host our fonts.

## Self Hosting

Rather than using a third-party provider like Google Fonts, we can self-host our fonts. This means we download the font files and serve them from our own domain.

Some benefits include:

### Fontsource

Self-hosting with fontsource is as easy as an npm install. It includes all of the google fonts, as well as other open source fonts, without the hassle of managing the files yourself.

They also have a Qwik City guide, on how to add fontsource to your project.

### Manual

Sometimes we want to self host a font that is not included in Google fonts, or fontsource.

If we have a ttf or otf file, we want to convert it to a woff or woff2 file. To do that, we can use Fontsquirrel's Webfont Generator Tool.

Next we need to create an @font-face rule in our CSS. We want to create a new rule for each font weight and style we want to use.

```
@font-face {
  font-display: swap;
  font-family: "Peace Sans";
  font-style: normal;
  font-weight: 400;
  src: url("../assets/fonts/peace-sans.woff2") format("woff2");
}
```

The above is an example of an @font-face rule for the font "Peace Sans" with a font weight of 400, with a relative URL to our font file. We can then use the font in our CSS like so:

```
body {
  font-family: 'Peace Sans', sans-serif;
}
```

#### Manually self-hosting Google Fonts

The Google Webfonts Helper is a tool that allows you to download the optimized google fonts.

Unfortunately, this does not include variable fonts. To get around this, you can use the Google Fonts API, and then download the optimized variable font file in Chrome's network tab.

### Reducing font size

If we are not using certain glyphs, we can reduce the font size by using the unicode-range property. Glyphhanger is a tool that allows us to grab a specific subset of a font.

A common scenario, would be using only the latin subset of a font. This can reduce our font file size.

## Fallback fonts

If you recall an earlier section, we mentioned that we can get CLS issues when our custom fonts load in.

Recently, there has been an effort of "font matching", or adjusting typography properties to reduce the CLS impact of custom fonts. Let's take a look at how we can do that.

### Fallback Font Generator

This tool generates a system fallback with special properties. Here's an over-exaggerated demo of how it works

You can use the size-adjust, ascent-override, and descent-override properties to adjust the system fallback font to match the custom font.

### Fontaine

Fontaine will automatically adjust the above properties to avoid CLS issues. They provide a vite plugin that you can add in your vite config.

## System Fonts

The most performant option is system fonts. This is because the user already has the font installed on their machine, and the browser can render the text immediately.

System fonts often are often called "font stacks", which are a collection of system fonts that are similar enough to each other. If the first font is not available, the browser can use the next one in the stack.

Tailwind CSS also provides utility classes for common system fonts. Modern Font Stacks is an example tool you can use to test out different font stacks, including a Tailwind CSS plugin from a community member.

## Font UX

### Do not use the ch unit for body max-width

It's recommended to have a max-width of 75ch or 75 characters so that the user does not have to move their head to read the text, as well as it's easier to follow.

However, if we are using a custom font, we should be mindful of the ch unit. This is because the ch unit is based on the width of the 0 character, which can vary between fonts.

This can cause some very peculiar layout shifts. We want to set a max-width using px or rem.

### Use rem with the font-size property.

Different units each have their own accessibility concerns. We want to use rem with the font-size property, as it is based on the root font size. Otherwise, the user's chosen font size will not be respected.

### Line height recommendations

The browser's default line height is not preferable for reading. With body fonts, we want to have a line height around 1.5. For headings, we want to have a line height around 1.2.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
