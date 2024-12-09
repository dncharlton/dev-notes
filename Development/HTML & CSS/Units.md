#### Absolute Units
`px` - absolute pixel size
`in` - inches
`cm` - centimeters 

#### Relative Units
`em` - font size
`rem` - font size (preferred)

e.g. `font-size: 16px; width: 4em;` total width would be `16*4=64px`

`1rem` is the `font-size` of the root element (either `:root` or `html`)

#### Viewport units
The units `vh` and `vw` relate to the size of the viewport. Specifically, `1vh` is equal to `1%` of the viewport height and `1vw` is equal to `1%` of the viewport width. These can be useful any time you want something to be sized relative to the viewport, examples including full-height heroes, full-screen app-like interfaces.

- **Viewport Width** (`vw`) – A percentage of the full viewport width. `10vw` will resolve to 10% of the current viewport width, or `48px` on a phone that is `480px` wide. The difference between `%` and `vw` is most similar to the difference between `em` and `rem`. A `%` length is relative to local context (containing element) width, while a `vw` length is relative to the full width of the browser window.
- **Viewport Height** (`vh`) – A percentage of the full viewport height. `10vh` will resolve to `10%` of the current viewport height.
- **Viewport Minimum** (`vmin`) – A percentage of the viewport width or height, _whichever is smaller_. `10vmin` will resolve to `10%` of the current viewport width in portrait orientations, and `10%` of the viewport height on landscape orientations.
- **Viewport Maximum** (`vmax`) – A percentage of the viewport width or height, _whichever is larger_. `10vmax` will resolve to `10%` of the current viewport height in portrait orientations, and `10%` of the viewport width on landscape orientations. Sadly, and strangely, `vmax` units are not yet available on Internet Explorer or Edge.


