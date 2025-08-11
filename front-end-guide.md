---
layout: page
title: Front End Guide
nav_order: 5
redirect_from:
  - /front_end_coding/front-end-user-guide
---
# Front End Guide

The pages in this section provide a detailed guide to the front end code, focusing on the stylesheets and classes.

{: .note-title }
> A note on style
>
> It is not necessary or desirable for the Archive to look identical in every browser. Pixel precison is not a reasonable or desirable goal because our layout is designed to be flexible and adaptable, so it will work on devices long forgotten and in contexts not yet conceived.
>
> When adding styles, remember that keeping the code simple and easy to maintain is a priority.


## Our philosophy

The AO3 front end, which is [HTML](/basics/semantic-html) and [CSS](/basics/css), uses a classification system that might be new to you in some ways, but will be familiar in others.

Rules on the Archive are written in modules, and generally in order from the most general or global rules, that affect the most things on the most pages, to the most specific rules, that move a single element in one context. We continually combine and simplify rules, finding commonalities of purpose behind ways of displaying information, working towards a simple and consistent interface.

To put this another way: in a single stylesheet, classes are laid out so more general classes (`.blurb`, `.index`, `.work`) are modified by more specific classes further down the cascade. Just like a chair can be modified by the adjective hard, a blurb can be modified by the class collection.

The core process in all front end design is the naming of things. By really thinking about each element we deal with, and describing it simply and aptly, we create the most *readable* (and therefore flexible, accessible, and maintainable) interface we can. This is true for [CSS classes](classes), for style rules, for bug fixing, for HTML markup, and for page design.
