# SASS-Syntactically Awesome Style Sheet
SASS is a CSS Preprocessor. 

## SASS Variable
Using SASS variable we can store: 
- String
- Numbers
- Colors
- Booleans
- Lists
- Nulls

### Declaring SASS Variable 
    - $primary-color: red;
    - $header: 36px;
### Use of SASS Variable
    header{
        background-color: $primary-color;
    }

## SASS Nested Rules and Properties

```
nav {
    background-color: cadetblue;
    ul {
        list-style: none;
        li {
            margin: 0 10px;
            display: inline-block;
            padding: 10px;
            a {
                text-decoration: none;
                color: white;
                font-size: 22px;
                transition: 0.4s;
                border-radius: 15px;
                display: inline-block;
                padding: 10px 15px;
                &:hover {
                    background-color: black;
                }
            }
        }
    }
}
```

## SASS @forward and partials
Sass keeps the CSS code DRY (Don't Repeat Yourself). One way to write DRY code is to keep related code in separate files.

### Sass Partials
By default, Sass transpiles all the .scss files directly. However, when you want to import a file, you do not need the file to be transpiled directly.

Sass has a mechanism for this: If you start the filename with an underscore, Sass will not transpile it. Files named this way are called partials in Sass.

So, a partial Sass file is named with a leading underscore:

#### Sass Partial Syntax:

```
_filename.scss;
```
#### Sass @forward
You can import as many files as you need in the main file using @forward:
Example: 
```
@forward "variables";
@forward "colors";
@forward "reset";
```
## Sass @use Modules
The @use rule loads mixins, functions, and variables from other Sass stylesheets, and combines CSS from multiple stylesheets together. Stylesheets loaded by @use are called "modules". Sass also provides built-in modules full of useful functions.
```
// Import Base variables
@forward "./base/variables";
// Use Primary Utility Variables
@use "./utils/primary-variables" as variables;
```
#### Use of @use module
```
h1 {
    font-size: variables.$primary-heading;
}
p {
    font-size: variables.$base_text;
}

```

## @mixins and @include
Mixins allow you to define styles that can be re-used throughout your stylesheet. They make it easy to avoid using non-semantic classes like .float-left, and to distribute collections of styles in libraries.

#### Create Mixin
```
// Mixins for Button
@mixin primary-button {
    padding: 10px 20px;
    border: none;
    border-radius: 20px;
    color: white;
    cursor: pointer;
    margin: 20px;
    font-size: 20px;
    font-weight: bold;
}
```
#### Use Mixin using @include
```
// Mixin to include
.click {
    @include primary-button();
    background-color: violet;
}

.order {
    @include primary-button();
    background-color: chocolate;
}
```
### Pass parameter and argument with mixin and include
#### Mixin with parameter
```
// Mixins for Button
@mixin primary-button($color) {
    padding: 10px 20px;
    border: none;
    border-radius: 20px;
    color: white;
    cursor: pointer;
    background-color: $color;
    margin: 20px;
    font-size: 20px;
    font-weight: bold;
}
```
#### @include with argument
```

// Mixin to include
.click {
    @include primary-button(violet);
}
.order {
    @include primary-button(chocolate);
}
```

## Sass @extend Directive
The @extend directive lets you share a set of CSS properties from one selector to another.

The @extend directive is useful if you have almost identically styled elements that only differ in some small details.

The following Sass example first creates a basic style for buttons (this style will be used for most buttons). Then, we create one style for a "Report" button and one style for a "Submit" button. Both "Report" and "Submit" button inherit all the CSS properties from the .button-basic class, through the @extend directive. In addition, they have their own colors defined:
#### Extend and Inheritance Example
```
// Extend
.primary-button {
    padding: 10px 20px;
    font-size: 20px;
    cursor: pointer;
    margin: 10px;
    color: white;
    border: 0;
    border-radius: 20px;
}
// Extend in another class
.green-button {
    @extend .primary-button;
    background-color: green;
}
.red-button {
    @extend .primary-button;
    background-color: red;
}
```
## Conditional Control Statement
Sass allows us to control the flow of our scripts through specific expressions that evaluate conditions. Based on the result of these conditions, Sass will execute certain sections of specified code.
```
<!-- HTML -->
<button class="success">Success</button>
<button class="warning">Warning</button>
<button class="danger">Danger</button>
<button class="normal">Normal</button>
```
```
// Working with Conditional Control Statement
@mixin setButtonColor($color) {
    @if $color ==success {
        background-color: #3a86ff;
    }
    @else if $color ==warning {
        background-color: #bc6c25;
    }
    @else if $color ==danger {
        background-color: #e63946;
    }
    @else {
        background-color: #219ebc;
    }
}
@mixin simpleButton {
    font-size: 20px;
    border-radius: 20px;
    padding: 10px 20px;
    margin: 20px;
    border: none;
    cursor: pointer;
}
.success {
    @include simpleButton;
    @include setButtonColor(success)
}
.warning {
    @include simpleButton;
    @include setButtonColor(warning)
}
.danger {
    @include simpleButton;
    @include setButtonColor(danger)
}
.normal {
    @include simpleButton;
    @include setButtonColor(normal)
}
```
## Looping in SASS
Sass has several loop options, much like other programming languages. They include the @for loop, @each loop and @while loop. These loops are an incredibly powerful tool for generating CSS code because you can defer code generation into an iterable task.
### For Loop
``` 
<!-- HTML Code -->
<div class="row">
    <div class="col-1">Div-1</div>
    <div class="col-2">Div-2</div>
    <div class="col-3">Div-3</div>
    <div class="col-4">Div-4</div>
    <div class="col-5">Div-5</div>
    <div class="col-6">Div-6</div>
    <div class="col-7">Div-7</div>
    <div class="col-8">Div-8</div>
    <div class="col-9">Div-9</div>
    <div class="col-10">Div-10</div>
    <div class="col-11">Div-11</div>
    <div class="col-12">Div-12</div>
</div>       
```
```
<!-- SASS Code    -->

[class*="col-"] {
    float: left;
    background-color: red;
    margin: 10px 0;
    padding: 10px;
    color: wheat;
    font-size: 20px;
    text-align: center;
    border: 2px solid slateblue;
}
@for $i from 1 through 12 {
    .col-#{$i} {
        width: 100% / 12 * $i;
    }
}
.row::after {
    clear: both;
}
```









