# HyperText Markup Language (HTML)

HTML is used to structure content on a web page (images, text, forms etc). We use HTML tags to structure contents. `tagName + tab` populates HTML tag directly.

## Basic Tags of HTML

- `<p>`: paragraph
- `<strong>`: make the text bold indicating that it's important
- `<small>`: make the text smaller
- `<em>`: make the text italic
- `<h1>` ~ `<h6>`: headings
- `<img>`
- `<ul>`: unordered list is a wrapper for `<li>` tags with symbols.
- `<ol>`: ordered list is a wrapper for `<li>` tags with numbers.
- `<div>`: used to divide contents into different sections or group together relevant contents which belong together. `<div>` has no visual difference but it comes handy when we work with CSS.
- `<span>`: used to add CSS or JS hooks to text of HTML.
- `<br>`: linebreak (no closing tag needed since no content inside it)
- `<hr>`: horizontal ruler (Equivalent to `<hr />`)
- `<img src="image_path", alt="text representation of image for accessibility">`
- `<a href="">`: href is hyperlink reference
- `<blockquote cite="source">`: used for quoting
- `<p style="">`: style attributes in `<p>` can be used for text styling.

## HTML Forms

```
<form action="">
    <label for="username">enter username: </label>
    <input type="text" id="username">
    <br><br>
    <label for="email"> enter email: </label>
    <input type="email" id="email">
    <br><br>
    <label for="password"> enter password: </label>
    <input type="password" id="password">

    <input type="radio" name="gender" value="Male"> Male <br>
    <input type="radio" name="gender" value="Female"> Female <br>
    <input type="radio" name="gender" value="Other"> Other <br>
</form>
```

- `id` attribute identifies a specific tag which can be used in CSS and JS.
- `name` attribute identifies a tag but it has another purpose which is service side processing. It'a always good practice to add `name`attribute same as `id`.
- `name` is also important for grouping for `radio` type.
- `required`: input must be provided for validataion
- `placeholder`: is like a `hint` in Android
- `<select> + <option>`

```
<label for="">Security Question:</label>
    <select name="question" id="question">
        <option value="q1">What colour are your favorite pair of socks?</option>
        <option value="q2">If you could be a vegetable, what it be?</option>
        <option value="q3">What is your favorite movie?</option>
    </select>
```
