# Advanced CSS and Sass Course on [Udemy](https://www.udemy.com/advanced-css-and-sass/)
This is my second run go through the course. 

From the root of each project run 
- `live-server` in one terminal and 
- `npm run compile:sass` in another.

### Table of Contents
- [Section 2](#section-2)
- [Section 3](#section-3)
- [Section 4](#section-4)
- [Section 5](#section-5)

-----------------------
## Section 2

- `clip-path` 

## NOTES
Resetting or normalizing CSS is less important now with better implementation in browsers. Basic reset should only need...
```css
*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
    / https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing
}
```  

When working with a background image, don't forget to set the background-position as well.
```css
div {
  background-size: cover;
  background-position: top;
}
```  

Clip path works like a clipping mask that is set to coordinates. 
```css
div {
  clip-path: polygon(x y, x y, x y, x y);
}
```

([Back to Top](#table-of-contents))  

-----------------------
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


### Convert to REM (lecture 18)
```scss
html {
  font-size: 62.5%; // converts default 16px font-size of most browsers to 10px
}

p { font-size: 1.6rem; /* equals 16px */  }
```
After this reset, all future `px` declarations are given in multiples of `.1rem`.  


### Visual Formatting Model (lecture 19)
- box model
  - [box-sizing](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing)  


### Implementing BEM (lecture 20 and 21)

`block__element--modifier`   


([Back to Top](#table-of-contents))  

-----------------------
## Section 4

### Mixins, Functions, and Extends
[Codepen with examples from course](https://codepen.io/cfsanderson/pen/yGPNwN?editors=1100)

**MIXIN**
Works like a variable that is reusable throughout code.
```scss
/* without a variable */
@mixin clearfix {
  &::after {
    content: "";
    clear: both;
    display: table;
  }
}

/* with a variable */
@mixin style-link-text($color) {
  color: $color;
}

nav {
  margin: 3rem;
  background-color: $color-primary;

  @include clearfix; //without passing in a variable
  @include style-link-text($color-text-light) //passing in a variable - similar to a function
}
```

**FUNCTION**
```scss
@function divide($a, $b) {
  @return $a / $b;
}

nav {
  margin: divide(60, 2) * 1px;
}

// silly use of a function but works
```

**EXTENDS**
Extends is similar to @mixin but instead of compilng the declarations into the selector (mixing them in), it makes a whole new selector with the given declarations.

```scss
%btn-placeholder {
  padding: 1rem;
	display: inline-block;
	text-align: center;
	border-radius: 10rem;
	width: $width-button;	
	@include style-link-text($color-text-light);	
}

.btn--main {
  &:link {
    @extend %btn-placeholder;
  }
}
```
This would compile to something like...
```scss
.btn--main:link {
  padding: 10px;
	display: inline-block;
	text-align: center;
	border-radius: 100px;
	width: 25px;	
	color: #fff;
}
```  

### Installing and Compiling Sass 
- `npm init` which starts walkthrough to initialize a `package.json`
- `npm install node-sass --save-dev` installs `node-sass` as a dev dependency in `package.json`
- Add `"scripts": { "compile:sass": "node-sass sass/main.scss css/style.css"}` to `package.json`  


([Back to Top](#table-of-contents))  

-----------------------
## Section 5

### lecture 30 = intro  

### lecture 31 - converting CSS to Sass  

### lecture 32 - implementing the 7-1 CSS Architecture  
- abstracts
- base
- components
- layout
- pages
- themes (not included but would include dark theme etc.)
- vendors (not included but would include 3rd party frameworks like bootstrap)
  
### lecture 33 - review basic principles of responsive design and layout types  
1 - fluid grids and layouts
2 - flexible/responsive images
3 - media queries

Natours - float layout (b/c still maintainable)
Nexter - flexbox
Trillo - grid  

### lecture 34 - building a custom grid with floats
stopped at 25

### lecture 35-37 - building the about section part 1

### lecture 39

TODO - make variables for box shadows and replace throughout

**Stopped 2/4 at 8:00 on lecture 50**