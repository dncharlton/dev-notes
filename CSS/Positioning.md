#### Static and relative positioning

The default positioning mode that you’ve gotten used to is `position: static`. The difference between static and relative is fairly simple. Static is the default position of every element, and properties `top`, `right`, `bottom`, and `left` do not affect the position of the element. Relative on the other hand is pretty much the same as static, but properties `top`, `right...(etc.)` displace the element relative to its normal position in the flow of the document.

#### Absolute positioning

`position: absolute` allows you to position something at an exact point on the screen without disturbing the other elements around it. More specifically, using absolute positioning on an element will remove that element from the normal document flow while being positioned relative to an ancestor element. To put it in simple terms: elements that are removed from the normal flow of the document don’t affect other elements and are also not affected by other elements. Using absolute positioning allows you to position elements anywhere on the screen using `top`, `right`, `bottom`, and `left` properties. This property is really useful when you want to position something at an exact point on the screen, without disturbing any of the other elements. A couple of good use cases for absolute positioning are:

- modals
- image with a caption on it
- icons on top of other elements

#### Fixed positioning

Fixed elements are also removed from the normal flow of the document and are positioned relative to the `viewport`. You basically use `top`, `right`, `bottom`, and `left` properties to position it, and it will stay there as the user scrolls. This is especially useful for things like navigation bars and floating chat buttons.

#### Sticky positioning

Sticky elements will act like normal elements until you scroll past them, then they start behaving like fixed elements. They are also not taken out of the normal flow of the document. It might sound confusing, but checking out the behaviour of [this](https://codepen.io/theanam/pen/MPLBYy) example might clear things up for you. It’s useful for things like section-headings. Remember being able to still see what category you’re looking at while scrolling through a shop? This is how it’s done!

[mdn article](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
