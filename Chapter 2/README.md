# Chapter 2 - Sass @import and Partials

Sass keeps the CSS code DRY (Don't Repeat Yourself). One way to write DRY code is to keep related code in separate files.

You can create small files with CSS snippets to include in other Sass files. Examples of such files can be: reset file, variables, colors, fonts, font-sizes, etc.

## Sass Importing Files

Just like CSS, Sass also supports the `@import` directive.

The `@import` directive allows you to include the content of one file in another.

The CSS `@import` directive has a major drawback due to performance issues; it creates an extra HTTP request each time you call it. However, the Sass `@import` directive includes the file in the CSS; so no extra HTTP call is required at runtime!

### Sass Import Syntax

```scss
@import 'filename';
```

**Tip**: You do not need to specify a file extension, Sass automatically assumes that you mean a `.sass` or `.scss` file. You can also import CSS files. The `@import` directive imports the file and any variables or mixins defined in the imported file can then be used in the main file.

You can import as many files as you need in the main file:

```scss
@import 'config';
@import 'general';
@import 'fonts';
```

### Example 1

Let's look at an example: Let's assume we have a reset file called "config.scss", that looks like this:

```scss
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    outline: none;
    border: none;
    list-style-type: none;
    text-decoration: none;
}

html {
    scroll-behavior: smooth;
}
```

and now we want to import the "config.scss" file into another file called "general.scss".

Here is how we do it: It is normal to add the @import directive at the top of a file; this way its content will have a global scope:

```scss
@import 'config';

body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: #f2f3f5;
}
```

So when the `general.scss` file is transpiled, the CSS will look like this:

```scss
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    outline: none;
    border: none;
    list-style-type: none;
    text-decoration: none;
}

html {
    scroll-behavior: smooth;
}

body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: #f2f3f5;
}
```

## Sass Partials

By default, Sass transpiles all the `.scss` files directly. However, when you want to import a file, you do not need the file to be transpiled directly.

Sass has a mechanism for this: If you start the filename with an underscore, Sass will not transpile it. Files named this way are called partials in Sass.

So, a partial Sass file is named with a leading underscore:

```
_filename.scss
```

The following example shows a partial Sass file named "_colors.scss". (This file will not be transpiled directly to "colors.css"):

```scss
$pink-color: #EE82EE;
$blue-color: #4169E1;
$green-color: #8FBC8F;
```

Now, if you import the partials file, omit the underscore. Sass understands that it should import the file `_colors.scss`:

```scss
@import 'colors';

body {
    background-color: $pink-color;
    color: $blue-color;
}
```

## Links

[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/pranjalagupte)  
[![instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/pranjalagupte/)

## Authors

 - [@PranjalGupte](https://github.com/Pranjal-Gupte/)