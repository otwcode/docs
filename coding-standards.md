---
layout: page
title: Coding Standards
nav_order: 3
---
# Coding Standards
{: .no_toc }

This is a guide to the specifications and formatting standards used in our front end code, which involves a CSS cascade and a consistent HTML framework used across many of our pages. Our standards help us write code that is as accessible and easily maintainable as possible, so if you're committing code, please make sure it follows these standards.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## HTML specifications

Prior to 2016, our pages were written in [XHTML 1.0](http://www.w3.org/TR/xhtml1/) (Strict), which is a cleaner, stricter version of HTML that separates content from presentation. Our pages used `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">` as their `DOCTYPE` declaration.

While the Archive now uses HTML5, we still follow the same standards we used when writing in XHTML 1.0 (Strict):

* All markup must be written in lowercase
* All tags must be closed
  * Empty tags are closed within the tag, e.g. `<br />`
  * Non-empty tags have a corresponding closing tag, e.g. `<p>This is a paragraph.</p>`
* All tags must be properly nested
* [Deprecated elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements#obsolete_and_deprecated_elements) must be avoided

We recommend checking your work with [the W3C Markup Validation Service](https://validator.w3.org) to catch any mistakes.

### Content-type/charset

The Archive uses the UTF-8 character set: `<meta charset="utf-8" />`

### Frequently used fragments

There are some patterns that appear in many places throughout the Archive. There are diagrams of some of these recurring patterns available in our [Patterns Index](/patterns).

### HTML identifiers

Identifiers are attributes that add meaning to an HTML element by providing more information about the element's function. Identifiers come in two varieties, `class` and `id`. An element can have one, both, or neither type of identifier.

#### IDs

The `id` identifier assigns a name to an element. The name can only be used once per document, and each element can only have one `id`.

Stylesheets, scripts, and user agents can referece an element by its `id`. An `id` can also serve as an anchor in a hyperlink or as a name for a declared `object` element.

#### Classes

A `class` identifier assigns a name to an element, but `class` names can be used multiple times per document and any element can have multiple `class` names, with each name separated by a single space: `<div class="preface group">This div has the names group and preface.</div>`.

#### Our identifier naming conventions

Class names should be short, lowercase English (U.S.) words in common usage. They should describe the function, not presentation, of the element to which they are applied. There is more information available in the [Classes documentation](classes).

An `id` name can and should be more complex to ensure that it only appears once per document. We use underscores or hyphens to separate the words and numbers in the `id`: `<form id="work-filters">` or `<li id="work_1234">`. We generally prefer hyphens for separating words.

## CSS specifications

Our default style uses aproximately 30 external stylesheets written primarily to [CSS 2.1 Specifications](https://www.w3.org/TR/CSS2/), although we do permit the use of CSS3 to provide non-essential formatting frills, such as box shadows, text shadows, and gradients. We do not use inline styles.

We only use CSS properties that are supported by our skin system. This ensures our styles can be overridden in both official and user-created skins. You can find our supported properties listed in [our config file](https://github.com/otwcode/otwarchive/blob/master/config/config.yml) under `SUPPORTED_CSS_SHORTHAND_PROPERTIES` and `SUPPORTED_CSS_PROPERTIES`.

Before submitting any code, it is always a good idea to check your CSS with [the W3C CSS validation service](https://jigsaw.w3.org/css-validator/).

### Units of measurement

Since Archive users and visitors browse the site with a variety of technologies, needs, and settings, we want our layout to be as flexible as possible. Using the right units of measurement in the right context helps us accomplish that.

#### Screen

We use relative measurements to specify all text and most element sizes on our screen layout.

We set our text size using [ems](em-scale) and unitless line height. We also use ems to set padding, margins, and widths and heights for other elements.

However, there are times when using an absolute measurement is the best option. For example, we use pixels in instances where an element's `margin` is dependent on the size of an image (e.g., on top of collection profiles).

#### Print

We have a separate stylesheet that controls the appearance of pages printed from the Archive. Text in our print stylesheet is sized using points.

### CSS formatting conventions

Since our stylesheets are edited by multiple coders, we have developed a house style that will allow us to easily read, track changes to, and avoid mistakes in our styles.

A ruleset written for the default Archive style should be formatted with:

* Muliple selectors on the same line, separated by a comma and a single space
  * When writing rulesets for official site skins, each selector is placed on a separate line
* The opening curly brace on the same line as the selector, preceded by a single space
* Each property indented and on a new line  
  * CSS 2.1 properties indented by two spaces
  * CSS3 properties listed last and indented by four spaces
* A space between the colon and the property value
* A semicolon at the end of each property, including the last one
* The closing curly brace on a new line, not indented
* A single blank line after each declaration block
* A zero preceding any decimal value that is less than 1 (e.g. `0.643em`)
* A space after each comma

Here is an example:

```css
#header ul.primary {
  float: none;
  margin: auto;
  background: #900 url(/images/skins/textures/tiles/red-ao3.png);
  border-bottom: 2px solid #700;
  padding: 0.25em 120px;
    box-shadow: inset 0 -5px 10px rgba(0, 0, 0, 0.5);
}
    
#header .primary a, #header .primary .current, #header .primary input, #header .search input {
  border-color: #a00;
  border-bottom-color: #400;
}
```

#### Combining selectors

In our stylesheets, we only combine selectors within a [supertype class](classes-taxonomy#supertypes) section. We don't use streamlining software to find and combine all selectors with the same rules. This makes code really hard to maintain, and can destroy a complex cascade design, so make sure you don't ever do this.
