---
layout: page
title: CSS
parent: HTML & CSS Basics
nav_order: 2
---
# CSS
{: .no_toc }

Cascading Stylesheets (<abbr>CSS<abbr>) tell a browser how to display our HTML document. We write a list of rules describing the color of the text, the size of the boxes -- what goes where and what it looks like.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Concepts

To write a CSS document, conceptually, we examine the structure of an HTML document:

```html
  <body>
    <div id="header">
      <h1>My Page Title</h1>
      <ul class="navigation">
        <li> <a href="...">site section one</a> </li>
        <li> <a href="...">site section two</a> </li>
      </ul>
    </div>
    <div id="main">
      <p>My content goes here</p>
      <span class="navigation"> <a href="...">home</a> </span>
    </div>
    <div id="footer">
      <p>My page by me!</p>
    </div>
</body>
```

...and then we lay out our CSS document in the same order: 


```css
body { 
  property: value;
}

#header {
  property: value;
}

#header h1 { 
  property: value;
}

ul.navigation { 
  property: value;
}

#main { 
  property: value;
}

#main p { 
  property: value;
}

#footer { 
  property: value;
}
```

HTML documents are like Tupperware on a shelf: boxes nested inside each other. Everything **nested** inside the body tag **inherits** the properties and values assigned to body, unless you say different. Everything inside `#main` inherits the properties of `body` and `#main`, and so on. CSS then, cascades down the page, sort of like champagne filling a pyramid of glasses.

## Terms

A single CSS **ruleset** is made up of the following parts:

```css
selector { 
  property: value;
}
```

A property must always be paired with a value to form a valid **declaration**. A single ruleset can have multiple selectors separated by commas or multiple declarations separated by semi-colons.

### Selectors

A **selector** is the part of the rule that says which elements are being styled. A rule set can have multiple selectors to make it apply to multiple elements, and different types of selectors can be combined in order to select an element only when it appears within a specific context.

#### ID selectors

Some elements that are used only once per page have unique names that are given to them with the HTML `id` attribute, like `<div id="header">`. To select an element by its `id`, use a hash sign in front of the element's `id` value.

```css
#header {
  property: value;
}
```

#### Class selectors

For something used more than once, we may assign a class, or many classes. A class says this is a type, not a unique thing. Our example HTML has both `<ul class="navigation">` and `<span class="navigation">`. We could target both of those elements at once using their shared `class` value. 

To select elements by a `class` attribute, use a period in front of the desired `class` value.

```css
.navigation {
  property: value;
}
```

#### Type selectors

Type selectors apply a style to a type of HTML element. To select all elements that are a certain type, use the element name as the selector.

```css
p {
  property: value;
}
```

#### Other selectors

We use class and type selectors the most often, but there are some other kinds of selectors you should also get to know:

* [Attribute selectors](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Attribute_selectors)
* [Pseudo-class and pseudo-element selectors](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Pseudo_classes_and_elements#what_is_a_pseudo-element)


#### Using selectors

Looking again at the example HTML and CSS documents, notice that the selector in a style rule is actually a *path*. You can select every paragraph everywhere using just a type selector:

```css
p { 
  property: value;
}
```

You can also specify only certain paragraphs, in certain places, by combining different kinds of selectors using [combinators](https://www.w3schools.com/cssref/css_ref_combinators.php):

```css
#footer p {
  property: value;
}
```

The space that separates `#footer` from `p` is called a descendant combinator. It allows us to select *only* paragraph elements that are located somewhere inside `#footer`.

### Properties

A property is the part of declaration that says which characteristic of the selector you want to style, such as the font family and size of a paragraph or the background color of your site footer:

```css
p {
  font-family: value;
  font-size: value;
}

#body #footer {
  background-color: value;
}
```

#### Shorthand properties

Instead of writing separate declarations to control both the font family and font size, we can use the `font` shorthand property to adjust multiple related characteristics with one declaration:

```css
p {
  font: font-size-value font-family-value;
}
```

Shorthand is efficient and we use a lot of it.

### Values

Finally, a [value](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Values_and_Units) is the part of the declaration that specifies what style to use for the given property. Values come in many forms and include things like font names, measurements, and colors:

```css
p {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1em;
}

#body #footer {
  background-color: #900;
}
```

Values can even be [variables](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_cascading_variables/Using_CSS_custom_properties) or [functions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Values_and_Units/CSS_Value_Functions).

The possible values are different for each property, so it's a good idea to use a reference like [MDN's list of properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Properties#alphabetical_index_of_properties). Each property has a page that provides details about its allowed values.

For shorthand properties, the order of values is important, and some values may be required while others are optional. Again, a reference like [MDN's list of shorthand properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_cascade/Shorthand_properties#shorthand_properties) can be useful.


## Resources

* [CSS at MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS)
* [W3C CSS Validator](https://jigsaw.w3.org/css-validator/)
