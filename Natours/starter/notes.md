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

<!-- through video 17 -->

