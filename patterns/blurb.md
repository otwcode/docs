---
layout: page
title: Blurb Pattern
parent: Design Patterns
nav_order: 8
redirect_from:
  - /front_end_coding/patterns/blurb
---
# Blurb Pattern
{: .no_toc}

A blurb is the small summary box which provides a description of a work, bookmark, collection, user, or series. Blurbs appear on index pages (e.g., the [works index for the Alternate Universe tag](https://archiveofourown.org/tags/Alternate%20Universe/works) or the [bookmarks index for the user testy](https://archiveofourown.org/users/testy/bookmarks)).

The styles for blurbs are located in [the stylesheet named 13-group-blurb.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/13-group-blurb.css). Blurb is part part of the group [supertype](classes-taxonomy#supertypes).

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Structure

The work blurb is the most used chunk of HTML code in the Archive, so we've revised it a lot. It has to contain lots of information and allow different ways of accessing its material. The blurb is flexible, accessible, and has multiple redundancies (says the same thing in different ways).

![Work blurb in the default Archive style](/images/workblurb.png)

Since we usually have many blurbs listed together, the index page that holds the blurbs is coded as an HTML list, and each blurb is coded as a list item. If a page will only ever contain one blurb (e.g., the adult content warning), the blurb can be coded as a different element, such as a `div`.

### HTML diagram

<div class="diagram">
  <ol>
    <li>landmark heading level 3 "list of works" <code>&lt;h3 class="landmark heading"&gt;Listing Works&lt;/h3&gt;</code>
    </li>
    <li>list container work index <code>&lt;ol class="work index group"&gt;</code>
      <ol>
        <li class="emphasize">list item work blurb <code>&lt;li class="work blurb group work-1234 user-000" id="work_1234"&gt;</code>
          <ol>
            <li>division header module <code>&lt;div class="header module"&gt;</code>
              <ol>
                <li>heading level 4 title link by user link <code>&lt;h4 class="heading"&gt;</code></li>
                <li>heading level 5 fandom tag link <code>&lt;h5 class="fandoms heading"&gt;</code></li>
                <li>unordered list of required tags <code>&lt;ul class="required-tags"&gt;</code>
                  <ol>
                    <li>list item with rating symbol<code>&lt;li&gt;...&lt;span class="rating...</code></li>
                    <li>list item with warnings symbol<code>&lt;li&gt;...&lt;span class="warnings...</code></li>
                    <li>list item with category symbol<code>&lt;li&gt;...&lt;span class="category...</code></li>
                    <li>list item with work status symbol<code>&lt;li&gt;...&lt;span class="iswip...</code></li>
                  </ol>
                </li>
                <li>paragraph datetime <code>&lt;p class="datetime"&gt;</code></li>
              </ol>
            </li>
            <li>landmark heading level 6 "tags" <code>&lt;h6 class="landmark heading"&gt;Tags&lt;/h6&gt;</code></li>
            <li>unordered list of tags <code>&lt;ul class="tags commas"&gt;</code>
              <ol>
                <li>list item(s) with warnings tags <code>&lt;li class="warnings"&gt;&lt;a class="tag"...</code></li>
                <li>list item(s) with relationship tags (if any) <code>&lt;li class="relationships"&gt;&lt;a class="tag"...</code></li>
                <li>list item(s) with character tags (if any) <code>&lt;li class="characters"&gt;&lt;a class="tag"...</code></li>
                <li>list item(s) with additional tags (if any) <code>&lt;li class="freeforms"&gt;&lt;a class="tag"...</code></li>
              </ol>
            </li>
            <li>landmark heading level 6 "summary" <code>&lt;h6 class="landmark heading"&gt;Summary&lt;/h6&gt;</code></li>
            <li>blockquote of summary <code>&lt;blockquote class="userstuff summary" title="summary"&gt;</code></li>
            <li>landmark heading level 6 "series" <code>&lt;h6 class="landmark heading"&gt;Series&lt;/h6&gt;</code></li>
            <li>unordered list of series <code>&lt;ul class="series"&gt;</code>
              <ol>
                <li>list item(s) with series <code>&lt;li&gt;Part &lt;strong&gt;#&lt;/strong&gt; of &lt;a...&lt;/li&gt;</code></li>
              </ol>
            </li>
            <li>definition list of stats <code>&lt;dl class="stats""&gt;</code>
              <ol>
                <li>definition list property: value pairs <code>&lt;dt&gt;Words:&lt;/dt&gt;&lt;dd&gt;151&lt;/dd&gt;...</code></li>
              </ol>
            </li>
          </ol>
        </li>
        <li>next list item work blurb</li>
      </ol>
    </li>
  </ol>
</div>

### HTML

```html
<h3 class="landmark heading">Listing Works</h3>
<ol class="work index group">
  <li id="work_1234" class="work blurb group work-1234 user-000" role="article">
    <!--title, author, fandom-->
    <div class="header module">

      <h4 class="heading">
        <a href="...">Work Title</a> by <a href="..." rel="author">pseud (username)</a>
      </h4>

      <h5 class="fandoms heading">
        <a href="..." class="tag">Fandom Tags</a>
      </h5>

      <!--required tags-->
      <ul class="required-tags">
        <li>
          <a href="..." aria-controls="#modal" class="help symbol question modal" title="Symbols key">
            <span class="rating" title="Rating Name">
              <span class="text">Rating Name</span>
            </span>
          </a>
        </li>
        <li> 
          <a href="..." aria-controls="#modal" class="help symbol question modal" title="Symbols key">
            <span class="warnings" title="Warning Names">
              <span class="text">Warning Names</span>
            </span>
          </a>
        </li>
        <li>
          <a href="..." aria-controls="#modal" class="help symbol question modal" title="Symbols key">
            <span class="category" title="Category Names"><span class="text">Category Names</span></span></a>
        </li>
        <li>
          <a href="..." aria-controls="#modal" class="help symbol question modal" title="Symbols key">
            <span class="iswip" title="Work Status">
              <span class="text">Work Status</span>
            </span>
          </a>
        </li>
      </ul>
  	  
      <p class="datetime">30 Sep 2013</p>
    </div>
	  
    <!--warnings again, cast, freeform tags-->
    <h6 class="landmark heading">Tags</h6>
    <ul class="tags commas">
      <li class='warnings'>
        <strong>
          <a href="..." class="tag">Warning Tag</a>
        </strong>
      </li>
      <li class="relationships">
        <a href="..." class="tag">Relationship Tag</a>
      </li>
      <li class="characters">
        <a href="..." class="tag">Character Tag</a>
      </li>
      <li class="freeforms">
        <a href="..." class="tag">Additional Tag</a>
      </li>
    </ul>

    <!--summary-->	
    <h6 class="landmark heading">Summary</h6>
    <blockquote class="userstuff summary">
      <p>This is the summary.</p>
    </blockquote>
  	
    <h6 class="landmark heading">Series</h6>
    <ul class="series">
      <li>Part <strong>2</strong> of <a href="...">Series Title</a></li>
    </ul>

    <!--stats-->
    <dl class="stats">
      <dt class="language">Language:</dt>
      <dd class="language" lang="en">English</dd>
      <dt class="words">Words:</dt>
      <dd class="words">8</dd>
      <dt class="chapters">Chapters:</dt>
      <dd class="chapters">1/1</dd>
      <dt class="kudos">Kudos:</dt>
      <dd class="kudos"><a href="...">1</a></dd>
      <dt class="hits">Hits:</dt>
      <dd class="hits">7</dd>
    </dl>

  </li>
</ol>
```

Here are some of the important things to understand about this layout:

* **The content is presented in logically readable order**, which has *nothing* to do with the order in which that information is displayed visually in a browser. The title comes first even though visually the first thing you see is the square of the required-tags icons.
* **We don't use inline styles.**  You don't see any CSS embedded into the code like this: `<p style="color: blue;">`. This kind of styling is much harder to track down later on for debugging and maintenance. Please don't do it!
* **We almost always name elements with classes rather than IDs.** Any single ID can only be used once per page. Additionally, CSS rules attached to IDs have higher priority than CSS rules attached to classes, so to make it as easy as possible to create skins, it's better if we use classes by default.
* The class names are space-separated groups of short, common words that describe and document what the information contained in that HTML element is.
* **Classes are nested.** That is, CSS rules from the classes on an outer HTML tag will be inherited by an inner tag, as long as they aren't overridden.
* **A class is only declared on the outermost element that needs it.** That is, we have `work blurb` and then the class `blurb` is inherited all the way down; we don't *also* declare, for instance, `<p class="blurb datetime">`. We just declare `<p class="datetime">` and let it inherit the blurb class from above.
* **We use headings with the `landmark` class and the `title` attribute to label otherwise unlabeled sections of HTML.** These are not displayed with the default CSS rules but are available to screenreaders and other special browsers to help with navigation.

The structure of blurbs should be changed only with extreme caution! Everything about the display can be reorganized (and in fact the blurb can be skinned pretty easily by our users), but the HTML should not be altered.

### Reasons for the structure

This structure means it is easy for a piece of software to accurately count the number of items (blurbs) shown in an index. Each new item —- work, index, page region -- is announced by a heading, so users know what information is attached to what title. As a result, a list of headings summarizes the entire index page.

This markup, which counts, groups, and names data, allows both linear and non-linear interactions. This means the page makes sense if you read it top to bottom, makes sense if you read parts of it out of context, and helps you jump around.

For example, a screen reader user may:

1.  enter search query <kbd>tag: bab5 het long</kbd>
2.  jump to the <kbd>Work List</kbd> landmark heading
3.  hear <samp>"list of 17 items"</samp>
4.  hear <samp>heading level 4 "fic title"</samp>
5.  list headings level 4
6.  jump to item 4 and select title link

Without the blurb's current HTML structure, it's hard to give alternative access technologies the kind of spatial interaction that a visual, mousing browser affords.

## Display

While the HTML structure of the blurb is incredibly important and should not be altered unless the actual content and purpose of the blurb changes, the display, which is governed entirely by CSS, is much more flexible.

Here you see two different examples of the work blurb from the AO3, one using the default CSS and one using a skin, which have some of their fields mapped to the blurb diagram to help give you the idea.

![work blurbs](/images/blurb_diagram_mapping.png)

These blurbs use *the same HTML*. The only thing different is the CSS.

### Generic styles

There are many different blurbs in the Archive -- the work blurb, the bookmark blurb, the collection blurb, and so on -- which are all quite similar in their underlying purpose. Rather than having one set of CSS code for the work blurb, another very similar set for the slightly-different-looking bookmark blurb, and so forth, we have made the generic blurb style rules contain everything that these blurbs have in common (which we have deliberately made a lot!).

The generic blurb style is controlled by the single HTML class `blurb`. Every blurb in the Archive should use this class. As you saw in the work blurb HTML, a work blurb uses it: 

`<li class="work blurb group" id="work_1234" role="article">`

If you look at a bookmark index, you will see bookmark blurbs use it as well:

`<li id="bookmark_5678" class="bookmark blurb group" role="article">`.

Let's examine the first generic blurb rule block from the blurb stylesheet:

```css
.blurb ul li, .blurb dd ul li {
  display: inline;
}
```

<dl>
  <dt><code>.blurb ul li</code></dt>
  <dd>This is the selector that tells the browser how to identify (select) the HTML elements that the CSS rule should be applied to. This selector says, to translate it into English, any list item (li) that appears inside an unordered list (ul) that appears inside any element that has the CSS class "blurb".</dd>
  <dt><code>.blurb dd ul li</code></dt>
  <dd>A second selector (you can have as many as you want in a CSS rule, comma-separated as here) that tells the browser to apply the style to any list item (li) that appears inside an unordered list (ul) that appears inside a definition list description (dd) that appears inside any element that has the CSS class "blurb".</dd>
  <dt>{...}</dt>
  <dd>The declaration block is a semicolon-separated list of property: value pairs that tell the browser how to style the selected elements.</dd>
  <dt><code>display: inline;</code></dt>
  <dd>This is the declaration. It is a property: value pair that, in this case, says to display these selected HTML elements inline (that is, following one another on the same line) instead of one after another each on a new line (which would otherwise be the default behavior for list items).</dd>
</dl>

Can you tell which parts of the work blurb this rule affects? What about the parts of the bookmark blurb?

### Specific styles

Notice that the class declaration of our blurbs *also* includes a class that describes the *type* of blurb: work blurbs have the class `work` and bookmark blurbs have the class `bookmark`.

This enables us to modify the basic setup slightly for different classes of blurb using the more specific class name. Normally these modifications are only going to be one or two lines. The most modification is for bookmark blurbs:

```css
.bookmark p.status {
  position: absolute;
  right: 0.25em;
  width: 60px;
  margin-top: 0.429em;
}

.bookmark .status span, .bookmark .status a {
  display: block;
  width: 25px;
  height: 25px;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: 0;
}

.bookmark .status a:focus {
  overflow: hidden;
}

.bookmark span.count {
  line-height: 1.875em;
  position: absolute;
  top: 0;
  left: 28px;
  text-align: center;
}

.bookmark .count a {
  border-bottom: none;
  color: #069;
}

.bookmark .count a:hover, .bookmark .count a:focus {
  color: #111;
}

.bookmark .datetime {
  top: 28px;
}

.bookmark .user {
  border: 1px solid #ccc;
  clear: right;
  overflow: hidden;
}

.bookmark .user .meta {
  display: inline;
  font-family: Georgia, serif;
  font-size: 0.875em;
  line-height: 2;
}

/* line break between types of meta */
.bookmark .user ul.meta:after {
  content: '\A';
  white-space: pre;
}

.bookmark .short .header {
  min-height: 30px;
}

.bookmark .user .datetime, .bookmark .work .datetime {
  top: 0;
}

.bookmark .short .status {
  left: 30px;
  margin-top: 0;
  top: 0;
  width: 25px;
}

.bookmark .dynamic {
  position: static;
}

.bookmark .recent .index {
  width: 100%;
}
```

So what this means is, if we decided to add individual user blogs to the Archive and wanted an index of blogs, we wouldn't need to code it from scratch. Instead, we could copy the HTML structure used for work blurbs or user blurbs and we would only add a few lines of CSS using something like the `.blog .blurb` class names combined in order to make the blog blurbs look the way you wanted them to, keeping everything as consistent as possible with the other blurbs.
