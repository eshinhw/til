# Cascading Style Sheets (CSS)

CSS works alongside with HTML, and are used to style web pages to make them look better by changing colours, position, effects, font sizes etc.

## Some Decorations in CSS

- `color`
- `background-color`
- `text-decoration`
- `font-family`
- `text-align`
- `line-height`
- `letter-spacing`
- `column-count`
- `column-gap`
- `border-width`
- `border-style`

## Classes and Selectors

```css
<p class="intro"> Hello World! </p>
<div class="first"> First Div </div>
<p id="uniqueID"> Paragraph for UniqueID </p>
<a href="www.google.com"> Click here! </a>
<div class="second"><p> Second Div </p></div>
```

We can modify the contents of HTML tags using CSS decorations.

```css
p {
    /* decorations for all <p> tags */
}

.intro {
    /* decorations for all tags which class name is "intro" */
}

div p {
    /* decorations for <p> tags which parent is <div> */
}

#uniqueID {
    /* decorations for all tags which ID are "uniqueID" */
}

p.error {
    /* decorations for all <p> tags which class name is "error" */
}

p.error.success {
    /* decorations for all <p> tags which class name is "error" and "success" */
}

div p a {
    /* decorations for all <a> tags inside <p> and <div> in order (<p> must be inside <div>) */
}

div .error {
    /* decorations for any class of "error" inside <div> */
}
```

## Attribute Selectors

```css
a[href] {
    /* decorations for all <a> tags which have href attribute */
}

a[href="google.com"] {
    /* decorations for all <a> tags which have href attribute with "google.com" */
}

a[href*="google"] {
    /* decorations for all <a> tags which href attribute contains "google" */
}

a[href$=".com"] {
    /* decorations for all <a> tags which href attribute ends with ".com" */
}
```

## CSS Cascade - Inheritance and Specification

CSS runs from the top to the bottom. However, selectors with more specific selections can't be overriden.

```html
<div><p>Hello World!</p></div>
```

```css
div {
    color: red;
    border: 1px solid grey;
    margin: 40px;
    font-weight: bold;
}

p {
    border:inherit;
    margin:inherit;
    /* crimson color is more specific decoration -> overrides parent color decoration */
    color: crimson; 
}
```

## CSS Flexbox

![css-flexbox](https://user-images.githubusercontent.com/41933169/215594227-e57d8499-f27f-4e23-97fd-7ed90b2bb7a6.png)

## Remove Hyperlink Styling from Texts

We need to apply `text-decoration: none` on `a` tag instead of `p` or `span`.

```
.header__title a {
    text-decoration: none
}
```



```

