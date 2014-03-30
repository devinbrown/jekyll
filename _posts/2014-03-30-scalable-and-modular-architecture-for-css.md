---
layout: post
title:  "notes::smacss"
date:   2014-03-30
categories: notes
---

Scalable and Modular Architecture for CSS: http://smacss.com/.

## Base Rules

These are the *defaults*. They are almost exclusively single element selectors
but it could include attribute selectors, pseudo-class selectors, child selectors
or sibling selectors. Essential, a base style says that wherever this element is
on the page, it should look like *this*.

Base styles include setting heading sizes, default link styles, default font
styles, and body backgrounds.

## Layout Rules

**Layout rules** divide the page into sections.

>Generally, a Layout style only has a single selector: a single ID or class name.

Two types of layout components:

1. Major components (the "master layout" of the page)
2. Minor components (login form, navigation item, etc.)

>From a layout perspective, all we care about is how each item relates to each other.

## Module Rules

The module is a more discrete component of the page. It is your navigation bars
and your carousels and your dialogs and your widgets and so on. This is the meat
of the page. Modules sit inside Layout components. Modules can sometimes sit
within other Modules, too. Each Module should be designed to exist as a
standalone component. In doing so, the page will be more flexible. If done right,
Modules can easily be moved to different parts of the layout without breaking.

>When defining the rule set for a module, avoid using IDs and element selectors, sticking only to class names.

### *Children, Siblings, Descendants*

It will select any list items that are anywhere underneath an unordered list in
the markup structure. The list item could be buried three levels deep within
other nested lists, and this selector will still match it.

{% highlight css %}
  ul li { margin: 0 0 5px 0; } <!-- descendent selector -->
{% endhighlight %}

This means it will only select list items that are direct children of an
unordered list. In otherwords, **it only looks one level down the markup structure,
no deeper**. So if there was another unordered list nested deeper, the list item
children of it will not be targeted by this selector.

{% highlight css %}
  ul > li { margin: 0 0 5px 0; } <!-- child combinator selector -->
{% endhighlight %}

c.f. [css-tricks.com/child-and-sibling-selectors/](http://css-tricks.com/child-and-sibling-selectors/)

### *Battling Against Specificity*

To avoid the specificity battle, we should instead recognize that the constrained
layout in the layout module is a subclass of the sub-module and style it accordingly.

{% highlight css %}
  .pod {
      width: 100%;
  }
  .pod input[type=text] {
      width: 50%;
  }
  .pod-constrained input[type=text] {
      width: 100%;
  }

  .pod-callout {
      width: 200px;
  }
  .pod-callout input[type=text] {
      width: 180px;
  }
{% endhighlight %}

>If load order is a factor in your project, watch out for specificity issues.
