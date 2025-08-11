---
layout: page
title: Preface Pattern
parent: Design Patterns
nav_order: 9
redirect_from:
  - /front_end_coding/patterns/preface
---
# Preface Pattern
{: .no_toc}

Preface groups together user notes about a work, collection, or challenge. Items that are grouped in preface include: summary, notes, end notes, FAQ, rules, about, description. On a work page, preface is inside `#workskin`, so it can be styled in work skins as well as site skins.

The preface style is declared in [14-group-preface.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/14-group-preface.css).

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Rules

A preface can be any block containing a child that can contain these blocks: `h1—6`, `p`, `div`, `ul`, `ol`, `dl`, `blockquote`. Normally it's a `div`.

A preface always contains a `blockquote.userstuff`, although the `blockquote` may be logicked out (e.g. if a work doesn't have a summary or note but does have associations).

A preface can have lots of child modules. You can have a preface with restricted children: `table.preface`, `ol`, `ul`, or `dl.preface`, so long as the block children are given the `module` class.

You can never have an inline preface, or a phrase element preface.

## Quick reference

<dl class="key"><dt>[...]</dt><dd>always included</dd>
<dt>{...}</dt><dd>sometimes included</dd></dl>

<pre>
[preface]
  {title heading} {byline heading}
  [block module]
    [heading] {span actions} [/heading]
    [blockquote userstuff]
    {p note} {ul actions}
  [block module]
[/preface]
</pre>

## HTML diagram

This diagram is taken from a challenge profile.

<div class="diagram">
  <ol>
    <li><code>&lt;div class="preface group"&gt;</code>
      <ol>
        <li><code>&lt;div id="intro" class="module"&gt;</code>
          <ol>
            <li><code>&lt;h3 class="landmark heading"&gt;</code></li>
            <li><code>&lt;ul class="actions"&gt;</code>
              <ol>
                <li><code>&lt;li&gt;</code>
                  <ol>
                    <li><code>&lt;a&gt;</code></li>
                  </ol>
                </li>
                <li><code>&lt;li&gt;</code></li>
              </ol>
            </li>
            <li><code>&lt;h3 class="heading"&gt;</code></li>
            <li><code>&lt;blockquote class="userstuff"&gt;</code></li>
          </ol>
        </li>
        <li><code>&lt;div id="faq" class="module"&gt;</code>
          <ol>
            <li><code>&lt;h3 class="landmark heading"&gt;</code></li>
            <li><code>&lt;ul class="actions"&gt;</code></li>
            <li><code>&lt;h3 class="heading"&gt;</code></li>
            <li><code>&lt;blockquote class="userstuff"&gt;</code></li>
          </ol>        
        </li>
        <li><code>&lt;div id="rules" class="module"&gt;</code></li>
      </ol>
    </li>
  </ol>
</div>
