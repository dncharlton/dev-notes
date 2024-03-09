Everything is boxes!!!!!!

#### Manipulating Boxes
- `padding` increases the space between the border of a box and the content of the box.
- `margin` increases the space between the borders of a box and the borders of adjacent boxes.
- `border` adds space (even if it’s only a pixel or two) between the margin and the padding.

![[padding-margin-border.png]]

`height` and `width` by default will set the size of the inner content, adding the padding and border on top of the set `height` and `width`. For example:

```css
.class {
  padding: 25px;
  border: 25px;
  width: 100px;
  height: 100px;
  margin: 100px;
}
```

This would result in a box with the dimensions `100+25+25+25+25` x `100+25+25+25+25` = `200` + `200`
Note: `width/height` + `border*2` + `padding*2` , margin is not includes as it exists *outside* the box.
You can override `width` and `height` to be the total box dimensions with:

```css
.class {
  padding: 25px;
  border: 25px;
  width: 100px;
  height: 100px;
  margin: 100px;
  box-sizing: border-box;
}
```

Resulting in the final dimensions being `100` x `100` and in this example the internal dimensions for content would be `0` x `0` Note: `100-25-25-25-25` x `100-25-25-25-25` > `width/height` - `border*2` - `padding*2`

#### Box Types:
###### Block
Elements such as `<p>` and `<div>` are by default block type elements that have `display: block` assigned as default. By default, each new block will start on a new line.
###### Inline
Elements such as `<span>` and `<a>`are by default inline type elements that have `display: inline` assigned as default. Inline elements do not start on a new line.
[w3school css block property](https://www.w3schools.com/cssref/pr_class_display.php)

