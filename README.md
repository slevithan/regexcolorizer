﻿# Regex Colorizer

Regex Colorizer is a lightweight library (5 KB min/gzip, no dependencies) for adding syntax highlighting to your regular expressions in blogs, docs, regex testers, and other tools. It supports the **JavaScript regex flavor** ([ES2022](https://github.com/slevithan/awesome-regex#javascript-regex-evolution)) with **web reality**. In other words, it highlights regexes as web browsers actually interpret them.

The API is simple. Just give the elements that contain your regexes (`pre`, `code`, or whatever) the class `regex`, and call `colorizeAll()`. See more usage examples below.

Errors are highlighted, along with some edge cases that can cause cross-browser grief. Hover over errors for a description of the problem.

## Demo

Try it out on the [**demo page**](https://slevithan.github.io/regexcolorizer/demo/), which also includes more details.

## Install and use

```sh
npm install regexcolorizer
```

```js
import {colorizeAll, colorizePattern, loadStyles} from 'regexcolorizer';
```

In browsers (using a global name):

```html
<script src="https://cdn.jsdelivr.net/npm/regexcolorizer@1.0.1/dist/regexcolorizer.min.js"></script>
<script>
  const {colorizeAll, colorizePattern, loadStyles} = RegexColorizer;
</script>
```

## Themes

Several themes are available as stylesheets, but you don't need to add a stylesheet to your page to use the default theme. Just run `loadStyles()`.

## Usage

```js
import {colorizeAll, colorizePattern, loadStyles} from 'regexcolorizer';
// Or, if using the browser bundle:
// const {colorizeAll, colorizePattern, loadStyles} = RegexColorizer;

// Don't run this line if you provide your own stylesheet
loadStyles();

// Highlight all elements with class `regex`
colorizeAll();

// Or provide a `querySelectorAll` value for elements to highlight
colorizeAll({
  selector: '.regex',
});

// Optionally provide flags
colorizeAll({
  // Flags provided in `data-flags` attributes will override this
  flags: 'u',
});

// You can also just get the highlighting HTML for a specific pattern
element.innerHTML = colorizePattern('(?<=\\d)', {
  flags: 'u',
});
```

In your HTML:

```html
<p>
  This regex is highlighted inline:
  <code class="regex">(?&lt;=\d)\p{L}\8</code>.

  And here's the same regex but with different rules from flag u:
  <code class="regex" data-flags="u">(?&lt;=\d)\p{L}\8</code>.
</p>
<!-- Can include any valid flags. Ex: data-flags="gimsuyd" -->
```
