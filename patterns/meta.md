---
layout: page
title: Meta Pattern
parent: Design Patterns
nav_order: 7
redirect_from:
  - /front_end_coding/patterns/meta
---
# Meta Pattern
{: .no_toc}

Meta is a definition list inside a wrapper div. We use meta in places such as the start of a work, a series listing, or a user profile. It shows metadata: all the tags, associations, and stats we hold on that object. Sometimes it includes a brief note, but normally it's tags and stats and status type data.

Meta is part of the group [supertype](../classes-taxonomy#supertypes) and is styled in [12-group-meta.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/12-group-meta.css).

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Rules

Meta is one of our simplest design patterns and has few rules.

* Meta is always a definition list (`<dl>`)
* Meta is always wrapped in `<div class="wrapper">`

The child `<dd>` elements may contain anything, but they normally contain dates and times, lists of tags, lists of mods or owners or other associations like Part X of Series Y, and a stats block (which *always* comes at the end!).

## Quick reference

<dl class="key"><dt>[...]</dt><dd>always included</dd>
<dt>{...}</dt><dd>sometimes included</dd></dl>

<pre>
[div wrapper]
  [dl meta]
    [dt {tag class}]
    [dd] {ul tags} [/dd]
    [dt]
    [dd] {blockquote userstuff} [/dd]
    {dt stats}
    {dd stats} [dl stats] [dt] [dd] [/dl] {/dd}
  [/dl]
[/wrapper]
</pre>

## HTML diagram

The work header is the most familiar example of the meta pattern.

<div class="diagram">
  <ol>
    <li>&lt;div class="wrapper"&gt;
      <ol>
        <li>&lt;dl class="work meta group"&gt;
          <ol>
            <li>&lt;dt class="rating tags"&gt;</li>
            <li>&lt;dd class="rating tags"&gt;</li>
            <li>&lt;dt class="warning tags"&gt;</li>
            <li>&lt;dd class="warning tags"&gt;</li>
            <li>...</li>
            <li>&lt;dt class="stats"&gt;</li>
            <li>&lt;dd class="stats"&gt;
              <ol>
                <li>&lt;dl class="stats"&gt;
                  <ol>
                    <li>...</li>
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
