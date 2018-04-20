# CSS - coding guidelines

These are the coding guidelines for CSS and SCSS. Following these will result in code that is less error prone, better readable and more in line with other peoples code.

## SCSS
A list of tips, not in the best order...

### Don't style html elements
Other than global setting, using html elements in your selector is a bad idea.
**Bad code**
```
button.button {}
```
this will tie your code down as it can only work on a button, making it inflexible.
**Good code**
```
.button {}
```
You may wanna set some styles globally, typography, some colours or the like
```
body {
  // global styling
}
```
or you can set the html element you expect in comments, if you think that it will make things clearer.
```
/*button*/.button {}
```

### Naming things
Choosing the right name for your class is one of the hardest things to do. Choose wisely, it will reduce the amount of phone calls you will receive while on holiday.
**Bad code**
```
// don't do this as it could become out of date
.red {
  color: red;
}
// is too specific as for the location
.nav a {
  color: green;
}
// is the color only needed here
.nav-color {
  color: green;
}
```
**Good code**
```
// we want to use it in more places
.attention-color {
  color: green;
}
```

### Nesting
SCSS let's you nest selectors, which is something you should avoid if you can.
**Bad code**
```
.foo {
  .bar {}
}
.foo {
  &__bar {}
}
```
Problem with the code above is that it is not easy to find, searching for `.foo .bar` of `.foo__bar` will give you no result.

**Good code**
```
.foo .bar {}
.foo__bar {}
```
**Better code**
```
.foo {}
.bar {}
.foo__bar {}
```
This gives you the lowest possible specificity, thus making it more flexible

### Mixins
Use mixins when you need to repeat your self, a [post-processor](https://www.npmjs.com/package/postcss-discard-duplicates) can handle the duplicate code for you.
```
.list {
  @include resetList;
  // more code
}
.other-list {
  @include resetList;
  // more code
}
```
For more info on [mixins](https://scotch.io/tutorials/how-to-use-sass-mixins).

### Simple is better.
Writing code is hard, writing readable code is even harder

**Bad code**
```
.foo ~ .bar:not([type="submit"]) {}
  ```
  While I enjoy a puzzle this is not clear right away
  Consider using a class instead.

### Linting
Checking code is boring, that is why we have computers. Use [stylelint](https://stylelint.io/) to catch the common mistakes. It also helps enormously in keeping your code consistent.
### BEM
Please use the BEM convention in your css. It gives you a proper system to work with and explain to other people.

A name in BEM can contain a block, a element and a modifier.

**BEM example**
```
.head {}
.head__ears {}
.head--red {}
```
For more info on BEM look [here](getbem.com) or [here](bem.info)

### Don't use ID's
ID's are way too specific for styling, just don't. ID's should be used only by JavaScript or backend code. For styling purposes they are too specific.

A id needs a other id or an `!important` statement to counter it.

So, don't use ID's

### Sources

I read a lot of other style guides and processes surrounding them and borrowed from them:
- [cssguidelin.es](https://cssguidelin.es/)
- [Tait brown](http://taitems.github.io/Front-End-Development-Guidelines/)
- [Brad Frost](http://bradfrost.com/blog/post/frontend-guidelines-exercise)
  - [isobar](https://isobar-us.github.io/code-standards/)
  - [gitlab](https://docs.gitlab.com/ee/development/fe_guide/style_guide_scss.html)
