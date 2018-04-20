# JavaScript coding guidelines

First read the [common guidelines]

## Don't use global variables
Please don't pollute the global scope by using global variables
```
// bad
x = true;

// better
var x = true;

// best
let x = true;
```
Don't use var if you don't have to

## Use let and const
Use let and const for variables, not var. The first two are block scoped
