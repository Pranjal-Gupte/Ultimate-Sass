# Chapter 3 - Sass @mixin and @include

## Sass Mixins

The `@mixin` directive lets you create CSS code that is to be reused throughout the website.

The `@include` directive is created to let you use (include) the mixin.

## Defining a Mixin

A mixin is defined with the `@mixin` directive.

```
@mixin name {
    property: value;
    property: value;
    ....
}
```

Let's create a mixin named 'important-word'

```scss
@mixin important-word {
    color: red;
    font-size: 30px;
    text-transform: uppercase;
    font-weight: 400;
}
```

> **Note: A tip on hyphens and underscore in Sass: Hyphens and underscores are considered to be the same. This means that @mixin important-text { } and @mixin important_text { } are considered as the same mixin!**

## Using a mixin

The `@include` directive is used to include a mixin.

```
selector {
    @include mixin-name;
}
```

So, to include the important-text mixin created above:

```scss
span.imp-word {
    @include important-text;
    background-color: black;
}
```

The Sass transpiler will convert the above to normal CSS:

```css
span.img-word {
    color: red;
    font-size: 30px;
    text-transform: uppercase;
    font-weight: 400;
    background-color: black;
}
```

A mixin can also have other mixins:

```scss
@mixin button {
    @include btn-font;
    @include btn-bg;
    @include btn-other;
}
```

## Passing variables to a Mixin

Mixins accept arguments. This way you can pass variables to a mixin.

Here is an example to define a mixin with arguments:

```scss
@mixin bordered($width, $color) {
    border: $width solid $color;
}

article {
    @include bordered(2px, red);
}

aside {
    @include bordered(1px, blue);
}
```

Notice that the arguments are set as variables and then used as the values (color and width) of the border property.

After compilation, the CSS will look like this:

```css
article {
    border: 2px solid red;
}

aside {
    border: 1px solid blue;
}
```

## Default Values for a Mixin

It is also possible to define default value for mixin variables:

```scss
@mixin bordered($width: 2px, $color: red) {
    border: $width solid $color;
}
```

Then, you only need to specify the values that change when you include the mixin:

```scss
article {
    @include bordered($color: blue);
}
```

## Using a Mixin for Vendor Prefixes

Another good use of a mixin is for vendor prefixes

Here is an example for transform:

```scss
@mixin transform($value) {
    -webkit-transform: $value;
    -ms-transform: $value;
    transform: $value;
}

.container {
    .box {
        @include transform(rotate(90deg));
    }
}
```

After compilation, the CSS will look like this:

```css
.container .box {
    -webkit-transform: rotate(90deg);
    -ms-transform: rotate(90deg);
    transform: rotate(90deg);
}
```

## Links

[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/pranjalagupte)  
[![instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/pranjalagupte/)

## Authors

 - [@PranjalGupte](https://github.com/Pranjal-Gupte/)
