`font-family` is used to assign fonts, specific font families will be referred to as `"Hack Nerd Font"` and generic families will be referred to as `serif`. A browser will iterate through all available fonts in order until one is found that is supported. It is recommended to have a generic font family at the end to fall back on. 
```css
font-family: "Hack Nerd Font", "Times New Roman", serif
```

`font-size` is the size of the font.
```css
font-size: 22px
```

`font-weight` affects the boldness of the text, the value can be a keyword or a number between 1 and 1000.
```css
font-weight: bold,
font-weight: 640
```

`text-align` will align the text horizontally with an element.
```css
text-align: center
```

neutral font declaration:
```css
body {
  font-family: system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
```

web font declaration
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
```

`@import` declaration
```css
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
```

Either method will import it to project for use in css:
```css
body {
  font-family: 'Roboto', sans-serif;
}
```

#### Importing own font:
```css
@font-face {
  font-family: my-cool-font;
  src: url(../fonts/the-font-file.woff);
}

h1 {
  font-family: my-cool-font, sans-serif;
}
```


#### font-style
```css
h1 {
  font-style: italic;
}
```

#### letter-spacing
```css
h1 {
  font-family: 'COUTUREBold';
  margin: 0;
  font-size: 38px;
}

.wide {
  font-size: 24px;
  letter-spacing: .5em;
}

.narrow {
  font-size: 48px;
  letter-spacing: -.15em;
}
```

#### line-height
```css
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  display: flex;
}

p.line-height {
  line-height: 1.5;
}
```

#### text-transform
Text transform simply changes the case of the given text. You can use this, for example, to force your heading tags to be all uppercase, or to capitalize every word.

Usage is simple, and can be seen in the clear example on these [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/CSS/text-transform).

#### text-shadow
As you might expect, `text-shadow` adds a shadow around the text in the selected element. This one is best used sparingly, but can be used to great effect in headings or other presentational text.

The examples on the [MDN reference page for text-shadow](https://developer.mozilla.org/en-US/docs/Web/CSS/text-shadow) show how to use it.

#### ellipsis
```css
.overflowing {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```
This one isn’t a single property, but it’s a useful trick to keep in your toolbox. With the `text-overflow` property, you can truncate overflowing text with an ellipsis. Making an overflow happen, however, requires the use of a couple other properties because the default behavior of text simply printing outside its container isn’t technically considered an `overflow` (that’s confusing, we know. Sorry.)

You can see more detail and an example in [this CSS Tricks Article](https://css-tricks.com/snippets/css/truncate-string-with-ellipsis/). (Be ready to go look that article up every time you want to use this.)

