#### Universal Selector
```css
* {
  color: white;
}
```

#### Type selectors
```html
<!-- index.html -->

<div>Hello, World!</div>
<div>Hello again!</div>
<p>Hi...</p>
<div>Okay, bye.</div>
```

```css
/* styles.css */

div {
  color: white;
}
```

#### Class selectors
```html
<!-- index.html -->

<div class="alert-text">Please agree to our terms of service.</div>
```

```css
/* styles.css */

.alert-text {
  color: red;
}
```

#### ID Selectors
```html
<!-- index.html -->

<div id="title">My Awesome 90's Page</div>
```

```css
/* styles.css */

#title {
  background-color: red;
}
```

#### Grouping Selectors
###### Before:
```css
.read {
  color: white;
  background-color: black;
  /* several unique declarations */
}

.unread {
  color: white;
  background-color: black;
  /* several unique declarations */
}
```

###### After:
```css
.read,
.unread {
  color: white;
  background-color: black;
}

.read {
  /* several unique declarations */
}

.unread {
  /* several unique declarations */
}
```

#### Chaining selectors
```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

```css
.subsection.header {
  color: red;
}
/*Only tags with subsection and header class will have this styling*/
```

This can also be used to chain a class and an ID, as shown below:

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection" id="preview">
    This is where a preview for a post might go.
  </p>
</div>
```

You can take the two elements above and combine them with the following:

```css
.subsection.header {
  color: red;
}

.subsection#preview {
  color: blue;
}
```

### Combinators
#### Descendant combinator
```html
<!-- index.html -->

<div class="ancestor">
  <!-- A -->
  <div class="contents">
    <!-- B -->
    <div class="contents"><!-- C --></div>
  </div>
</div>

<div class="contents"></div>
<!-- D -->
```

```css
/* styles.css */

.ancestor .contents {
  /* some declarations */
}
/*Any tag with class contents that is a child of a tag with class ancestor will have styling applied*/
```

In the above example, the first two elements with the `contents` class (B and C) would be selected, but that last element (D) wouldn’t be.

- `>` - the child combinator
- `+` - the adjacent sibling combinator
- `~` - the general sibling combinator

Examples
```html
<main class="parent">
  <div class="child group1">
    <div class="grand-child group1"></div>
  </div>
  <div class="child group2">
    <div class="grand-child group2"></div>
  </div>
  <div class="child group3">
    <div class="grand-child group3"></div>
  </div>
</main>
```

To select all children of parent div we could do below
```css
main div {
  /* Our cool CSS */
}
```

What if we want to specify only divs with class child or class grand-child, use `>` child combinator
```css
/* This rule will only select divs with a class of child */
main > div {
  /* Our cool CSS */
}

/* This rule will only select divs with a class of grand-child */
main > div > div {
  /* More cool CSS */
}
```

n order to select an element that is adjacent to our target, or on the same level of indentation, we can use the adjacent sibling combinator `+`
```css
/* This rule will only select the div with the class child group2 */
.group1 + div {
  /* Our cool CSS */
}

/* This rule will only select the div with the class child group3 */
.group1 + div + div {
  /* More cool CSS */
}
```

Finally, if we want to select all of an element’s siblings and not just the first one, we can use the general sibling combinator `~`.

```css
/* This rule will select all of .group1's siblings - in this case the 2nd and 3rd .child divs */
.group1 ~ div {
  /* Our cool CSS */
}
```


