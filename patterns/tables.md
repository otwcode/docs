---
layout: page
title: Tables
parent: Design Patterns
redirect_from:
  - /front_end_coding/accessible-tables
---
# Tables
{: .no_toc }

Tables aren't unique to us, and we don't use many in the Archive, but it's important to know how to write them well. A table is the right way to mark up three or more pieces of information in a matrix for cross referencing. It is not the right way to do anything else.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Structure

The following is an example of a table that might appear inside a form, which is a design pattern frequently found in the tag wrangling and admin areas of the Archive. Whether or not a table appears in a form, it should be structured in a similar way. Note that the header (`<thead>`) and footer (`<tfoot>`) are at the top of the table, below the caption (`<caption>`) and above the body (`<tbody>`).

```html
<table summary="Explain what the table does, list the data types it shows, and what you can do with them">
  <caption>Ten words or fewer!</caption>
  <thead>
    <tr>
      <th scope="col">Heading</th>
      <th scope="col">Heading</th>
      <th scope="col">Heading</th>
    </tr>
    </thead>
    <tfoot>
    <tr>
      <th scope="row" colspan="2">Whole table operator</th>
      <td><input type="submit"></td>
    </tr>
    </tfoot>
    <tbody>
    <tr>
      <th scope="row">Row Heading</th>
      <td>Value</td>
      <td>Value</td>
    </tr>
  </tbody>
</table>
```

## Some elements and attributes in detail

* Each table should have a `summary` attribute in the `<table>` tag, and its value should be a brief description of what the table does or what data it displays. For example, the summary on [the sign-up table for the Yuletide 2012 gift exchange challenge](http://archiveofourown.org/collections/yuletide2012/signups/summary) says, "Number of requests and offers for each requested fandom in this challenge, listed by fewest offers and most requests."

    Table summaries are not visible on the page, but they are useful to users of screen readers.

* `<caption>` *is* normally visible on the page, but we use CSS to hide captions by default. A caption should be really *short* and written in *simple* language. You can copy from the `.landmark` heading if there is one in the view already.

    Captions can be very useful to people with cognitive disabilities, and people browsing on small screens and phones, amongst others.

* Group your main headings in a `<thead>`. You can have multiple rows (`<tr>`) in a thead, so you can further group your headings in more complicated tables.
Never leave the first cell in your thead empty; it should always be a `<th>` scoped to the column. Leaving the cell empty causes problems for users of some screen readers.

* All `<th>` elements should have a `scope` attribute to tell user agents which heading relates to which part of the table. It's obvious when you *look* at a table that the bold word above or beside a normal weight word is the heading for that column or row, but it's not always obvious to a screen reader. Some user agents announce the relevant headings before every `<td>`, which can really help non-visual spatial navigation.

   Generally, if the `<th>` is in the table head, it will have a `scope` of `col`; a `<th>` in the table foot or body will usually have a `scope` of `row`.

* The `<tfoot>` comes before the body! This is so, for a really long table, a user agent can print the head and foot to the page and then scroll or paginate the body, and possibly progressively load it.

    You don't always need a tfoot, but if you have a "check all" or a final "submit" table row in a form, this is where those things should go.

* `<tbody>` is where the main content of your table lives; it's probably where you're used to a table beginning if you've used tables before, but for us it comes a way down the markup.

## Things to remember

* We don't ever use tables just for layout.

* If a table just shows two kinds of data, or "paired" data, it's probably a definition list masquerading as a table and should be rewritten. Most of our user-facing forms are definition lists.

* If a table is gigantic and filled with loads of things listed in a row stretching off the screen, like, name, date, tags, summary, user actions, it's a blurb confused about itself and should be rewritten.

* If you can't read and understand what a table does in the markup, it's probably confusing and inaccessible to a user. Fix it!

* If you want to check your work against some real examples, there are lots of tables in the admin views; a lot of admin work is managing tabular data.

## Resources

* [Accessible Data Tables](http://www.usability.com.au/resources/tables.cfm)
* [Building Accessible Websites by Joe Clark: Tables and frames](http://joeclark.org/book/sashay/serialization/Chapter10.html)
* [W3C Tables in HTML Documents](http://www.w3.org/TR/html4/struct/tables.html)
* [WebAIM: Creating Accessible Tables - Data Tables](http://webaim.org/techniques/tables/data)

