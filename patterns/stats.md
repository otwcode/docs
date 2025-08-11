---
layout: page
title: Stats Pattern
parent: Design Patterns
nav_order: 5
redirect_from:
  - /front_end_coding/patterns/stats
---
# Stats Pattern
{: .no_toc }

Stats are a list of paired properties and values that we use at the end of [meta](/meta), [blurbs](/blurb), and similar descriptive blocks. They are usually countable values (e.g., Hits: 100) or some kind of binary status (e.g., Status: Complete).

The stats style is declared in [10-types-groups.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/10-types-groups.css).

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Rules

Stats are always a `dl.stats`. You can never have any other kind of stats.

Stats always come at the end of meta and work blurbs. Stats may also appear in other contexts. 

`dl.stats` _may_ appear within a `dd.stats`, but it can't be depended on. Blurbs do _not_ use that structure, but meta does.

Property and value pairs may be given matching class names. Never give a class to the property and not the value (or vice verse).

## Quick reference

<dl class="key"><dt>[...]</dt><dd>always included</dd>
<dt>{...}</dt><dd>sometimes included</dd></dl>

<pre>
[dl stats]
  [dt][/dt]
  [dd][/dd]
[/dl]
</pre>

## HTML diagram

This diagram is taken from work meta.

<div class="diagram">
  <ol>
    <li><code>&lt;dl class="work meta group"&gt;</code>
      <ol>
        <li><code>&lt;dt...</code></li>
        <li><code>&lt;dd...</code></li>
        <li><code>&lt;dt class="stats"&gt;</code></li>
        <li><code>&lt;dd class="stats"&gt;</code>
          <ol>
            <li class="emphasize"><code>&lt;dl class="stats"&gt;</code>
              <ol>
                <li><code>&lt;dt class="published"&gt;</code></li>
                <li><code>&lt;dd class="published"&gt;</code></li>
                <li><code>&lt;dt class="words"&gt;</code></li>
                <li><code>&lt;dd class="words"&gt;</code></li>
                <li><code>&lt;dt class="chapters"&gt;</code></li>
                <li><code>&lt;dd class="chapters"&gt;</code></li>
                <li><code>&lt;dt class="comments"&gt;</code></li>
                <li><code>&lt;dd class="comments"&gt;</code></li>
                <li><code>&lt;dt class="kudos"&gt;</code></li>
                <li><code>&lt;dd class="kudos"&gt;</code></li>
                <li><code>&lt;dt class="hits"&gt;</code></li>
                <li><code>&lt;dd class="hits"&gt;</code></li>
              </ol>
            </li>
          </ol>
        </li>
      </ol>
    </li>
  </ol>
</div>
