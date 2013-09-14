---
layout: post
title: "Drive repetition into design using modular CSS"
date: 2013-09-14 14:32
comments: true
categories: [css, design, nilenso]
published: false
---
Analogous to how better object modelling leads to robust software, modular CSS leads to better design. Here's how:

One of the principles of good design is **Repetition**. Having similar elements across pages of a website or a brochure improves usability and readability since users are familiar with the look and functionality of these elements. Repetition creates a *theme* for your design.

 The following sections detail how one can enforce repetition into design by writing modular CSS:

###Write base styles
Having a font-size for paragraphs, h1 and h2, foreground colors for links and some default spacing measurements go a long way in giving you consistency throughout your website. Don't bother getting these values correct up front. Just get the repetition in these properties across the site. Base styles could be like this:
```sass base styles
h2 {font-size, margin}
p {font-size, font-family}
a {color}
a:hover {color}
```
See smacss.com/base-rules for more on base styles.

###Have a color palette
Set the color for your headings, body text, borders, background, and pull this CSS out into a palette. Use them everywhere on the site. But beware: to show repetition in colors, you need to have only a few colors in your palette. Here's a palette sample:
```sass color palette sample
$border-color:
$heading-color:
$link-color:
$text-color:
$dark-text-color:
```

###Write minimal CSS first
Write the bare minimum CSS required to make the design look good. If you have an inkling that this might be reused elsewhere, this makes it easier for you to pull out the common properties. Add the bling later to a subclass.

Repeat html, repeat entire elements, repeat tone

###Extract modules
This obvious one is last for the reason that extracting modules is more of a design excercise and driving this with CSS isn't easy. But for completeness sake: Try to pull out modal dialogs, forms, widgets and page sections into modules.
