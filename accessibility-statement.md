---
layout: page
title: Accessibility Statement
---
# Accessibility Statement
{: .no_toc }

This page is an overview of ways we have tried to make the Archive accessible. Accessibility is always a work in progress, so this document will and should change.

If you have any questions or comments, please [contact Support](https://archiveofourown.org/support). Portions of this document have been taken from the now-defunct diveintoaccessibility.com.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Standards compliance

{: .note }
>This section represents the standards we strive to meet; where we sometimes miss the mark, we will aim to get back into compliance at a future date.

When we talk about pages complying with a standard, we mean that the *site framework* (that is, the code for the interface surrounding user content like fanworks, summaries, descriptions, etc) complies. We do not try to validate our user-generated content, though we do parse it for display using [Nokogiri](https://nokogiri.org), a standards-compliant parser. But as a rule, we aim to encourage valid and accessible coding from our users through advocacy and training, not auto formatting.

1.  Most importantly, all pages on this site use structured semantic markup. `h1` is used for the site name. `h2` is used for the individual page name. `h3` is used for section headings within the page. `h4` is used for article names, like the name of commenter or the titles on a list of works. For example, on this page, JAWS users can skip to the next section within the accessibility statement by pressing <kbd>ALT+INSERT+3</kbd>.

2. All framework pages on this site are or work towards <abbr title="Web Content Accessibility Guidelines">WCAG</abbr> <abbr title="triple A">AAA</abbr> approved, complying with all [priority 1, 2, and 3 guidelines](https://www.w3.org/TR/WAI-WEBCONTENT/full-checklist.html) of the [World Wide Web Consortium Web Content Accessibility Guidelines](https://www.w3.org/TR/WCAG10/). This is a judgement call.

4. All framework pages on this site are <a href="https://www.cynthiasays.com/">Section 508 approved</a>, complying with all of the <abbr title="United States">U.S.</abbr> Federal Government <a href="https://www.section508.gov/">Section 508 Guidelines</a>. Again, a judgement call.

5. All framework pages on this site otherwise <a href="https://validator.w3.org/">validate</a>. This is not a judgement call; a program can determine with 100% accuracy whether a page is valid HTML. For example, you can enter your AO3 user page URL on the [W3 validator](https://validator.w3.org/check) and check it for HTML validity.

## Languages

The Archive is an international development, made by people who speak lots of different languages. Our goal is to allow the interface to be translated into any language that has volunteers to work on it.

## Navigation aids

1.  We aim to make our help and FAQs accessible in multiple ways. 

2.  We have tried to provide help that is not biased towards sighted or mouse methods of using the Archive, by describing pages and interactions in several different ways.

3.  Our help buttons are styled text, so you can make them bigger if they're hard to see or interact with.

4.  The home page and all archive pages include a search box. Advanced search options are available from any search results page and from the search menu.

5.  All navigation, sorting, actions, and page regions are announced by a relevant and descriptive heading. These headings are hidden from visual browsers by default, but you can use a skin to show these headings to any browser.

## Links

1.  Links are written to make sense out of context.

2.  Navigation and action links are visually styled as large and distinct buttons. They can be scaled up with text zoom to make them easier to click on with a mouse or joystick or tap on a touch screen.

## Forms

1.  Our forms are laid out in a limited and regular number of ways, and we've tried to make it clear when a form begins and ends.

2.  We have labelled everything to make it clear what we're asking you to do. In very short forms those labels may be visually hidden.

3.  We've written our forms so that you can click or tap on the label text to check the little box or position your cursor inside the text field.

## Images

1. All images are described with text alternatives. Purely decorative graphics include null `alt` attributes.

## Visual design

1.  We use cascading stylesheets for visual layout.

2.  We use only relative font sizes, compatible with the user-specified "text size" option in visual browsers.

3.  If your browser or browsing device does not support stylesheets at all, the content of each page is still readable.

### Alternative visual layouts (skins)

You can skin the archive interface for yourself in any way that you find useful.

We try to design in an accessible way, which means that we've made the interface *open* for you to *adapt* easily, rather than thinking to know what you need better than you do yourself. AO3 is lucky in that there are people using, coding, and testing via many different methods.

You don't have to know how to code to adapt the Archive. If you [contact Support](https://archiveofourown.org/support) with layout changes that would help you, Support will alert the coding team to your needs, and the coding team can attempt to make the necessary changes to the Archive's default style.

## JavaScript

We use JavaScript to improve usability and performance, but all our content and core functionality is accessible with JavaScript turned off.

## Screen readers

1.  We use headings and lists to structure our pages. You can jump around the page regions by heading.

2.  We have implemented basic ARIA landmark roles and as we go along we are adding in more ARIA attributes as we figure out how best to use them.

3.  We have an experimental aural stylesheet. We are investigating supporting a say-instead or pronunication dictionary. If you would like to help, please [volunteer](https://transformativeworks.org/volunteer) or send us [feedback](https://archiveofourown.org/support).

4.  We support aural skins.
				
## Keyboard access

1.  We write our pages in a logical order, so you can tab through the whole Archive. We decided not to add accesskeys, because we know they can sometimes mess up your own shortcuts.

## Small screens, slow Internet

We try and keep our site pages relatively small and functioning on screens of any size including mobile devices.
