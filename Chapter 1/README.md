# Chapter 1 - Sass Variables and Nesting

Variables are a way to store information that you can re-use later. With Sass, you can store information in variables, like:

- strings
- numbers
- colors
- booleans
- lists
- nulls

Sass uses the `$` symbol, followed by a name, to declare variables.

### Sass Variable Syntax

```scss
$variable-name: value;
```

### Example 1

The following example declares 4 variables named myFont, myColor, myFontSize, and myWidth. After the variables are declared, you can use the variables wherever you want:

```scss
$myFont: Helvetica, sans-serif;
$myColor: red;
$myFontSize: 18px;
$myWidth: 680px;

body {
  font-family: $myFont;
  font-size: $myFontSize;
  color: $myColor;
}

#container {
  width: $myWidth;
}
```

So, when the Sass file is transpiled, it takes the variables (myFont, myColor, etc.) and outputs normal CSS with the variable values placed in the CSS, like this:

CSS Output:

```css
:root {
    --my-font: Helvetica, sans-serif;
    --my-color: red;
    --my-font-size: 18px;
    --my-width: 680px;
}

body {
    font-family: var(--my-font);
    font-size: var(--my-font-size);
    color: var(--my-color);
}

#container {
    width: var(--my-width);
}
```

## Sass Variable Scope

Sass variables are only available at the level of nesting where they are defined.   
Look at the following example:

```scss
$myColor: red;

h1 {
  $myColor: green;
  color: $myColor;
}

p {
  color: $myColor;
}
```

Will the color of the text inside a `<p>` tag be red or green? It will be red!

The other definition, `$myColor: green;` is inside the `<h1>` rule, and will only be available there!   
So, the CSS output will be:

```css
h1 {
  color: green;
}

p {
  color: red;
}
```

## Using Sass !global

The default behavior for variable scope can be overridden by using the `!global` switch. `!global` indicates that a variable is global, which means that it is accessible on all levels.

Look at the following example (same as above; but with !global added):

```scss
$myColor: red;

h1 {
  $myColor: green !global;
  color: $myColor;
}

p {
  color: $myColor;
}
```

Now the color of the text inside a `<p>` tag will be green!

So, the CSS output will be:

```css
h1 {
  color: green;
}

p {
  color: green;
}
```

> **Note: Global variables should be defined outside any rules. It could be wise to define all global variables in its own file, named "_globals.scss", and include the file with the @include keyword.**

# Sass Nested Rules and Properties

Sass lets you nest CSS selectors in the same way as HTML.

Look at an example of some Sass code for a site's navigation:

```scss
nav {

  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li {
    display: inline-block;
  }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

Notice that in Sass, the ul, li, and a selectors are nested inside the nav selector.

While in CSS, the rules are defined one by one (not nested):

```css
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

nav li {
  display: inline-block;
}

nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```

Because you can nest properties in Sass, it is cleaner and easier to read than standard CSS.

## Sass Nested Properties

Many CSS properties have the same prefix, like font-family, font-size and font-weight or text-align, text-transform and text-overflow.

With Sass you can write them as nested properties:

```scss
font: {
  family: Helvetica, sans-serif;
  size: 18px;
  weight: bold;
}

text: {
  align: center;
  transform: lowercase;
  overflow: hidden;
}
```

The Sass transpiler will convert the above to normal CSS:

```css
font-family: Helvetica, sans-serif;
font-size: 18px;
font-weight: bold;

text-align: center;
text-transform: lowercase;
text-overflow: hidden;
```

## Links

[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/pranjalagupte)  
[![instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/pranjalagupte/)

## Authors

 - [@PranjalGupte](https://github.com/Pranjal-Gupte/)