#### Dynamic and user action pseudo-classes
[`:focus`](https://css-tricks.com/almanac/selectors/f/focus/) applies to an element that is currently selected by the user either through selecting it with their cursor or using their keyboard.

[`:hover`](https://css-tricks.com/almanac/selectors/h/hover/) will affect anything under the user’s mouse pointer. It can be used to give extra oomph to buttons and links to highlight that they’re interactable, or to trigger a drop-down menu.

[`:active`](https://css-tricks.com/almanac/selectors/a/active/) applies to elements that are currently being clicked, and is especially useful for giving your user feedback that their action had an effect. This is a great one to give your buttons and other interactive elements more ‘tactile’ feedback.

Link example
```css
  /* This rule will apply to all links */
  a {
    text-decoration: underline;
  }

  /* This will apply to unvisited links */
  a:link {
    color: blue;
  }

  /* And you guessed it, this applies to all links the user has clicked on */
  a:visited {
    color: purple;
  }
```

#### Structural pseudo-classes

[`:root`](https://css-tricks.com/almanac/selectors/r/root/) is a special class that represents the very top level of your document - the one element that has no parents. Generally when working with the web, this is equivalent to the `html` element, but there are a [few subtle differences](https://stackoverflow.com/questions/15899615/whats-the-difference-between-css3s-root-pseudo-class-and-html).

`:root` is generally the place where you will place your ‘global’ CSS rules that you want available everywhere - such as your custom properties and CSS variables, or rules such as `box-sizing: border-box;`.

[`:first-child`](https://css-tricks.com/almanac/selectors/f/first-child/) and [`:last-child`](https://css-tricks.com/almanac/selectors/l/last-child/) will match elements that are the first or last sibling.

Similarly, [`:empty`](https://css-tricks.com/almanac/selectors/e/empty/) will match elements that have no children at all, and [`:only-child`](https://css-tricks.com/almanac/selectors/o/only-child/) will match elements that don’t have any siblings.

For a more dynamic approach we can use [`:nth-child`](https://css-tricks.com/almanac/selectors/n/nth-child/). This is a flexible pseudo-class with a few different uses.

```css
  .myList:nth-child(5) {/* Selects the 5th element with class myList */}

  .myList:nth-child(3n) { /* Selects every 3rd element with class myList */}

  .myList:nth-child(3n + 3) { /* Selects every 3rd element with class myList, beginning with the 3rd */}

  .myList:nth-child(even) {/* Selects every even element with class myList */}
```

#### Pseudo-elements

While pseudo-classes give us an alternative way to interact with our HTML elements based on their state or structure, pseudo-elements are more abstract. They allow us to affect parts of our HTML that aren’t elements at all. These special elements share the same specificity as regular elements (0, 0, 0, 1). There are a number of useful pseudo-elements that can be utilized in any number of creative ways.

[`::marker`](https://css-tricks.com/almanac/selectors/m/marker/) allows you to customize the styling of your `<li>` elements’ bullets or numbers.

[`::first-letter`](https://css-tricks.com/almanac/selectors/f/first-letter/) and [`::first-line`](https://css-tricks.com/almanac/selectors/f/first-line/) allow you to (you guessed it!) give special styling to the first letter or line of some text.

[`::selection`](https://css-tricks.com/almanac/selectors/s/selection/) allows you to change the highlighting when a user selects text on the page.

[`::before` and `::after`](https://css-tricks.com/almanac/selectors/a/after-and-before/) allow us to add extra elements onto the page with CSS, instead of HTML. Using it to decorate text in various ways is one common use case.

```html
<style>
  .emojify::before {
    content: '😎 🥸 🤓';
}

  .emojify::after {
    content: '🤓 🥸 😎';
}
</style>

<body>
  <div> Let's <span class="emojify">emojify</span>this span!</div>
</body>
```

#### Attribute selectors

The last tool we’re going to add to the box is attribute selectors. Recall that an attribute is simply anything in the opening tag of an HTML element - such as `src='picture.jpg'` or `href="www.theodinproject.com"`.

Since we write our own values for attributes, we need a slightly more flexible system to be able to target specific values.

Attribute selectors have the same specificity as classes and pseudo-classes (0, 0, 1, 0).

Let’s look at some examples for basic usage.

- `[attribute]` - This general selector will select anything where the given attribute exists. Its value doesn’t matter.
- `selector[attribute]` - Optionally we can combine our attribute selectors with other types of selectors, such as class or element selectors.
- `[attribute="value"]` - To get really specific, we can use `=` to match a specific attribute with a specific value.

```css
  [src] {
    /* This will target any element that has a src attribute. */
  }

  img[src] {
    /* This will only target img elements that have a src attribute. */
  }

  img[src="puppy.jpg"] {
    /* This will target img elements with a src attribute that is exactly "puppy.jpg" */
  }
```

Sometimes we need to be more general in how we access these attributes. For example, perhaps we’re only interested in `img` elements where the `src` attribute’s value ends in `.jpg`. For cases like this we have some attribute selectors that allow us to match a part of the attribute’s value. If you’ve ever come across [regular expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) before, these attributes use a similar syntax.

- `[attribute^="value"]` - `^=` Will match strings from the start.
- `[attribute$="value"]` - `$=` Will match strings from the end.
- `[attribute*="value"]` - `*=` The wildcard selector will match anywhere inside the string.

```css
[class^='aus'] {
  /* Classes are attributes too!
    This will target any class that begins with 'aus':
    class='austria'
    class='australia'
  */
}

[src$='.jpg'] {
  /* This will target any src attribute that ends in '.jpg':
  src='puppy.jpg'
  src='kitten.jpg'
  */
}

[for*='ill'] {
  /* This will target any for attribute that has 'ill' anywhere inside it:
  for="bill"
  for="jill"
  for="silly"
  for="ill"
  */
}
```