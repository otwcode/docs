---
layout: page
title: Class Taxonomy
parent: Front End Guide
nav_order: 3
---
# Class Taxonomy
{: .no_toc }

The Archive by default shows as much information and as many actions as possible. Thoroughly and systemically classifying information and actions allows things to be hidden, de-emphasised, or highlighted with CSS. We can easily reorganize pages as we develop and gladly allow our users to reorganize things to their own liking.

Most of the classes listed on this page are concrete classes, which can be found in HTML `class` attributes on at least one page, and often many pages. However, some of the classes here are abstract classes that never appear in the HTML, but instead influence how we organize our stylesheets.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Supertypes

There are four concrete supertype classes and one abstract supertype class. (Abstract classes

* [.region](#region)
* [.group](#group)
* [.zone](#zone)
* [.actions](#actions)
* [.interactions](#interactions) (abstract)

### .region

Specific regions are given `id` identifiers that are applied alongside the `.region` class.

Regions correspond with [ARIA regions and HTML5 sectioning elements](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/HTML5.html).

* #header
* #dashboard
* #main
* #footer

### .group

* [.index](/patterns/indexes)
* [.listbox](/patterns/listbox)
* [.meta](/patterns/meta)
* [.blurb](/patterns/blurb)
* [.preface](/patterns/preface)
* [.comments](/patterns/comments)
* [.stats](/patterns/stats)

### .zone

* .system
  * .splash
  * .sessions
  * .docs
  * .feedbacks (support)
  * .faq
  * .tos
  * .tos_faq
  * #tos_prompt
  * #proxy-notice
* .home
  * [objects](#object) (abstract)
* searchbrowse (abstract)
  * .filters
  * .search
* .tags
* .translation

### .actions

* .navigation
* .pagination
* .action

### .interactions

* .post also .create (create or edit something, since post and edit forms are the same)
* .search (find something)
* .destroy (delete a record)
* .manage (edit preferences, manage inbox)
* .filter (remove this in favor of .searchbrowse .filters)
* .review (tag set nominations)
* .update (tag edit)
* widget (abstract)
  * .character_counter
  * .LV_* (live validation does not have an overarching class, but all of its classes begin with the prefix LV)
  * .autocomplete
  * .ui-sortable and .ui-draggable
  * .ui-datepicker and .ui-timepicker
  * .qtip (tooltips)
  * #modal
* ajax (abstract)
  * .ajax-remove
  * .ajax-create-destroy

### Grouping and Spacing

There are also a few presentational classes set in `10-types-groups.css` that do not have patterns or a lot of layout. They can be useful for skins.

* .module
* .wrapper
  * #outer
  * #inner

Another presentational class is `.clear`, set in `02-elements.css.` It is used strictly on null `div` elements when we need to apply [clear: both](https://www.w3schools.com/css/css_float.asp) to ensure an element appears below the preceding floated elements.


## Types

We can divide types into two abstract classes:

* [object](#object)
* [data](#data)

### object

The abstract class `.object` encompasses classes that correspond with database records. These are typically a *type* of record that corresponds with a model name, such as `.work` or `.user`, but sometimes they're *specific* records, such as the `.rating-teen` class that corresponds with the [Teen and Up Audiences rating tag](https://archiveofourown.org/tags/Teen%20And%20Up%20Audiences).

* .user
* .work
  * .chapter
* .series
* .bookmark
  * .rec (a state [modifier](#modifiers) specific to bookmarks, like `.public` and `.private`)
* .skin
* .tags
  * .tag
    * .freeform
    * .required-tags
      * .rating
        * .rating-general-audience
        * .rating-teen
        * .rating-mature
        * .rating-explicit
        * .rating-notrated
      * .category
        * .category-femslash
        * .category-gen
        * .category-het
        * .category-slash
        * .category-multi
        * .category-other
        * .category-none
      * .warnings
        * .warning-yes
        * .warning-no
        * .warning-choosenotto
        * .external-work (.warnings becomes an abstract)
      * .iswip (a state [modifier](#modifiers) presented as part of the `.required-tags` block in [blurbs](/patterns/blurb))
        * .complete-yes
        * .complete-no
* .tagset
  * .nomination
* .collection
  * .prompt
  * .item
  * .signup

### data

The abstract class `.data` encompasses classes that describe the type or format of the information it's applied to.

* .heading
* .title
* .byline
* .datetime
* .news
* .notes
* .footnote
* .summary
* .toc
* .faq
* .intro
* .count
* [.status](#modifiers#state-modifiers)
* .notice
* .error
* .icon
* .symbol
  * .help
  * .question
* .alphabet
  * .letter
* .media
  * .medium

Additionally, `.userstuff` is a type of data that was entered into a text field by a user, guest, or admin. It's the only type of data with its own stylesheet, [21-userstuff.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/21-userstuff.css).

For simplicity, we also use `.userstuff` on [system pages](#zone) like the [Terms of Service](https://archiveofourown.org/tos), where the text is hardcoded rather than user-entered. This helps ensure consistent styling of text-heavy pages.

## Modifiers

Modifier classes are used to further describe data, objects, and interactions. They're the most specific type of class and should come first: `own work blurb group` or `caution notice`.

Modifiers can be grouped into these abstract classes:

* [roles](#role-modifiers)
* [states](#state-modifiers)
* [contexts](#context-modifiers)
* [abilities](#ability-modifiers)
* [modes](#mode-modifiers)

### Role modifiers

* roles (abstract)
  * .wrangler
  * .user
  * .visitor
  * .admin
  * .participant also .member
  * .mod
  * .owner
  * .anonymous
  * .official

### State modifiers

* states (abstract)
  * [.current](/patterns/actions) (navigation modifer used to indicate the current position in the navigation options)
  * .hidden
  * .public (bookmark)
  * .private (bookmark)
  * .mystery (work)
  * .important
  * .caution
  * .required
  * .latest also .recent
  * .open
  * .closed
  * .odd ([comment](/patterns/comments))
  * .even ([comment](/patterns/comments))
  * pending (abstract state)
    * .draft
    * .preview
    * .unreviewed
    * .unread
    * .unfulfilled
    * .unwrangled
  * completed (abstract state)
    * .reviewed
    * .read
    * .replied
    * .claimed
    * .posted
  * relationship (abstract state)
    * .child
    * .parent
    * .synonym
    * .meta (tag)
    * .canonical
    * .own

### Context modifiers

* contexts (abstract)
  * .dashboard
  * .primary
  * .secondary
  * .tertiary
  * .start
  * .end

### Ability modifiers

Ability modifiers apply to [interactions](/patterns/interactions).

* abilities (abstract)
  * .draggable
  * .droppable
  * .sortable
  * .dynamic
  * .expandable

### Mode modifiers

Mode modifiers apply to [interactions](/patterns/interactions).

* modes (abstract)
  * .single
  * .simple
  * .verbose

## Travellers

[Index](/patterns/indexes) is the most used example of the polyvalent "types or states of groups."

* .index
* .tree
* .cloud
