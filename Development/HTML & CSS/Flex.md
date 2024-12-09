## [Flex Cheat Sheet](https://flexbox.malven.co/)
## [Complete guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)


`flex` is actually a shorthand for `flex-grow`, `flex-shrink` and `flex-basis`
`flex: 1` equates to: `flex-grow: 1`, `flex-shrink: 1`, `flex-basis: 0` or `flex: 1 0 0`

e.g.
```html
<div class="flex-container">
  <div class="one"></div>
  <div class="two"></div>
  <div class="three"></div>
</div>
```

```css
.one {
  width: 100px; height: 100px;
  flex-grow: 1;
  flex-shrink: 1;
}
.two {
  width: 100px; height: 100px;
  flex-grow: 2;
  flex-shrink: 2;
}
.three {
  width: 100px; height: 100px;
  flex-grow: 1;
  flex-shrink: 4:
}
```

The `flex-grow` factor will let a flex item grown `x` times faster than the others e.g. `flex-grow: 2` will grow *two time* faster than the other flex items. `flex-shrink` will let the flex item shrink 3 times faster than the other containers.
In this example when display goes past `300px` then the `two` div will grow two times faster,  however when the display gets lesser than 300px the `three` div will shrink four times faster div `one` and twice as fast as div `two`.

`flex-basis` sets the initial size of the flex item. e.g. in case of `flex: 1` `flex-basis` would be `0` as flex would actually be defined as `flex: 1 1 0`, which is different from `flex-basis: auto` which is the actual default.

[w3 flex](https://www.w3.org/TR/css-flexbox-1/#flex-common)
[mdn web docs](https://developer.mozilla.org/en-US/docs/Web/CSS/flex)

#### Flex direction
Flex direction can be set with `row` or `column` using `flex-direction` These are the two axes of flex axes.
In *most* circumstances. `row` will align items left to right and `column` will be top to bottom.

`flex-direction: column` will not work with `flex: 1 1 0` it will only work with `flex: 1 1 auto`
when `flex-basis` is `0` it will begin all their calculation at `0` as by empty divs have 0 height and as such will stack all flex items on top of each other.


