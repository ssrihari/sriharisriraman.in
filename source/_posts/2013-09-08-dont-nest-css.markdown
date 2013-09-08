---
layout: post
title: "Don't nest CSS"
date: 2013-09-08 12:16
comments: true
categories: 
---

**TL;DR:**  Don't nest CSS. Nest class names instead. This is one of the most useful take-aways from [SMACSS](http://smacss.com).
Follow this, and it will change the way you write scss for the better.


With the coming of [sass](http://sass-lang.com/),  we have all seen how writing css has gotten easier.
We love writing css that is similar to our html. The following would seem natural to us:

```html HTML for a component
<div class="my-component">
  <header></header>
  <div class="some-section">
    <header></header>
    <p class="description">
      <span class="important"></span>
    </p>
  </div>
</div>
```

```sass Styling the component (the wrong way)
div.my-component {
  header {}
  .some-section {
    header {}
    p {
      .important {}
    }
  }
}
```
This gives us the comfort of nesting css the same way we nest html. It gives us context that
`some-section` rests inside `my-component`, but nothing more. And, this gets convoluted quickly. if I had to override the style for this component elsewhere, I'd have to do something like:
```sass Overriding the style for .important
.my-component .some-section p .important {}
```

# The correct way:
Add the context, name of component/module in the class attribute:
```html HTML for a component
<div class="my-component">
  <header class="my-component-header"></header>
  <div class="my-component-section">
    <header class="my-component-section-header"></header>
    <p class="my-component-section-description">
      <span class="my-component-section-important"></span>
    </p>
  </div>
</div>
```

```sass Styling the component (the correct way)
.my-component {}
.my-component-header {}
.my-component-section {}
.my-component-section-header {}
.my-component-section-description {}
.my-component-section-important {}
```

###What does this give us?
  - All the context that we got in nesting css. Except that the nesting is in the name instead of nested braces that are hard to read.
  - CSS with minimum specificity so that it is easy to override. For the purpose of subclassing modules, it is preferable to nest the styling by exactly one level. See exceptions below.
  - Independence from structure, so we can move our components around without having to move css around. For this purpose, it is also good to stay away from element selectors.
  - Control over cascading, that you thought was only possible [with nesting](http://37signals.com/svn/posts/3003-css-taking-control-of-the-cascade). The nesting in class names gives a unique name to your selector that is quite hard to override accidentally with cascading.
  - The answer to "Where is the CSS for this?". Since the selectors have almost a one to one mapping with the class attributes, you just have to file-search for them now.
  - Speed. See how this helped [github](https://speakerdeck.com/jonrohan/githubs-css-performance?slide=11) speed up their diff pages.

###Conclusion:
Don't nest CSS. You could start off with the [inception rule](http://thesassway.com/beginner/the-inception-rule), but I strongly suggest you stick to zero nesting levels (see exceptions below).

###Exceptions:
 - When you are writing modules that you will [subclass](http://smacss.com/book/type-module#subclassing), it is necessary to nest (by one level) the styling under the module's selector so that you can keep the defaults and override only the differences.
 - When overriding [base rules](http://smacss.com/book/type-base), one usually has to provide enough specificity to override an element selector, say. In these cases, nesting (by one level) is ok.
