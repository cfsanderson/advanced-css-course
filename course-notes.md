# Advanced CSS and Sass Course on [Udemy](https://www.udemy.com/advanced-css-and-sass/)
I started back over and plan to cruise back through the course.

## Section 2

- `clip-path` 

## NOTES
Resetting or normalizing CSS is less important now with better implementation in browsers. Basic reset should only need...
```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```  

When working with a background image, don't forget to set the background-position as well.
```css
div {
  background-size: cover;
  background-position: top; / sets the 
}
```  

Clip path works like a clipping mask that is set to coordinates. 
```css
div {
  clip-path: polygon(x y, x y, x y, x y);
}
```

## Section 3

### 3 Pillars of Good HTML and CSS (#13)
1) Responsive Design  
  - fluid layouts
  - media queries
  - responsive images
  - correct units
  - dektop-first vs mobile-first
2) Maintainable and Scalable Code  
  - clan
  - easy-to-understand
  - growth
  - reusable
  - how to organize files
  - how to name classes
  - how to sturcture HTML
3) Web Performance  
  - less HTTP requests
  - less code
  - compress code
  - use a CSS prepocessor
  - less images
  - compress images

### What happens to CSS when we load up a webpage?

Load HTML -->--Parse HTML--> ------------>------------------>----------------- DOM-------->-------+
                  |                                                                               |
                  |                                                                               |
                  |                                                                               |
                  Load CSS --> Parse CSS   --> -------------------------- --> CSS Object Model----|
                                - resolve conflicting CSS declarations                            |
                                - Process final CSS                                               |
                                                                                                  |
                Final rendered website <=----------Website rendering: <-------------------<--Render tree
                                              (the visual formatting model)

### How CSS is parsed (#14) 

A CSS rule has...
- a selector
- a declaration block that has
  - properties
  - declarations

#### Cascade  

Importance > Specificity > Source Order

Importance  
- User `!important` declarations
- Author `!important` declarations
- Author decla rations
- User declarations (browser settings)
- Default browser settings

Specificity
- Inline styles
- IDs
- Classes, pseudo-classes, attribute
- Elements, pseudo-elements

Source Order
- duh, order

