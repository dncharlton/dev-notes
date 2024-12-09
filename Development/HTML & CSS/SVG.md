SVGs are a scalable image format that use math to create images rather than rasterised images.
SVGs are often used for:
1. Icons
2. Graphs/Charts
3. Large, simple images
4. Patterned background
5. Applying effects to other elements via SVG filter

SVG Example:
```html
<div class="container">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
    <rect x=0 y=0 width=100 height=100 fill="burlywood"/>
    <path d="M 10 10 H 90 V 90 L 10 60" fill="transparent" stroke="black" stroke-width="3"/>
  <circle cx=50 cy=50 r=20 class="svg-circle"/>
    <g class="svg-text-group">
      <text x="20" y="25" rotate="10" id="hello-text">Hello!</text>
      <use href="#hello-text" x="-10" y="65" fill="white"/>
    </g>
</svg>
</div>
```

```css
.container {
  max-width: 200px;
  margin: auto;
}

.svg-circle:hover + .svg-text-group {
  opacity: 0;
}
```

| With Mouse Hover                     | Without Mouse Hover                  |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20240918093108.png]] | ![[Pasted image 20240918093150.png]] |
1. `xmlns` - stands for “XML NameSpace”. This specifies what _dialect_ of XML you’re using. In our case, that dialect is the SVG language spec. Without it, some browsers will not render your image or will render it incorrectly.
2. `viewBox` - defines the bounds of your SVG. When you have to define the positions of different points of the elements in your SVG, this is what that’s referencing. It also defines the aspect ratio _and_ the origin of your SVG. So it’s doing quite a lot! Be sure to play around with different values in the example above to get a feel for how it affects the shapes.
3. `class`, `id` - these attributes function just like they do in HTML. Using these in SVGs allows you to easily target an element via CSS or JavaScript, or to reuse an element via the [`use` element](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/use).
4. Elements such as `<circle>`, `<rect>`, `<path>`, and `<text>` are defined by the SVG namespace. These are our basic building-blocks. Although you can make extremely complex images with SVG, they are mostly created with just a dozen or so of these basic elements. Here is a [complete list of SVG elements](https://developer.mozilla.org/en-US/docs/Web/SVG/Element).
5. Many SVG attributes, such as `fill` and `stroke`, can be changed in your CSS. Learn more in this [article on SVG properties and CSS](https://css-tricks.com/svg-properties-and-css/).