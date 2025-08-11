---
layout: page
title: Regions
parent: Design Patterns
nav_order: 1
---
# Regions
{: .no_toc}

As discussed in [Stylesheets & Views](../stylesheets-views), there are four major regions on the Archive, three of which are included on every page. They are contained within outer and inner wrappers.

While the regions aren't themselves reusable patterns -- each region appears a maximum of once per page -- they do make use of patterns.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Quick reference

<dl class="key"><dt>[...]</dt><dd>always included</dd>
<dt>{...}</dt><dd>sometimes included</dd></dl>

<pre>
[outer wrapper]
  [header region]
  [inner wrapper]
    {dashboard region}
    [main region]
  [/inner wrapper]
  [footer region]
[/outer wrapper]
</pre>

## HTML diagram

{: .note-title }
> A note on skip links
>
> Skip links are not considered a region and are not visible. However, they are included on every page to allow users of some assistive technology to jump directly to the main content, so we've included them in our diagram.

Because the page in our diagram has a `#dashboard` region, the `#main` region is given the `.dashboard` [modifier](../class-taxonomy#modifiers) class.

<div class="diagram">
  <ol>
    <li>
      <code>&lt;body&gt;</code>
      <ol>
        <li>
          <code>&lt;div id="outer" class="wrapper"&gt;</code>
          <ol>
            <li>
              <code>&lt;ul id="skiplinks"&gt;</code>
            </li>
            <li>
              <code>&lt;div id="header" class="region"&gt;</code>
            </li>
            <li>
              <code>&lt;div id="inner" class="wrapper"&gt;</code>
              <ol>
                <li>
                  <code>&lt;div id="dashboard" class="region"&gt;</code>
                </li>
                <li>
                  <code>&lt;div id="main" class="dashboard region"&gt;</code>
                </li>
              </ol>
            </li>
            <li>
              <code>&lt;div id="footer" class="region"&gt;</code>
            </li>
          </ol>
        </li>
      </ol>
    </li>
  </ol>
</div>

## Header region

The header is the first region, styled in [03-region-header.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/03-region-header.css). It contains our branding, the main navigation, and depending on whether or not you are logged in, the login or greeting block.

<div class="diagram">
  <ol>
    <li>
      <code>&lt;div id="header" class="region"&gt;</code>
      <ol>
        <li>
          <code>&lt;h1 class="heading"&gt;</code>
            <ol>
              <li>
                <code>&lt;a&gt;</code>
                <ol>
                  <li>
                    <code>&lt;span&gt;</code>
                  </li>
                  <li>
                    <code>&lt;sup&gt;</code>
                  </li>
                  <li>
                    <code>&lt;img&gt;</code>
                  </li>
                </ol>
              </li>
            </ol>
          </li>
        <li><code>&lt;div id="<a href="#login-block">login</a> or <a href="#greeting-block">greeting</a>"&gt;</code></li>
        <li>
          <code>&lt;h3 class="landmark heading"&gt;</code>
        </li>
        <li>
          <code>&lt;ul class="primary navigation actions"&gt;</code>
          <ol>
            <li>
              <code>&lt;li class="dropdown"&gt;</code>
              <ol>
                <li>
                  <code>&lt;a class="dropdown-toggle"&gt;</code>
                </li>
                <li>
                  <code>&lt;ul class="menu dropdown-menu"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;li&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;a&gt;</code>
                        </li>
                      </ol>
                    </li>
                    <li>
                      <code>&lt;li&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;a&gt;</code>
                        </li>
                      </ol>
                    </li>
                    <li>...</li>
                  </ol>
                </li>
              </ol>
            </li>
            <li>
              <code>&lt;li class="search"&gt;</code>
              <ol>
                <li>
                  <code>&lt;form id="search" class="search"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;fieldset&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;legend&gt;</code>
                        </li>
                        <li>
                          <code>&lt;p&gt;</code>
                          <ol>
                            <li>
                              <code>&lt;label class="landmark"&gt;</code>
                            </li>
                            <li>
                              <code>&lt;input id="site_search" class="text" type="text"&gt;</code>
                            </li>
                            <li>
                              <code>&lt;span class="tip"&gt;</code>
                            </li>
                            <li>
                              <code>&lt;span class="submit actions"&gt;</code>
                              <ol>
                                <li>
                                  <code>&lt;input class="button" type="submit"&gt;</code>
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
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;div class="clear"&gt;</code>
        </li>
      </ol>
    </li>
  </ol>
</div>

The hyphenated class names are not in the view files and are only applied when the user has JavaScript enabled; therefore, they should not be used for styling the header elements.

## Login block

The login block consists of a link that summons the small login form when the user has JavaScript enabled or that takes the user to the log in page when they have JavaScript disabled.

<div class="diagram">
  <ol>
    <li>
      <code>&lt;div id="login" class="dropdown"&gt;</code>
      <ol>
        <li>
          <code>&lt;p class="user actions"&gt;</code>
          <ol>
            <li>
              <code>&lt;a class="dropdown-toggle"&gt;</code>
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;div id="small_login" class="simple login"&gt;</code>
          <ol>
            <li>
              <code>&lt;form id="new_user_session"&gt;</code>
              <ol>
                <li>
                  <code>&lt;dl&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;dt&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;label&gt;</code>
                        </li>
                      </ol>
                    </li>
                    <li>
                      <code>&lt;dd&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;input class="text" type="text"&gt;</code>
                        </li>
                      </ol>
                    </li>
                    <li>
                      <code>&lt;dt&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;label&gt;</code>
                        </li>
                      </ol>
                    </li>
                    <li>
                      <code>&lt;dd&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;input class="text" type="text"&gt;</code>
                        </li>
                      </ol>
                    </li>
                  </ol>
                </li>
                <li>
                  <code>&lt;p class="submit actions"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;label class="action"&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;input type="checkbox"&gt;</code>
                        </li>
                      </ol>
                    </li>
                    <li>
                      <code>&lt;input type="submit"&gt;</code>
                    </li>
                  </ol>
                </li>
                <li>
                  <code>&lt;ul class="footnote actions"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;li&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;a&gt;</code>
                        </li>
                      </ol>
                    </li>
                    <li>
                      <code>&lt;li&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;a&gt;</code>
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
    </li>
  </ol>
</div>

### Greeting block

The greeting block contains the user's icon and navigation items that are only available to logged in users.

<div class="diagram">
  <ol>
    <li>
      <code>&lt;div id="greeting"&gt;</code>
      <ol>
        <li>
          <code>&lt;h3 class="landmark heading"&gt;</code>
        </li>
        <li>
          <code>&lt;ul class="user navigation actions"&gt;</code>
          <ol>
            <li>
              <code>&lt;li class="dropdown"&gt;</code>
              <ol>
                <li>
                  <code>&lt;a class="dropdown-toggle"&gt;</code>
                </li>
                <li>
                  <code>&lt;ul class="menu dropdown-menu"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;li&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;a&gt;</code>
                        </li>
                      </ol>
                    </li>
                  </ol>
                </li>
              </ol>
            </li>
            <li>
              <code>&lt;li class="dropdown"&gt;</code>
              <ol>
                <li>
                  <code>&lt;a class="dropdown-toggle"&gt;</code>
                </li>
                <li>
                  <code>&lt;ul class="menu dropdown-menu"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;li&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;a&gt;</code>
                        </li>
                      </ol>
                    </li>
                    <li>
                      <code>&lt;li&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;a&gt;</code>
                        </li>
                      </ol>
                    </li>
                  </ol>
                </li>
              </ol>
            </li>
            <li>
              <code>&lt;li&gt;</code>
              <ol>
                <li>
                  <code>&lt;a&gt;</code>
                </li>
              </ol>
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;p class="icon"&gt;</code>
          <ol>
            <li>
              <code>&lt;a&gt;</code>
              <ol>
                <li>
                  <code>&lt;img class="icon"&gt;</code>
                </li>
              </ol>
            </li>
          </ol>
        </li>
      </ol>
    </li>
  </ol>
</div>

## Dashboard region

The dashboard is the second region, styled in [04-region-dashboard.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/04-region-dashboard.css). It does not appear on every page, but when it *is* on the page, it comes after the header and before the main region.

<div class="diagram">
  <ol>
    <li>
      <code>&lt;div id="dashboard" class="region"&gt;</code>
      <ol>
        <li>
          <code>&lt;h4 class="landmark heading"&gt;</code>
        </li>
        <li>
          <code>&lt;ul class="navigation actions"&gt;</code>
          <ol>
            <li>
              <code>&lt;li&gt;</code>
              <ol>
                <li>
                  <code>&lt;a&gt;</code>
                </li>
              </ol>
            </li>
            <li>
              <code>&lt;li&gt;</code>
              <ol>
                <li>
                  <code>&lt;a&gt;</code>
                </li>
              </ol>
            </li>
            <li>
              <code>&lt;li&gt;</code>
              <ol>
                <li>
                  <code>&lt;span class="current"&gt;</code>
                </li>
              </ol>
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;h4 class="landmark heading"&gt;</code>
        </li>
        <li>
          <code>&lt;ul class="navigation actions"&gt;</code>
        </li>
      </ol>
    </li>
  </ol>
</div>

## Main region

The structure of `#main` varies significantly from page to page. Most of the remaining stylesheets deal with elements found in main; the [05-region-main.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/05-region-main.css) stylesheet only covers very basic styles, like how wide it should be when appearing with a dashboard (`#main.dashboard`).

The structure of an individual page's main region is commented in the views. Each section is announced by a heading, although many of these headings are not displayed in the Archive default style; these are called landmarks. Like the skip links, they are designed to help users of assistive technology jump around on the page.

```html
<!--Descriptive page name and system messages, descriptions, and instructions.-->
<h2> </h2>

<!--Subnavigation, sorting and actions.-->
<h3 class="landmark"> </h3>

<!--main content-->
<h3 class="landmark"> </h3>

<!--Subnavigation, sorting and actions.-->
<h3 class="landmark"> </h3>
```

### Example structure

Here's a brief look at the structure of a filterable work index, like the [work index for The X-Files](https://archiveofourown.org/tags/The%20X-Files/works):

<div class="diagram">
  <ol>
    <li>#main
      <ol>
        <li>h2</li>
        <li>h3 .landmark</li>
        <li>ul .navigation
          <ol>
            <li>li <span>a</span></li>
            <li>li <span>span .current</span></li>
          </ol>
        </li>
        <li>h4 .landmark</li>
        <li>ol .pagination
          <ol>
            <li>li .previous <span>a</span></li>
            <li>li <span>span .current</span></li>
            <li>li <span>a</span></li>
            <li>li...</li>
            <li>li .next <span>a</span></li>
          </ol>
        </li>
        <li>h3 .landmark</li>
        <li>ol .work index
          <ol>
            <li>blurb</li>
            <li>blurb</li>
            <li>blurb</li>
            <li>blurb...</li>
          </ol>
        </li>
        <li>form .filters
          <ol>
            <li>h3 .landmark</li>
            <li>fieldset
              <ol>
                <li>legend</li>
                <li>dl .filters
                  <ol>
                    <li>dt .landmark</li>
                    <li>dd .submit <span>input</span></li>
                    <li>dt</li>
                    <li>dd</li>
                    <li>dt...</li>
                    <li>dd...</li>
                    <li>dt .landmark</li>
                    <li>dd .submit <span>input</span></li>
                  </ol>
                </li>
              </ol>
            </li>
          </ol>
        </li>
        <li>h4 .landmark</li>
        <li>ol .pagination
          <ol>
            <li>li .previous <span>a</span></li>
            <li>li <span>span .current</span></li>
            <li>li <span>a</span></li>
            <li>li...</li>
            <li>li .next <span>a</span></li>
          </ol>
        </li>
        <li>div .clear</li>
      </ol>
    </li>
  </ol>
</div>

Other indices on the Archive, such as [a tag's bookmark index](https://archiveofourown.org/tags/The%20X-Files/bookmarks) and [the collections index](https://archiveofourown.org/collections), follow the same pattern. There are also variations of it that don't have filters, such as [the main works index](https://archiveofourown.org/works), or that have filters and a dashboard, such as [a user's bookmark index](https://archiveofourown.org/users/testy/bookmarks).

## Footer region

The footer is the final region, and its styles are in [06-region-footer.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/06-region-footer.css).

<div class="diagram">
  <ol>
    <li>
      <code>&lt;div id="footer" class="region"&gt;</code>
      <ol>
        <li>
          <code>&lt;h3 class="landmark heading"&gt;</code>
        </li>
        <li>
          <code>&lt;ul class="navigation actons"&gt;</code>
          <ol>
            <li>
              <code>&lt;li class="module group"&gt;</code>
                <ol>
                  <li>
                    <code>&lt;h4 class="heading"&gt;</code>
                    <ol>
                      <li>
                        <code>&lt;ul class="menu"&gt;</code>
                        <ol>
                          <li>
                            <code>&lt;li&gt;</code>
                            <ol>
                              <li>
                                <code>&lt;a&gt;</code>
                              </li>
                            </ol>
                          </li>
                        </ol>
                      </li>
                      <li>
                        <code>&lt;ul class="menu"&gt;</code>
                      </li>
                    </ol>
                  </li>
                </ol>
            </li>
            <li>
              <code>&lt;li class="module group"&gt;</code>
            </li>
          </ol>
        </li>
      </ol>
    </li>
  </ol>           
</div>
