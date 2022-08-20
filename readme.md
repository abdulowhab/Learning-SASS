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







