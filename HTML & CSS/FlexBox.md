#### Flexibility of a flexbox

![[Pasted image 20240105163834.png]]
#### Summary:
- Use `display: flex;` to create a flex container.
- Use `justify-content` to define the horizontal alignment of items.
- Use `align-items` to define the vertical alignment of items.
- Use `flex-direction` if you need columns instead of rows.
- Use the `row-reverse` or `column-reverse` values to flip item order.
- Use `order` to customize the order of individual elements.
- Use `align-self` to vertically align individual items.
- Use `flex` to create flexible boxes that can stretch and shrink.

#### Flex Container & #### Flex Items
The container of the flex items
```css
.flex-container {
  display: flex;
}
```

The items within the flex container, can have their flex fill ability adjusted
```css
.flex-item {
  flex: 1; /*Could be 0.25, 1.5 etc*/
}
```

![[Pasted image 20240105163914.png]]
#### Aligning a flex item
```css
.flex-container {
  display: flex;
  justify-content: center; /*flex-start, flex-end, etc*/
}
```
![[Pasted image 20240105164014.png]]
#### Distribution of flex items
```css
.flex-container {
  width: 900px;
  display: flex;
  justify-content: space-around;
}
```
![[Pasted image 20240105164041.png]]
### Grouping of flex items
Flex items can be group by nesting divs e.g, moving the last two elements of a 3 item flex item container into another div:
![[Pasted image 20240105164331.png]]
#### Aligning Content

![[Pasted image 20240105164401.png]]
```css
.flex-container {
  width: 900px;
  height: 300px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

![[Pasted image 20240105164435.png]]

#### Wrapping flex items
![[Pasted image 20240105164553.png]]

#### Flex container direction
![[Pasted image 20240105165135.png]]
#### Alignment Consideration
![[Pasted image 20240105165226.png]]
#### Flex Item Order
![[Pasted image 20240105165256.png]]
```css
.flex-container {
  flex-direction: row-reverse; /*row, column, column-reverse*/
}
```

This reverses order PER ROW or PER COLUMN for example:
![[Pasted image 20240105165438.png]]

![[Pasted image 20240105165809.png]]
```css
.first-item {
  order: 1;
}

.last-item {
  order: -1;
}
```

#### Flexible Items:
![[Pasted image 20240105165946.png]]