# Section 2

## Responsive Design

- fluid layouts
- media queries
- correct units
- destop/mobile first

## Maintainable and scalable code

- clean
- easy to understand
- growth
- reusable
- how to org files
- how to name classes
- how to structure HTML

## Web Performance

- less HTTP reqests
- less code
- compress codeuse a css preprocessor
- less images
- compress images

load HTML => parse HTML ==========================================> DOM
                |
                |
                |
              load CSS => Parse CSS
                            - resolve conflicting CSS declarations (cascade)
                            - proces final CSS values
                            - results in CSSOM (CSS Object Model)


DOM ===> + CSSOM ===> Render Tree ===> site rendering: the visual formatting model ===. Final render (painted) website

## #14 how CSS is parsed, Part 1: the cascade and specificity

- selector
- declaration block

CSS can come from

- author (you)
- user (e.g. increase base font size)
- browser (user agent)

Importance:

- user `!important` declarations
- author `!imporant` declarations
- author declarations
- user declarations
- default browser declarations
... if same

Specificity:

- inline styles
- IDs
- classes, pseudo-classes, attribute
- elements, pseudo-elements
...if still same

Source Order:

- last in wins

## #16 How CSS values are parsed

1 - declared value (author declarations)
2 - cascaded values (after the cascade)
3 - specified value (defaulting, if ther is no cascaded value)
4 - computed value (converting relative values to absolute)
5 - used value (final calculations, based on layout)
6 - actual value (browser and device restrictions)

## #17 Inheritance

Basically every element either inherits the properties of it's parent or it doesn't.  
Most things font-based inherit (line-height, color, size, etc.) but things like padding and margin on a div obviously don't or shouldn't.  
Using the `inherit` property forces an element to inherit from it's parent where it normally wouldn't. This can be a powerful tool in cases like the global reset where we do...

```css
*,
::after,
::before {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

html {
  font-size: 62.5%;
}

body {
  box-sizing: border-box;
}
```
## #18 Converting px to rem

See reset above :point-up:

The goal is to get the root font-size to 10px so that you can easily convert all px measurements to rem by dividing by 10.
Since it's bad practice to explicity overwrite the base font size in px, percentages are better and allow users to zoom or set base size explicitly and everything will adjust.
62.5% turns 16px (the default font-size for all browsers) into 10px.

## #18 The Visual Formatting Model

1) box model
- fill area includes content plus padding and margin but not border - for background images or color
- when defining the width or height of something, by default CSS does not include the padding, margin, or border.
  - e.g. div with padding 20px and content area of 100px wide would actually end up as 140px wide.
  - this is fixed with `box-sizing: border-box;` which includes padding and margin in overall width or height. The abover example is now 100px wide.

2) box types: inline, block-level, and inline-block

- **Block-level boxes**
  - elements formatted visually as blocks
  - 100% of parent's width
  - Verically, one after another
  - Box-model applies as showed
    - `display: block;` also...
      - `display: flex;`
      - `display: inline-flex;`
      - `display: table;`

- **Inline-block boxes**
  - A mix of block and inline
  - Occupies only content's space
  - No line-breaks
  - Box-model applies as showed
    - `display: inline-block;`

- **Inline boxes**
  - Content is distributed in lines
  - Occupies only content's space
  - No line-breaks
  - No heights and widths
  - Padding and margins only horizontal (left and right)
    - `display: inline;`

3) Positioning Schemes: Normal flow, absolute positioning, and floats

- **Normal flow**
  - Default positioning scheme;
  - NOT floated;
  - NOT absolutely positioned;
  - Elements laid out accouding to their source order.
    - Default
    - `position: relative;`
- **Floats**
  - Element is removed from the normal flow;
  - Text and inline elements will wrap around the floated element;
  - the container will not adjust it's height to the element.
    - `float: left;`
    - `float: right;`
- **Absolute positioning**
  - Element is removed from the normal flow;
  - NO impact on surrounding content or elements;
  - We use `top`, `bottom`, `left`, and `right` to offset the element from its relatively positioned container.
    - `position: absolute;`
    - `position: fixed;`

4) Stacking Contexts
(like layers in Photoshop)
- `z-index` is one way to create stacking contexts but also opacity value, transition property, etc can also change.

## #19 The Think - Build - Architect Mindset
- think about the layout
- build with good CSS and markup - meaningful class names (BEM)
- architect with good file and folder organization

Component-driven Design
- modular building blocks
- held together by the layout of the percentages
- re-usable across a project and even between diff projects
- Independent, allowing us to use them anywhere on the page.
[e.g. ATOMIC DESIGN]

### BEM - Block Element Modifier
- BLOCK: standalone component that is meaningful on its own. `.block {}`
- ELEMENT: part of a block that has no standalone meaning. `.block__element {}`
- MODIFIER: a diff version of a block or an element. `.block__element--modifier {}` or `.block__element--modifier--modifiers {}` 

 ### The 7-1 Pattern
 - 7 different folders for partial Sass files, and 1 main Sass file to import all other files into a compiled CSS stylesheet
   - `base/`
   - `components/`
   - `layout/`
   - `pages/`
   - `themes/`
   - `abstracts/`
   - `vendors/`
