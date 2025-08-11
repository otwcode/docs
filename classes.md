---
layout: page
title: Classes
parent: Front End Guide
nav_order: 2
---
# Classes
{: .no_toc }

Classes are used to add structural meaning. A good class describes more specifically the function of the element to which it is applied, while a bad class describes what the CSS does. (You may know these bad classes as "utility classes.") A bad class is something like `red` ; a good class is something like `warning`. (Imagine that you were creating a skin for people with red-green color blindness, and you wanted to change the appearance of words using the class `red` to be the color blue! That would be very confusing and therefore harder to maintain.)

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Rules

* Classes are general and written in English (U.S). Ideally, they are short words in common usage.
* Classes describe en element's function, not presentation.
* Do **not** give every element on every page a unique class. Classes are inherited from their parent element and can be combined together to style elements uniquely.
* Do **not** give elements very specific names.
* Classes are listed from the most specific to the least, e.g. `work blurb group` or `unread comment group`.

If you find yourself combining several words to make a class, like `unsubscribe-button`, stop and think whether you could use two more general classes: `unsubscribe button`. Then consider if any of those classes are redundant. For example, the `button` class would be unnecessary on `<button class="unsubscribe button">` since the element is a button.

You should only write the class on the highest element it applies to on each level. All the elements nested inside this parent will inherit its properties anyway, and otherwise you could end up double-applying the attributes of that class to the nested elements.

Our classes are how we describe and document our data, so it's very important to use them consistently and accurately. If you find a class that doesn't fit this system, it's probably a mistake and needs fixing. The main exceptions are:

* [classes added by Rails](#rails-classes)
* classes used by jQuery plugins, since it is easier to keep plugins up to date if we *don't* modify the class names
* classes used by our own JavaScript, although classes that follow our naming system are strongly preferred
* classes used on [blurbs](/patterns/blurb) to allow muting (e.g., `work-000` and `user-000`), which are also listed last for neatness

## "What kind and where?"

It might be useful to look at some [diagrams of pages](/patterns) on our Archive to really understand that in CSS, we write a path *to* places in our HTML; we don't need to give everything a unique name, because we describe it: "what kind and where".

For example, we use a dotted line to underline all tag links: `a.tag { border-bottom: 1px dotted; }`. If we want to change how tag links look on bookmark blurbs, we don't add a new `bookmark-tag` class in the HTML -- we just use the bookmark tags' unique path in the DOM: `.bookmark a.tag { border-bottom: none; }`

## Rails classes

Rails automatically generates a unique class on `<div id="main">` on each page, named by the view partial that `div` calls. This means that each page can have rules set independently, which is very useful for tweaking the layout, but should not be used as a core technique.

* The [Media Index](https://archiveofourown.org/media) has the Rails class `media-index`.
* The [works index for testy](https://archiveofourown.org/users/testy/works) has the Rails class `works-index`, and we also tell Rails to automatically add `dashboard` and `filtered` to the page because it contains dashboard navigation and filters.
