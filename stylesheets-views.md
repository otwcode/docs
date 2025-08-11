---
layout: page
title: Stylesheets & Views
parent: Front End Guide
nav_order: 1
---
# Stylesheets & Views
{: .no_toc }

Our stylsheets contain the CSS that styles the HTML in our views.

<details markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Stylesheets

The Archive has 33 stylesheets, the first 22 of which are always applied. Of the remaining 11:

- two are role-specific (translator and admin),
- two are specific to relative screen width (midsize and narrow)
- two are media-specific (aural for speech synthesizers, and print for printers),
- four are Internet Explorer conditionals (used only when the site is accessed in the corresponding version of Internet Explorer), and
- one is our sandbox (always used, but home to temporary or experimental styles we aren't ready to put into the first 29).

On your development environment, you will see all of the stylesheets listed in the document head. The order they are listed in is the cascade hierarchy.

Things are a little different on our staging and production environments, which use our skin system to combine the stylesheets. If you look at the page source on either of these environments, you will notice that the first 22 stylesheets have been grouped into a single file named 01\_site\_screen\_.css. (These skin stylesheets are cached, so if a change fails to show up after being deployed to test or production, the first step to figuring out why is to ask the person in charge of the code push to recache the stylesheets.)

### Core

The first stylesheet defines the basics to make the Archive readable and navigable. It sets the typographic styles, applies padding to create space between page regions (e.g. the header and the main content), turns off elements that should be inaccessible to everyone, visibly hides elements that should only be available to screen readers, sets certain list items to display horizontally instead of vertically, and adds styling to make forms readable.

### Elements

The second stylesheet includes [the Meyers Reset](https://meyerweb.com/eric/tools/css/reset/index.html), a CSS reset designed to remove any browser-specific styling that is applied to specific elements. This means we have to spend less time figuring out why there is more space between paragraphs in Firefox than in Internet Explorer.

This stylesheet is also where we set the base styling for HTML elements like paragraphs, tables, and links. There are virtually no classes or ids here; those belong farther down the cascade.

### Regions

The next four stylesheets cover the four basic regions of the site in the order they are included on the page. These are the stylesheets most likely to use ids rather than classes as selectors, since they are high up in the cascade and often need to override styles that are defined lower in the cascade. Three of the four regions appear on every page.

#### Header

The header is the region containing the site name and logo, the log-in form or logged-in user-specific navigation, main site navigation, and collection name and banner. All styles specific to the header belong in this stylesheet.

#### Dashboard

The dashboard is the only region that does not appear on every page. It most often contains navigation specific to users and collection pages, and it generally takes the form of a sidebar on the left of such pages. (It appears beneath the header and above the main content on narrow screen.) All styles specific to elements contained in the dashboard belong in the dashboard stylesheet.

#### Main

The main region includes most of the site content. While filters, which typically appear as a sidebar on the right of index pages, are part of the main content, the dashboard is *not*.

Although the main region contains the majority of our content, this stylesheet contains perhaps the fewest rules. Here we focus on `<div id="main">` itself (e.g., setting it off to the right to give the dashboard room) rather than its contents, which we instead style in stylesheets 7 - 24.

#### Footer

The footer primarily contains informational links, but some quick customization options go here as well (currently, that means the skin selector; in the future, it will also mean a language selector). It appears beneath the main content and all styles specific to the footer should be defined in this stylesheet.

### Interactions

Interactions are means through which users provide us information. Generally, this means forms and form elements. We also have a few JavaScript-based tools that help users fill out forms (e.g., the tag autocomplete, a calendar widget, a drag-and-drop for reordering series or chapters) that we include here, since they serve as custom form elements.

### Actions

Actions are links, buttons, and the elements that contain the links and buttons (e.g., lists that hold pagination links). For convenience, we include submit buttons here rather than in interactions; we often display links and submit buttons side-by-side (e.g., the Subscribe option on a work is an input and the Share option next to it is a link) and thus style them similarly.

### Modifiers

The next two stylesheets, 09-roles-states and 10-types-groups primarily contain modifiers. The stylesheet named 10-types-groups also contains groups.

#### States

States modify the appearance of an element based on its status: whether an inbox message has been read, whether a tag is canonical, whether a list can be expanded. These classes tend to be non-permanent, changing based on user actions (e.g., a work stops being `.draft` once it is posted).

#### Types

A type is a descriptor that does not change: this tag is always going to be a relationship tag, this link is always going to be an RSS link.

#### Relationships

Relationships describe how an element relates to something else: `.own` might describe the relationship between a dashboard region and a logged-in user, `.child` and `.parent` might describe the relationship between two related works.

#### Roles

Roles are generally used to describe elements that are tied to users with certain permissions. Since administrator and administrator-granted roles (e.g., tag wranglers) have areas of the site that are only accessible to them and require extensive styling, they have their own zone and role stylesheets farther down the cascade. Styles for less complex roles (e.g., `.mod` or `.participant` for a challenge or collection) would go here.

### Groups

Groups are collections of related information. There are eight kinds of groups, the last five of which have their own stylesheets. The first three are currently in 10-types-groups.

#### Stats

A stats group contains paired values that give information about an item (e.g. "Hits: 3" or "Completed: Yes"), generally in blurbs or meta. A stats group always takes the form of `dl.stats`.

#### Module

A module is a general group that contains related elements, usually of multiple types: a navigation module might contain `ol.pagination` and `p.action`, a header module might contain `h2.heading` and `p.icon`. Styling for specific types of modules goes elsewhere; here we just set `.module` and `.dashboard .module` to have the right size and position.

#### Index

An index is a list group: `dl.index`, `ul.index`, or `ol.index`. We use them in a lot of different places and do a lot of different things with them, so we keep the default styling to a minimum.

#### Listbox

A listbox is a container for an index; we use them when a page is designed to include multiple indices. For example, a user's home includes indices of works, series, and bookmarks that the user has created. Each index is grouped inside a listbox. If a user only has bookmarks, their bookmarks are still displayed in a listbox because the page *could* contain other indices given more user data (e.g., if the user posts a work, a works index will be added).

#### Meta

Meta is a group that provides an overview of the tags, associations, and statistics we keep for a single item: a user, a work, a series, a collection. It's always inside a wrapper.

#### Blurb

Blurbs are standalone metadata, most often presented in an index list.

#### Preface

A preface is the group of information at the start of a work or chapter. We modify the preface with `.afterword` for the group of information at the bottom of a work or chapter.

#### Comment

Comments are groups containing messages from users or guests. Like blurbs, they are most often presented in an index list.

### Zones

Zones are types of `#main` regions. There are five zones that make up stylesheets 16 - 20.

#### System

The system stylesheet has eight subsections:

  1. Splash (i.e., the homepage)
  2. Sessions (e.g., the login page and password reset page)
  3. Docs (e.g., the about page and wrangling guidelines)
  4. Comms (unused)
  5. Support (i.e., the Support and Policy & Abuse forms)
  6. FAQ
  7. TOS, including the TOS FAQ and the TOS pop-up
  8. Proxy notice, which is a warning that displays on proxy sites but is never used on AO3 itself

#### Home

The home zone is a type of `#main.dashboard` -- that is, a type of page with a dashboard. If the page has a module containing an icon, a heading, and some navigation, it's in the home zone. The main and profile pages for users and collections are examples of this zone.

#### Search/browse

The search zone refers to pages containing search forms; the browse zone refers to pages containing filters.

#### Tags

Pages for tags, tag sets, and tag wrangling belong to the tags zone.

#### Translation

The Archive will eventually be translated into additional languages. This may one day be needed for style overrides for the third-party in-context editor.

### Userstuff

The userstuff stylesheet styles blocks of user-entered text such as comments or summaries, admin-entered text like news posts or FAQs, and large blocks of hardcoded text like the [About Us page](https://archiveofourown.org/about).

Styling for works can be found in `#workskin`.

### System messages

Error, success, and caution messages as well as notes. This also styles the admin banners that are displayed on every page of the site during certain events.

### User roles

These stylesheets override the Archive default styles for certain types of logged-in users. This is necessary to accommodate certain role-specific options. We sometimes further modify regions here (e.g., the footer background is teal for administrators).

#### Translator role

Style overrides for users who are logged in as translators will go here. This will probably be merged with the translation zone.

#### Admin role

Style overrides for logged-in administrators go here.

### Stylesheet roles

There are eight stylesheets with styles that are only applied when the Archive is being accessed with specific hardware or software.

#### Media roles

These stylesheets provide information for devices with narrow screens, screen readers, and printers. The 62em and 48em breakpoints were not chosen to correspond to any particular device, but to the size at which the Archive layout needs to be adjusted to improve usability.

#### Internet Explorer roles

These stylesheets make the site more compatible with Internet Explorer. We have stylesheets for Internet Explorer 5 - 8, but we are only actively supporting Internet Explorer 8.

### Sandbox

The sandbox is where we put experimental styles and temporary style fixes. It is loaded *after* user skins, which means it overrides their styles. It can be handy for development, but it is generally best to make sure your styles are incorporated into the proper stylesheet before submitting a pull request.

## Page-by-page views

{: .caution-title }
> Incomplete
>
> This section is a draft.

Views follow regular layouts and contain repeating groups of HTML elements. These groups are described with [classes](classes). Rails generates some classes, and those contain underscores; you can use them to target rules at individual pages.

Within the region `#main` the view changes. There are N basic views:

### Index view

An index is a list of works, users, collections, or bookmarks (e.g., the [work index for Bandom](https://archiveofourown.org/tags/Bandom/works) or the [bookmark index for Supernatural](https://archiveofourown.org/tags/Supernatural/bookmarks)).

The metadata describing the items in an index view is grouped in a [blurb](/patterns/blurb).

### Work view

Works are viewed on their own pages (e.g., [Sliding Doors](https://archiveofourown.org/works/149319)). They are similar to a blog post: metadata at the top and comments at the bottom.

### Bookmark view

Bookmarks can be viewed on their own (e.g., a [single bookmark for Sliding Doors](https://archiveofourown.org/bookmarks/8020331)) or grouped with all the bookmarks of a work (e.g., the [list of bookmarks for Sliding Doors](https://archiveofourown.org/works/149319/bookmarks)).

### User, collection view

Each identity (e.g. the [user testy](https://archiveofourown.org/users/testy) or the [Yuletide collection](https://archiveofourown.org/collections/yuletide)) has its own set of pages, listing activities like works written, works viewed, personal profile, preference settings, and so on. There's a persistent dashboard navigation on these pages.

### Profile view

Profile view is only used in user and collection views (e.g. the [Yuletide collection profile](https://archiveofourown.org/collections/yuletide/profile) and [testy's profile](https://archiveofourown.org/users/testy/profile)).
