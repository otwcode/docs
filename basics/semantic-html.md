---
layout: page
title: Semantic HTML
parent: HTML & CSS Basics
nav_order: 1
---
# Semantic HTML
{: .no_toc }

In our [Coding Standards](../coding-standards), we say that with semantic <abbr title="HyperText Markup Language">HTML</abbr> and <abbr title="Cascading Style Sheets">CSS</abbr> we separate our content from our presentation. HyperText Markup Language and Cascading Style Sheets are flexible, accessible, and logical ways to mark up content for the web.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## "Code what you mean; mean what you code."

The combination of CSS and HTML separates style from content: the way things **look** from what things **mean**. CSS takes care of how everything looks; HTML controls what things mean. In this way, you can build consistent, logical documents that can be read on any device, by any user agent, whether that's a screen reader, a smart phone, a printer, or whatever the *next* gadget might be.

It's faster and easier to code correctly because there is a process of reasoning that you can follow. Instead of saying, "Oh, this is a book title, so it should be `<u>underlined</u>` or written in `<i>italics</i>`," you can just say, "Oh, this is `<cite>A Book Title</cite>`."

We do this because, while people can use context to understand why text has been italicized, computers can't understand that `<i>this</i>` word is emphasised but `<i>The Lord of the Rings</i>` is a book. You have to tell them that `<em>this</em>` word is emphasised and `<cite>The Lord of the Rings</cite>` is a book.

## But it looks bad!

Once your content is marked up in a consistent, semantic, and logical manner, you can go wild with your presentational CSS. You can change the way your entire site looks by changing a single line in a single document. 

Returning to the example of book titles, if you used `<i>italics</i>` and later decided you would prefer to have the titles `<u>underlined</u>`, you would have to go through and replace all the `<i>` tags around book titles with `<u>` tags. This becomes particularly tricky if you have also used `<i>italics</i>` in place of `<em>emphasis</em>`. However, if you used semantic HTML with `<cite>` and `<em>` tags, you could change the formatting of all book titles with just one line of CSS: `cite { text-decoration: underline; }`.

## Resources

* [HTML elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements)
  * [Obsolete and deprecated elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements#obsolete_and_deprecated_elements)
* [Content categories of elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)
