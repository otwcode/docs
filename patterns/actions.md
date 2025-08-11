---
layout: page
title: Actions Pattern
parent: Design Patterns
nav_order: 3
redirect_from:
  - /front_end_coding/patterns/actions
---
# Actions Pattern
{: .no_toc}

Actions are navigational links and form inputs, which we style to look like buttons.

It's a very loose pattern, but it's normally a list of links. On most pages, there is an unordered actions list straight after the `h2` page heading. Actions can show up anywhere, however, in any group, zone, region, or interaction.

The actions styles are declared in [the stylesheet named 08-actions.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/08-actions.css). They are a [supertype](../classes-taxonomy#supertypes).

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Rules

Actions can be any element that contains one or more actions. While actions frequently appear in groups marked up as unordered lists (`<ul class="actions">`), a single action can often be found inside paragraphs (`<p>`) or descriptions (`<dd>`) with the `action` class applied to the containing element (rather than the link or input).

Nested actions blocks have the class `secondary`, which is a general modifier.

Forms may be included inside actions blocks, but only if they are `simple` forms with a single text `input` (e.g., a search form like the one in the site header) or single-button forms (e.g., a Subscribe button).

## HTML diagram

<div class="diagram">
  <ol>
    <li><code>&lt;ul class="navigation actions"&gt;</code>
      <ol>
        <li><code>&lt;li&gt;</code>
          <ol>
            <li><code>&lt;a&gt;</code></li>
          </ol>
        </li>
        <li><code>&lt;li&gt;</code>
          <ol>
            <li><code>&lt;span class="current"&gt;</code></li>
          </ol>
        </li>
        <li><code>&lt;li aria-haspopup="true"&gt;</code>
          <ol>
            <li><code>&lt;a&gt;</code></li>
            <li><code>&lt;ul class="secondary"&gt;</code>
              <ol>
                <li><code>&lt;li&gt;</code>
                  <ol>
                    <li><code>&lt;a&gt;</code></li>
                  </ol>
                </li>
                <li><code>&lt;li&gt;</code>
                  <ol>
                    <li><code>&lt;a&gt;</code></li>
                  </ol>
                </li>
              </ol>
            </li>
          </ol>
        </li>
        <li><code>&lt;li&gt;</code>
          <ol>
            <li><code>&lt;a&gt;</code></li>
          </ol>
        </li>
      </ol>
    </li>
  </ol>
</div>

## Subtypes of actions

* `.navigation` actions are the major navigational items in a region. In the header, footer, and dashboard, all actions are `.navigation`. In the main region, `.navigation` actions follow the `h2` page heading (they can also be repeated after all other `#main` content).

* `.landmark` items help users who access the Archive with screen readers skip around on a page. In our default style, landmarks are hidden from view in a way that keeps them accessible to screen readers. Landmarks generally do not have the `actions` class and are more often headings than links.

  * `#skiplinks` are links at the top of the page that let users skip over the navigation and go directly to the main content of the page. (You can learn more about skip links from [WebAIM's "Skip Navigation" Links article](https://webaim.org/techniques/skipnav/).)
  
* `.pagination` actions let users move between pages of like items (e.g., when there are more than 20 works for a particular tag, the blurbs are spread across multiple pages). Pagination actions are typically included both before and after the list of paginated items.

* `.sorting` actions rearrange items (e.g., a user can rearrange the works on their statistics page most kudos, fewest hits, and so on).

* `.submit` actions are form input controls (e.g., `<p class="submit actions"><input type="submit"></p>`).

* `.action`

* `.current` is an actions state used to give a visual indication that an action corresponds to the current page and parameters (e.g., the "Bookmarks" navigation action has the `.current` state on the [Fullmetal Alchemist bookmarks index](https://archiveofourown.org/tags/Fullmetal%20Alchemist/bookmarks) and the "Comments" sorting action has the `.current` state when sorting statistics by most or least comments).

* `.cancel`
* `.close`
* `.delete`

* `input[type="submit"]` and `button` are elements rather than classes. Browsers typically style these elements to look like buttons by default, but we override that to make them look like *our* buttons.

## Actions and landmark headings

Sometimes actions blocks are announced by a landmark heading. This is a case-by-case decision and must not be done reflexively, only where it is properly useful, like where there are lots of different kinds of actions blocks grouped, or where a user is probably going to load a page and go directly to a specific action. So, in layout, you can't rely on an actions block being directly preceded by a heading.

## ARIA roles

Actions may have [ARIA roles](http://www.w3.org/TR/wai-aria/roles). Unfortunately, many of these have been applied incorrectly and should be removed whenever they are encountered.

<dl>
  <dt><a href="https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role">role="navigation"</a></dt>
  <dd>Intended for the main blocks of navigation on a page, such as the site navigation. It should only be applied to elements like <code>div</code>, which don't have their own implicit role, but you may find it incorrectly applied to elements like lists. In cases where it is correctly applied to a <code>div</code>, replacing the <code>div</code> with a <code>nav</code> element may be prefereable to removing the role -- check with the Front End Leads.</dd>
  <dt><a href="https://www.w3.org/TR/wai-aria-1.1/#menu">role="menu"</a></dt>
  <dd>Intended for application-style menus, like what you might find in the rich text editor. On the Archive, it is generally misued in the same manner as <code>role="navigation"</code>.</dd>
  <dt><a href="https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role">role="button"</a></dt>
  <dd>Intended for elements that trigger a response when clicked, such as toggling the visibility of an item on the page. This role is redundant when applied directly to buttons and incorrect when applied to elements surrounding them (e.g., <code>li role="button"</code>). Links with this role applied directly or to their parent should be replaced with <code>button</code> elements if they provide button-like functionality.</dd>
</dl>
