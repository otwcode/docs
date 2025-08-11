---
layout: page
title: Comments Pattern
parent: Design Patterns
nav_order: 10
redirect_from:
  - /front_end_coding/patterns/comments
---
# Comments Pattern
{: .no_toc }

Comments group together information about the commenter, information about the item the comment refers to, the comment itself, and actions pertaining to the comment.

The comment style is declared in [15-group-comments.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/15-group-comments.css). Comment is part of the group [supertype](../classes-taxonomy#supertypes)

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Rules

An individual comment is always a `li` contained within an `ol`. These comment lists, or threads, may be nested. Comments are given the class `even` or `odd`.

## Quick reference

<dl class="key"><dt>[...]</dt><dd>always included</dd>
<dt>{...}</dt><dd>sometimes included</dd></dl>

<pre>
[ol thread]
  [li odd comment group]
    [byline heading] {a} [span datetime] [/heading]
    [div icon] {a} {img} {/a} [/div]
    [blockquote userstuff]
    {p datetime}
    {landmark heading}
    {ul actions}
  [/li]
[/ol]
</pre>

## HTML diagrams

### Single comment

<div class="diagram">
  <ol>
    <li><code>&lt;li class="odd comment group user-123" id="comment_456"&gt;</code>
      <ol>
        <li><code>&lt;h4 class="byline heading"&gt;</code>
          <ol>
            <li><code>&lt;a&gt;</code></li>
            <li><code>&lt;span class="posted datetime"&gt;</code></li>
          </ol>
        </li>
        <li><code>&lt;div class="icon"&gt;</code>
          <ol>
            <li><code>&lt;a&gt;</code>
              <ol>
                <li><code>&lt;img class="icon"&gt;</code></li>
              </ol>
            </li>
          </ol>
        </li>
        <li><code>&lt;blockquote class="userstuff"&gt;</code></li>
        <li><code>&lt;p class="edited datetime"&gt;</code></li>
        <li><code>&lt;h5 class="landmark heading"&gt;</code></li>
        <li><code>&lt;ul class="actions"&gt;</code></li>
      </ol>
    </li>
  </ol>
</div>

### Threads

To illustrate the HTML for threads, we'll diagram the following example. Each `li` with the `comment` class contains the HTML diagramed in the previous section.

![Two top-level comments, with two direct reples to the second top-level comment. The second reply also has a reply.](/images/comment_thread_for_diagram.png)

<div class="diagram">
  <ol>
    <li><code>&lt;ol class="thread"&gt;</code>
      <ol>
        <li><code>&lt;li class="odd comment group"&gt;</code></li>
        <li><code>&lt;li class="even comment group"&gt;</code></li>
        <li><code>&lt;li&gt;</code>
          <ol>
            <li><code>&lt;ol class="thread"&gt;</code>
              <ol>
                <li><code>&lt;li class="even comment group"...</code></li>
                <li><code>&lt;li class="odd comment group"...</code></li>
                <li><code>&lt;li&gt;</code>
                  <ol>
                    <li><code>&lt;ol class="thread"&gt;</code>
                      <ol>
                        <li><code>&lt;li class="even comment group"...</code></li>
                      </ol>
                    </li>
                  </ol>
                </li>
              </ol>
            </li>
          </ol>        
        </li>
      </ol>
    </li>
  </ol>
</div>
