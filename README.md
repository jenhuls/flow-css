# CSS Styleguide Proposal

### Objective

* Structuring CSS in large web projects
* Keep code transparent, sane, and readable
* Keep styles/stylesheets maintainable
* Keep code scalable

### Guidelines

#### Use latest CSS versions and related technologies when possible

The current CSS version is CSS3 and there are two commonly used CSS preprocessors: `LESS` and `SASS`.

##### Always `Minify`, `Transpile` the CSS code as needed

Use `Gulp`, `Webpack` or any other task-runner/module bundler to automate the process.

#### File / Directory structure

There is no right or wrong way to structure the CSS files, but keeping them organized in a modular manner is the best way to manage a large project.

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

Here, we keep all the third-party CSS libraries (if any) in `vendor/` directory, and `SASS` files in `sass/` directory divided into separate modules. Finally, the transpiled-minified version of all, outputs to `final.css`.

#### Code styles

##### Put stylesheet information in top of the each CSS file

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
    - Ind
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

#### Write multi-line CSS unless it’s just only a single line of code

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

##### Avoid uses of `!important` when possible

One of the best practices of CSS in a larger codebase is avoid uses of `!imporatnt` when possible.

##### Adding test/temporary styles

Put an additional tab indent for a test/temporarily added style(s).

Ex-
```
.alert {
  border: 1px solid #ccc;
  padding: 5px 10px;
  font-size: 10px;
  display: block;
    background-color: #eee; /* temporarily put here */
}
```

##### Disabling style rules

Add `x-` prefix to disable a style rule without removing it entirely. 

Ex-
```
.alert {
  border: 1px solid #ccc;
  padding: 5px 10px;
  font-size: 10px;
  x-display: block; /* disabled */
}
```

##### Keep all the style rules in alphabetical order

Ex-
```
.alert {
    background-color: #eee; /* temporarily put here */
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

#### Avoid batch styling and use classes instead

Ex-
```
// Incorrect:
div#a, dv#b {}

// Correct:
.ab {}
```

##### Always try to write styles in __simplified__ and __minified__ ways as possible

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

##### Use a specific prefix for each of the custom CSS rules to prevent any possible complication that may happen with third-party CSS libraries

Ex-
```
.kf-container {}
.kf-alerts {}
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

##### Always follow the semantic naming for HTML elements and styles

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

##### BEM-like naming convention for CSS rules

Ex-
```
.alerts {} /* block */
.alerts__error {} /* element */
.alerts--show {} /* state */
```

This a basic draft for a better styleguide implementation for web projects focusing on scalability and maintainability.

## References
* [Structuring CSS in large projects](https://medium.com/peergrade-io/structuring-css-in-large-projects-37f1695f5ec8)
* [Principles of Code Cleanup and the New Best Practices](https://msdn.microsoft.com/en-us/magazine/jj983725.aspx)
* [High-level advice and guidelines for writing sane, manageable, scalable CSS](http://cssguidelin.es/)
* [BEM and SMACSS: Advice From Developers Who’ve Been There](https://www.sitepoint.com/bem-smacss-advice-from-developers/)
* [A Look at Some CSS Methodologies](http://sixrevisions.com/css/css-methodologies/)


