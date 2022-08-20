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
                // background-color: black;
                padding: 10px 15px;

                &:hover {
                    background-color: black;
                }
            }
        }
    }

}
