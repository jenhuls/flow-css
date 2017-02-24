# CSS Styleguide

> A proposal for structuring CSS in larger web projects

There are bunch of various CSS guidelines, methodologies and blueprints are available on the internet. I did research (briefly) on numbers of leading projects before come down to draft this document.

Here's a list of a few of main existing guidelines that I looked into:

* Object-Oriented CSS (OOCSS)
* BEM - Block, Element, Modifier
* SMACSS - Scalable and Modular Architecture for CSS
* MaintainableCSS
* SUIT CSS
* Systematic CSS

Before move into the proposing solution, let's summarize the few of existing guidelines here;

### Object-Oriented CSS (OOCSS)

OOCSS is based Object-oriented thinking pattern as implicates by its' name.

A best example for uses of OOCSS is [Bootstrap](http://getbootstrap.com/). All the bootstrap style classes has organized in OOCSS manner.

Ex-
```
.btn
.btn-default
.btn-primary
.btn-success
```

### BEM - Block, Element, Modifier

BEM is entirely focused on __naming convention__ of CSS classes. It has divided into three type of CSS classes based on the behaviour.

* **Block**  .block
* **Element**   .block__element
* **Modifier**  .block__element--modifier

Ex-
```
.notifications // block
.notifications__error or notifications__warnning // element
.notifications--show or .notifications--hide // modifier
```

### SMACSS - Scalable and Modular Architecture for CSS

SMACSS is also based on categorization of CSS rules. Unlike BEM; SMACSS classified CSS rules into five categories:

* **Base**  Primary html DOM elements, such as `body`, `h1`, `p` `a` ..etc.
* **Layout**  This may be like `.page-layout`, `.contact-form`, `.alert` ..etc.
* **Modules**  Modules are reusable components. `.btn`, `.input-field`
* **State**  The state of the DOM element. `.show`, `.notified` ..etc.

## Conclusion

The conclusion is; all the above guidelines have both pros and cons and those things are always depends on the use-case and the complexity of the application.

Secondly, in a real-world project, if someone or an organization wants to implements a styleguide such as for web development projects; it can't be based on a single methodology (above mentioned or any other). In that case, we may need to make an additional set of rules for a better implementation.

---

## Proposal

### Objective

* Structuring CSS in large web projects
* Keep codes transparent, sane, and readable
* Keep styles/stylesheets as maintainable
* Keep codes as scalable

### Guidelines

#### Use latest CSS versions and related technologies as possible

In the time I draft this document; the latest CSS version is CSS3 and there are two commonly use CSS preprocessors as LESS and SASS.

##### Always `Minify`, `Transpile` the CSS codes as needed

Use `Gulp`, `Webpack` or any other task-runner/module bundler to automate the process.

#### File / Directory structure

There are no right or wrong way to structured the CSS files, but keep them organize in module-wise manner is a best way to manage a large project.

Ex-
```
css/
  vendor/
    xyz/
      xyz.min.css
  sass/
    header.sass
    theme.sass
    sidebar.sass
  final.css
```

Here, we keep all the third-party css libraries (if any) in `vendor/` directory, and `SASS` files in `sass/` directory as divided into separate modules. Finally, the transpiled-minified version of all, keeps as in `final.css`.

#### Code styles

##### Put stylesheet information in top of the each css file

> Follow the YAML standards

Ex-
```
/**
  file: theme.css
  description: Common theme styles
  date-created: February 28, 2017
  date-modified: March 01, 2017
  authors:
    - _thinkholic
    - Indika
  includes:
    - Header
    - Primary Menu
    - Button Styles
**/
```

##### Put a title for each main sections

```
/** -------------------------
  =Header
-------------------------- */
```

##### Tabs and indent style

Use two space indents and maintain it properly in the entire codebase.

#### Write multi-line CSS unless it's just only a single line of code

Ex-
```
.alert {
  border: 1px solid #ccc;
  padding: 5px 10px;
  font-size: 10px;
  display: block;
}

.alert__error { color: red; }
```

##### Avoid uses of `!important` as possible

The one of the best practices of CSS in a larger codebase is avoid uses of `!imporatnt` as possible.

##### Test/temporarily styles

Put an additional tab indent for a test/temporarily added styles.

Ex-
```
.alert {
  border: 1px solid #ccc;
  padding: 5px 10px;
  font-size: 10px;
  display: block;
    background-color: #eee; // temporarily put here
}
```

##### Disabling style ruled 

Add `x-` prefix for disable style rule without removing entirely. 

Ex-
```
.alert {
  border: 1px solid #ccc;
  padding: 5px 10px;
  font-size: 10px;
  x-display: block; // disabled
}
```

##### Keep all the style rules in alphabetical order

Ex-
```
.alert {
    background-color: #eee; // temporarily put here
  border: 1px solid #ccc;
  display: block;
  font-size: 10px;
  padding: 5px 10px;
}

.box {
  top:    0;
  right:  0;
  bottom: 0;
  left:   0;
}
```

#### Avoid batch styling and use classes instead;

Ex-
```
// Incorrect:
div#a, dv#b {}

// Correct:
.ab {}
```

##### Always try to write styles in simplified and minified ways as possible

Ex-
```
// Incorrect:
#sidebar {
  background-color: #fff;
  background-image: (bg.png);
  background-position: 0 0;
}

// Correct:
#sidebar {
  background: #fff url(bg.png) repeat-x 0 0;
}
```

##### Use a clearfix class to clearing `float`

```
.clearfix {
  clear: both;
}
```

#### Naming conventions

##### Use a specific prefix for each of custom css rules to prevent any possible complication may happen with third-party css libraries

Ex-
```
.ig-container {}
.ig-alerts {}
```

##### Use lowercase letters in all the style rules

##### Use `-` instead of `_`

##### Keep selector (id/class) names short and meaningful as possible

##### Use `ids` and `classes` as relevant always

Ex-
```
// Incorrect
<ul id="list-1"></ul>
<ul id="list-2"></ul>
<img class="main-logo" />

#list-1, #list-2 {}
.main-logo {}

// Correct:
<ul class="list" id="list-1"></ul>
<ul class="list" id="list-2"></ul>
<img id="main-logo" />

.list {}
#main-logo {}

```

##### Always follow the semantic naming for html elements and styles

Ex-
```
// Incorrect:
<div class="article">
  <div class="title">Title</div>
  <div class="content">Article contents goes here!</div>
</div>

.article {}
.article .title {}
.article .content {}

// Correct:
<article>
  <h1>Title</h1>

  <p>Article contents goes here!</p>

  <ul>
    <li>list item</li>
  </ul>
</article>

article {}
article > h1 {}
article > p {}
article > ul {}
```

##### BEM like naming convention for css rules

Ex-
```
.alerts // block
.alerts__error // element
.alerts--show // state
```

This just a draft for a better styleguide implementation can use for scalable web projects.

## References
* [Structuring CSS in large projects](https://medium.com/peergrade-io/structuring-css-in-large-projects-37f1695f5ec8)
* [Principles of Code Cleanup and the New Best Practices](https://msdn.microsoft.com/en-us/magazine/jj983725.aspx)
* [High-level advice and guidelines for writing sane, manageable, scalable CSS](http://cssguidelin.es/)
* [BEM and SMACSS: Advice From Developers Who’ve Been There](https://www.sitepoint.com/bem-smacss-advice-from-developers/)
* [A Look at Some CSS Methodologies](http://sixrevisions.com/css/css-methodologies/)
* and more..

@created-at 23rd Feb 2017 | @last-update 24th Feb 2017

