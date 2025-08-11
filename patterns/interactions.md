---
layout: page
title: Interactions Pattern
parent: Design Patterns
nav_order: 2
redirect_from:
  - /front_end_coding/patterns/interactions
---
# Interactions Pattern
{: .no_toc}

Interactions are forms. The styles for forms and form elements are found in [07-interactions.css](https://github.com/otwcode/otwarchive/blob/master/public/stylesheets/site/2.0/07-interactions.css).

Interactions is an abstract [supertype](../classes-taxonomy#supertypes). That means you won't find an `interactions` class in our code. Instead, "interactions" is synonymous with the `form` element. So if we wanted all interactions to have a gray background, we would use `form { background: #ccc; }`.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
* TOC
{:toc}
</details>

## Rules

Unless a form is very simple, it should be broken down into logical sections using `<fieldset>`. For example, the [Work Search form](https://archiveofourown.org/works/search) is grouped into Work Info, Work Tags, Work Stats, and Search.

Each `<fieldset>` should be labeled with a `<legend>`. Some screen readers don't read form legends. For them, we repeat the legend text as a landmark heading, e.g. `<h3 class="landmark heading">`. If the legend text is more than a few words long, the form probably needs rearranging.

Inputs should be labeled. Most of the time, this means using `<label>`, but in some very simple or very complex forms (e.g., form tables on wrangling pages), it means using the `title` attribute on the `<input>` itself. A label should come *before* a text field (`<input type="text">` or `<textarea>`) or select menu (`<select>`) but *after* a radio button (`<input type="radio">`) or checkbox (`<input type="checkbox">`). A label may also surround a checkbox or radio button.

Form labels and controls are inline elements, which means they have to be wrapped in block level elements. We generally use [definition lists](http://www.w3schools.com/tags/tag_dl.asp) (`<dl>`) because the [term](http://www.w3schools.com/tags/tag_dt.asp) (`<dt>`) and [definition](http://www.w3schools.com/tags/tag_dd.asp) (`<dd>`) structure corresponds nicely to the typical `<label>Label</label>` and `<input>` structure of a form. However, if a form cannot be logically structured as terms and definitions, it can be structured as paragraphs.

Submit buttons are a type of control, so they also need to be wrapped in block level elements. Most forms only have one submit button -- they can use `<p class="submit">`. Forms with many submit buttons (e.g. the work form) can use `<ul class="actions">`.

## HTML diagram

The following diagram is adapted from the new work form. Note the use of the `.verbose` class, which should be applied directly to the `form` element when the form has four or more `fieldset` elements as direct children.

<div class="diagram">
  <ol>
    <li>
      <code>&lt;form class="verbose post"&gt;</code>
      <ol>
        <li>
          <code>&lt;p class="required notice"&gt;* Required information&lt;/p&gt;</code>
        </li>
        <li>
          <code>&lt;fieldset&gt;</code>
          <ol>
            <li>
              <code>&lt;legend&gt;Tags&lt;/legend&gt;</code>
            </li>
            <li>
              <code>&lt;h3 class="landmark heading"&gt;Tags&lt;/h3&gt;</code>
            </li>
            <li>
              <code>&lt;p class="note"&gt;Tags are comma separated, 100 characters per tag.&lt;/p&gt;</code>
            </li>
            <li>
              <code>&lt;dl&gt;</code>
              <ol>
                <li>
                  <code>&lt;dt class="required"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;label&gt;Rating*&lt;/label&gt;</code>
                    </li>
                  </ol>
                </li>
                <li>
                  <code>&lt;dd class="required"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;select&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;option&gt;Not Rated&lt;/option&gt;</code>
                        </li>
                        <li>
                          <code>&lt;option...</code>
                        </li>
                      </ol>
                    </li>
                  </ol>
                </li>
                <li>
                  <code>&lt;dt class="required"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;label&gt;Archive Warning*&lt;/label&gt;</code>
                    </li>
                  </ol>
                </li>
                <li>
                  <code>&lt;dd class="required"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;fieldset&gt;</code>
                      <ol>
                        <li>
                          <code>&lt;ul&gt;</code>
                          <ol>
                            <li>
                              <code>&lt;li&gt;
                                <span>&lt;input type="checkbox"&gt;</span>
                                <span>&lt;label&gt;Choose Not To Use Archive Warnings&lt;/label&gt;</span>
                              </code>
                            </li>
                            <li>
                              <code>&lt;li...</code>
                            </li>
                          </ol>
                        </li>
                      </ol>
                    </li>
                  </ol>
                </li>
                <li>
                  <code>&lt;dt class="required"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;label&gt;Fandoms*&lt;/label&gt;</code>
                    </li>
                  </ol>
                </li>
                <li>
                  <code>&lt;dd class="required"&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;input type="text"&gt;</code>
                    </li>
                    <li>
                      <code>&lt;p class="footnote"&gt;This is information about the field.&lt;/p&gt;</code>
                    </li>
                  </ol>
                </li>
              </ol>
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;fieldset&gt;</code>
          <ol>
            <li>
              <code>&lt;legend...</code>
            </li>
            <li>
              <code>&lt;h3 class="landmark heading"...</code>
            </li>
            <li>
              <code>&lt;dl&gt;</code>
              <ol>
                <li>
                  <code>&lt;dt...</code>
                </li>
                <li>
                  <code>&lt;dd...</code>
                </li>
              </ol>
            </li>
          </ol>
        </li>
        <li>
          <code>&lt;fieldset&gt;</code>
          <ol>
            <li>
              <code>&lt;legend&gt;Post&lt;/legend&gt;</code>
            </li>
            <li>
              <code>&lt;h3 class="landmark heading"&gt;Post&lt;/h3&gt;</code>
            </li>
            <li>
              <code>&lt;ul class="actions"&gt;</code>
              <ol>
                <li>
                  <code>&lt;li&gt;</code>
                  <ol>
                    <li>
                      <code>&lt;input type="submit"&gt;</code>
                    </li>
                  </ol>
                </li>
                <li>
                  <code>&lt;li...</code>
                </li>
              </ol>
            </li>
          </ol>
        </li>
      </ol>
    </li>
  </ol>
</div>
