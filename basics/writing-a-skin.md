---
layout: page
title: Writing a Skin
parent: HTML & CSS Basics
nav_order: 3
---
# Writing a Skin
{: .no_toc }

Anyone with an Archive account can customize the way the Archive is presented to them by creating and applying a site skin that either modifies the default display or restyles the Archive from scratch. 

The skin system is also a great way to get familiar with CSS in general or the Archive's class structure. You can create a new skin by logging in and going to [the Skins index](https://archiveofourown.org/skins), where you will find a "Create Skin" link. Select that and you will be taken to a form, which will already be set up to create a Site Skin -- you just need to enter a unique title.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Styling the regions

Here we'll walk through a simple skin that modifies the Archive's default appearance by changing fonts and colors, adding images, and adjusting margins and borders.

![A user dashboard with our skin: a bright diagonal striped background, translucent white main content, and translucent yellow dashboard sections](/images/writing_a_skin_preview.png)

For our colors and images, we'll be using a stripe pattern called [sing together](https://www.colourlovers.com/pattern/850926/sing_together) and its color palette, [like fireflies](https://www.colourlovers.com/palette/1172215/like_fireflies), both of which are by [electroCUTE!](https://www.colourlovers.com/lover/electroCUTE%21). You'll need to save and upload the background image to an image host, but because you are the only one seeing your skin, you probably don't need to worry about running out of bandwidth.

Once you've entered the style block from the first step into the CSS field, you'll need to select "Submit" after the form and "Use" on the following page to see the changes. After that, using the "Update" button on the skin form will save the changes and let you see them. It's a good idea to do it after each step so you can understand exactly what changes we've made.

1.  Let's change the font and the font color for the entire page using the universal selector (`*`) and `!important`, which will ensure that our changes override the defaults across the whole site.

    ```css
    *{
      font-family: Verdana, Tahoma, Helvetica, Arial, sans-serif !important;
      color: #444;
    }
    ```

2.  Now let's use our striped pattern for the background of the page. We'll also set the lightest color from the corresponding palette as the fallback color to make sure we don't see the usual white even if our image fails to load. We'll do this with `background`, which is a [CSS shorthand property](css#shorthand-properties) that lets you set values for multiple properties, including `background-color` and `background-image`, at the same time.

    ```css
    body {
      background: #F6F6C6 url(https://example.com/sing_together.png);
    }
    ```

3.  The Archive's signature red clashes with that, so let's take the pinkish red from the palette and use that to replace the red in the header and footer. We'll also change the borders on the header and footer and remove the shadow effect from the header.

    ```css
    #header ul.primary, #footer {
      background: #FE8665;
    }
    
    #header ul.primary {
      border-bottom: 5px #FCDF7D solid;
      box-shadow: none;
    }
    
    #footer {
      border-top: 5px #FCDF7D solid;
    }
    ```

4.  It's hard to read on that busy pattern, so let's give the main content of the site a translucent white background. We'll let the pattern stick out on the sides by setting some margins, and we'll also round off the corners and give our white area a drop shadow. We've previously been using hexadecimal values for the colors, but here we'll switch to RGBa to lower the opacity of our colors. (If you're using Internet Explorer 8 or earlier, you'll see solid colors instead. If this were the official Archive layout, we might use a special stylesheet to add transparency for Internet Explorer 8 and lower.)

    ```css
    #main {
      background: rgba(255,255,255,0.9);
      margin: 1em;
      border-radius: 1em;
      box-shadow: 1px 1px 2px rgba(0,0,0,0.25);
    }
    ```

5.  Pages that belong to users or collections have an additional navigation section called the dashboard. Not only does that need to be styled, but we also need to adjust `#main` slightly so it still has margins when the dashboard is present. We'll give the dashboard a translucent yellow background, rounded edges, no borders, and highlighting for current and hover areas.

    ```css
    #main.dashboard {
      margin-right: 1em;
    }
    
    #dashboard.own {
      border: none;
    }
    
    #dashboard ul {
      background: rgba(252,223,125,0.9);
      border-top: none;
      text-align: center;
      margin-top: 2px;
      border-radius: 1em;
    }

    #dashboard .current, #dashboard a:hover {
      background: rgba(255,255,255,0.35);
    }
    ```

## Styling works

All user copy is placed inside either `<blockquote class="userstuff">` or `<div class="userstuff">`, so you can style it by targeting `.userstuff` as a whole or by using `.userstuff` along with another selector. 

Let's add the following to our site skin:

```css
.userstuff { 
  background: #F6F6C6; 
  border: 1px #FCDF7D solid; 
  border-radius: 1em;
}
``` 

If you spend a few minutes browsing the site with that in your skin, you'll notice that works aren't the only user copy on the site. Profiles, collection pages, work and bookmark blurbs, and administrative pages (e.g. the FAQ) all contain user copy and are also affected by that style.

(You can go back and delete the `.userstuff` styles now -- we won't be using it elsewhere in the tutorial.)

If you *only* want to change the way works are displayed, using `#workskin` is your best bet. Its primary function is to help work creators make work skins, which style the work for anyone who views it on the Archive, but it is also an effective way to modify works for your personal site skin. 

You may want to...

* Change the font: `#workskin { font-family: Georgia, serif; }`
* Indent paragraphs: `#workskin p { text-indent: 2.5em; }`
* Hide the work notes: `#workskin .preface .notes { display: none; }`

## Styling work metadata

The work view has a lot of metadata on it, but other pages such as user stats, user profiles, and series pages also contain metadata that you might not want to style. The metadata is *not* inside `#workskin`, but you can use `.work-show .meta` to target the metadata for works.

You might want to suppress some metadata: 

* Hide the whole meta block: `.work-show .meta { display: none; }`
* ...or just the bits you don't want to know: `.work-show .meta .warning, .work-show .meta .stats { display: none; }`

Or you might want to highlight some metadata:

* Highlight the rating with pink: `.work-show .meta .rating { background: #FE8665; }`
* Make the fandoms bold: `.work-show .meta .fandoms { font-weight: bold; }`
