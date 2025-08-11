---
layout: page
title: Index Pattern
parent: Design Patterns
nav_order: 4
redirect_from:
  - /front_end_coding/patterns/pattern-index
---
# Index Pattern
{: .no_toc}

Index is a very general class of list. You'll most often see it containing blurbs, or as the content in a listbox, but it isn't restricted to those. Index has very few rules; it's a flexible grouping class. 

It doesn't have its own stylesheet, but index styles are declared in [the stylesheet named 10-types-groups.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/10-types-groups.css). Index is part of the group [supertype](../classes-taxonomy#supertypes)

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## HTML structure

An index can be any of the three kinds of HTML list.

1. dl.index
2. ol.index
3. ul.index

You can **never** have **any** other kind of index.

### dl.index

`dl.index` is sometimes used to display simple paired data (e.g. on a [translated news post](https://archiveofourown.org/admin_posts/148)), but it more often functions as a sort of brief alternative to showing a full blurb (or a full list of blurbs).

Instead of displaying a full work blurb on a user's related works or subscriptions page, we use a `dl.index` to provide basic information and options. We do the same instead of displaying each individual request blurb on a user's assignments page.

While it's less work to display these shorter blurbs, users frequently express a preference for more information rather than less, and it is not uncommon for us to switch from an abbreviated `dl.index` to an index with a full `li.blurb`.

#### HTML diagram of dl.index

The following diagram is taken from the assignments page a user can access from their dashboard.

<div class="diagram">
  <ol>
    <li>
      <code>&lt;dl class="assignment index group"&gt;</code>
      <ol>
        <li>
          <code>&lt;dt&gt;</code>
          <ol>
            <li>
              <code>&lt;a&gt;Assignment link</code>
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;dd&gt;</code>
          <ol>
            <li>
              <code>&lt;ul class="actions"&gt;</code>
              <ol>
                <li>
                  <code>&lt;li&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;a&gt;Fulfill</code>
                    </li>
                  </ol>
                </li>
                <li>
                  <code>&lt;li&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;a&gt;Default</code>
                    </li>
                  </ol>
                </li>
              </ol>
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;dt&gt;</code>
          <ol>
            <li>
              <code>&lt;a&gt;Assignment link</code>
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;dd&gt;</code>
          <ol>
            <li>
              <code>&lt;a&gt;Work link</code>
            </li>
            <li>
              <code>&lt;dl class="stats"&gt;</code>
              <ol>
                <li>
                  <code>&lt;dt&gt;</code>
                </li>
                <li>
                  <code>&lt;dd&gt;</code>
                </li>
              </ol>
            </li>
          </ol>
        </li>
      </ol>
    </li>
  </ol>
</div>

### ol.index and ul.index

Refer to the [Blurb Design Pattern page](blurb) for a [digram of an ol.index](blurb#html-diagram).
