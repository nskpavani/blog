# Emmet for HTML: A Beginner's Guide to Writing Faster Markup

Emmet is a powerful toolkit that dramatically speeds up HTML and CSS coding through abbreviations that expand into full code blocks. For example, when you type a short abbreviation, hit Tab or Enter, it expands into complete element markup.

## Why Emmet?

Writing HTML can be a very tedious task with opening and closing tags and its attributes. Emmet reduces this effort and also keeps almost 99% error free. Most modern code editors include Emmet support by default. Examples include VS Code, Sublime Text, Atom etc.

## How to Use it in Code Editors

Just type an abbreviation of an element and hit Tab or Enter. This will generate the element boilerplate.

Example: Type `div` and hit Tab, generates `<div></div>`

Few more examples:

```
p      →  <p></p>
span   →  <span></span>
```

---

## Creating HTML Elements Using Emmet

The most useful Emmet abbreviation:

`!` or `html:5` will expand to a complete HTML5 boilerplate:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

</body>
</html>
```

---

## Adding Classes, IDs, and Attributes

### Adding ID

To add ID to an element before it generates/expands, use `#`

```
div#header  →  <div id="header"></div>
```

### Adding Classes

To add a class to an element, use `.`

```
p.intro  →  <p class="intro"></p>
```

You can add multiple classes to an element:

```
div.container.main  →  <div class="container main"></div>
```

By default it takes `div` element when not mentioned explicitly:

```
#hero  →  <div id="hero"></div>
.card  →  <div class="card"></div>
```

### Adding Attributes

To add attributes, use square brackets `[..]`

```
a[href="#" title="Link"]              →  <a href="#" title="Link"></a>
img[src="photo.jpg" alt="Photo"]      →  <img src="photo.jpg" alt="Photo">
input[type="email" placeholder="Email"]  →  <input type="email" placeholder="Email">
```

### Adding Text Content

To add text content, use curly braces `{..}`

```
p{Hello World}  →  <p>Hello World</p>
a{Click here}   →  <a href="">Click here</a>
```

### Adding Numbering

To add numbering to a class, use `$`:

```
ul>li.item$*3
```

Generates:

```html
<ul>
    <li class="item1"></li>
    <li class="item2"></li>
    <li class="item3"></li>
</ul>
```

You can also use multiple dollar signs for zero-padding:

```
ul>li.item-$$$*3
```

Generates:

```html
<ul>
    <li class="item-001"></li>
    <li class="item-002"></li>
    <li class="item-003"></li>
</ul>
```

---

## Nested Elements or Multiple Elements at the Same Time

### Same Level Multiple Elements

Use `+` to create sibling elements:

```
div+p+span  →  <div></div><p></p><span></span>
h1+p        →  <h1></h1><p></p>
```

### Repeat Same Elements

Use `*` to multiply elements:

```
ul>li*5
```

Generates:

```html
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```

### Move Back Up One Level

Use `^` to move back up one level in the hierarchy:

```
div>p>span^div
```

Generates:

```html
<div>
    <p><span></span></p>
    <div></div>
</div>
```

### Group Complex Structures

Use parentheses `()` to group complex structures together:

```
div>(header>ul>li*2)+footer>p
```

Generates:

```html
<div>
    <header>
        <ul>
            <li></li>
            <li></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```
