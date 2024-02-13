[mdn web docs css](https://developer.mozilla.org/en-US/docs/Web/CSS) → Reference → Functions → *
or looks at this list of [value functions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Functions)

Examples:
`calc()`, allows mixing units and calculating units e.g.
```css
:root {
	--header: 3rem;
	--footer: 40px;
	--main: calc(100vh - calc(var(--header) + var(--footer)));
}

body {
	margin: 0;
	padding: 0;
	border: 0px solid transparent;
	background: #7a7a7a;
}

#container {
	border: 0px solid transparent;
	height: 100vh;
	color: white;
}
#container > * {
	display: flex;
	justify-content: center;
	align-items: center;
}

#header {
	height: var(--header);
	background: #111111;
}
#mainContent {
	height: var(--main);
	background: #343434;
	margin-right: auto;
	margin-left: auto;
}
#footer {
	height: var(--footer);
	background: #232323;
}
```

`min()` is good for responsiveness getting the minimum size between two parameters e.g.
```css
.image {
	width: min(150px, 100%);
	height: min(150px, 100%);
}
```
Meaning the dimensions will be 150px x150px until the window size is lesser and then it will shrink

![[min-demo.mp4]]

`max()` will work in the same way as `min()` except in reverse, selecting the largest e.g.
```css
width: max(100px, 4em, 50%);
```
from this list, as long as `4em` or `50% `result in lengths longer than `100px`, `max()` will select the biggest of them, however if they are small than `100px` will be set, `max()` is more commonly used as a *minimum size*. For example, scaling text size with window size, however setting a *minimum* of `16px` with something like `font-size: max(16px, 12%)`

![[max-demo.mp4]]

`clamp()` is like combining `min()` and `max()` for sizing as well as providing an ideal size e.g:
```css
h1 {
  font-size: clamp(320px, 80vw, 60rem);
}
```
1. the smallest value (320px)
2. the ideal value (80vw)
3. the largest value (60rem)

![[clamp-demo.mp4]]

- `min(<value-list>)`: selects the smallest (most negative) value from a list of comma-separated expressions
- `max(<value-list>)`: selects the largest (most positive) value from a list of comma-separated expressions
- `clamp(<min>, <ideal>, <max>)`: clamps a value between an upper and lower bound, based on a set ideal value

