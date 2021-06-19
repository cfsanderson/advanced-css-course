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

