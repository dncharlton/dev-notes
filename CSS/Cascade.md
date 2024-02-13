### Rules of the cascade
#### Specificity
A CSS declaration that is more specific will take precedence over less specific ones. Inline styles have the highest specificity compared to selectors, while each type of selector has its own specificity level that contributes to how specific a declaration is.

Different declarations have different weights and can be broadly put into below specificity hierarchy:
1. **Inline styles** - Example: `<h1 style="color: pink;">`
2. **IDs** - Example: `#navbar`
3. **Classes, pseudo-classes, attribute selectors** - Example: `.test` `:hover` `[href]`
4. **Elements and pseudo-elements** - Example: `h1` `::before`

##### Calculating Specificity
Start with a value of 0
1. Inline have a value of 1000, however as they come last in the cascade they will always win, it can be overridden with `!important`
2. Add 100 for each ID value
3. Add 10 for each class value (or pseudo-class or attribute selector)
4. Add 1 for each element selector or pseudo-element
5. Ignore the following as they have 0 value:
	1. `*`
	2. ` `
	3. `+`
	4. `~`
	5. `>`

| Selector | Breakdown | Calculation | Specificity Value |
| ---- | ---- | ---- | ---- |
| `p` | elem | 1 | 1 |
| `p.test` | elem + class | 1 + 10 | 11 |
| `p#demo` | elem + id | 1 + 100 | 101 |
| `<p style="color: pink;"` | inline | 1000 | 1000 |
| `demo` | id | 100 | 100 |
| `.test` | class | 10 | 10 |
| `p.test1.test2` | elem + class + class | 1 + 10 + 10 | 21 |
| `#navbar p#demo` | id + elem + id | 100 + 1 + 100 | 201 |
| `*` | 0 | 0 | 0 |

**The selector with the highest specificity value will win and take effect!**

#### Inheritance
Example:
```html
<!-- index.html -->
<div id="parent">
  <div class="child"></div>
</div>
```

```css
/* styles.css */
#parent {
  color: red;
}
.child {
  color: blue;
}
```

Parent Weight > 100
Child Weight > 10

Despite parent having higher weight/specificity, the child element will override with `colour: blue`, as `color: red` is inherited by the child, and child sets colour to blue, it will be overriden.

#### Rule Order
The final rule is the tie breaker and simplest, of equally weighted styles, the one last defined will be the tie-breaker.
