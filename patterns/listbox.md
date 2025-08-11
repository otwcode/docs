---
layout: page
title: Listbox Pattern
parent: Design Patterns
nav_order: 6
redirect_from:
  - /front_end_coding/patterns/listbox
---
# Listbox Pattern
{: .no_toc }

A listbox is a box containing a list. We use listbox to show more than one index on a page. Listboxes can be list items and they can nest, but they don't have to. They can be expandable, draggable, and sortable. You can have a single listbox on a page so long as that page could show multiple indexes with enough user data; they don't need to be logicked out in the view file. For example, the [Yuletide Recs collection](https://archiveofourown.org/collections/yuletide_recs) is a collection that only contains bookmarks, but the bookmark index on the collection index is still a listbox. This is allowed because, if someone added a work to the collection, there would also be a work index on that page.

Listbox styles are declared in [11-group-listbox.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/11-group-listbox.css). Listbox is part of the group [supertype](../classes-taxonomy#supertypes).

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Rules

A listbox can be any block container that can contain these blocks: `h1—6`, `p`, `div`, `ul`, `ol`, `dl`. So this means a listbox could be a:

* `fieldset.listbox`
* `div.listbox`
* `li.listbox`
* `dd.listbox`
* `td.listbox` (not recommended)
* `form.listbox` (not recommended)

You can never have an inline listbox of any kind. You can never have a listbox with restricted children: no `table.listbox`, `ol.listbox`, `ul.listbox`, or `dl.listbox`.

The first element inside a listbox is always a heading, and it always contains an index (i.e., `<ol class="index group">`, `<ul class="index group">`, or `<dl class="index group">`). It might also contain a note (e.g., `<p class="note">`) or actions (e.g., `<p class="actions">`) outside the index.

## Quick reference

<dl class="key"><dt>[...]</dt><dd>always included</dd>
<dt>{...}</dt><dd>sometimes included</dd></dl>

<pre>
[listbox]
  [heading] {span action} [/heading]
  {p note}{/p} {ul actions} {div form}
  [index]
    {listbox}...{/listbox}
  [/index]
  {p note} {ul actions}
[/listbox]
</pre>

## HTML diagram

The following diagram is taken from [an index of fandoms for a specific media type](https://archiveofourown.org/media/Theater/fandoms). It's an example of multiple listboxes within an index.

<div class="diagram">
  <ol>
    <li>
      <code>&lt;ol class="alphabet fandom index group"&gt;</code>
      <ol>
        <li>
          <code>&lt;li class="letter listbox group"&gt;</code>
          <ol>
            <li>
              <code>&lt;h3 class="heading"&gt;A&lt;/h3&gt;</code>
              <ol>
                <li>
                  <code>&lt;span class="action top"&gt;
                    <span>&lt;a&gt;↑&lt;/a&gt;</span>&lt;/span&gt;
                  </code>
                </li>
              </ol>
            </li>
            <li>
              <code>&lt;ul class="tags index group"&gt;</code>
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;li class="letter listbox group"&gt;</code>
          <ol>
            <li>
              <code>&lt;h3 class="heading"...</code>
              <ol>
                <li>
                  <code>&lt;span class="action top"...</code>
                </li>
              </ol>
            </li>
            <li>
              <code>&lt;ul class="tags index group"&gt;</code>
            </li>
          </ol>
        </li>
      </ol>
    </li>
  </ol>
</div>

## Notes

We call it listbox (instead of indexbox) because a listbox might be a dynamically inserted form or form component, and therefore would need managed focus. This seems most closely related to [the ARIA role listbox](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role).

There are currently no listboxes in the codebase with the role listbox.
