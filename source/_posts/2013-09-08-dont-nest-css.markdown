---
layout: post
title: "Don't nest CSS"
date: 2013-09-08 12:16
comments: true
categories: 
published:falsegs
---

Make a claim here about this rule changing the way you write scss.
Say how this is primarily a [smacss](http://smacss.com) inspiration.

TL;DR:
- Don't nest css
- Don't nest css at all

With the coming of [sass](http://sass-lang.com/) and scss,  we have all seen how writing css has gotten easier.
We love writing css that is similar to our html.

Give better example here of a module, with classes
```html HTML for a section
 <section>
    <header></header>
    <article>
      <header></header>
    </article>
</section>
````

```sass Styling the section
section {
    header {}
    article {
      header {}
    }
}
```

```
give your proposed solution here with nested class names and non nested css
```

- Show generated css 
- Show specificity needed to be overridden
- 
- List of benefits of not nesting, nesting in name and keeping specificity to a minimum
  - context
  - speed [Link to github post about speed]
  - modularity
  - maintainability
  - readability
  - searchability

Link to this in one of previous points: http://37signals.com/svn/posts/3003-css-taking-control-of-the-cascade

The inception rule: http://thesassway.com/beginner/the-inception-rule
-> How I would keep the rule to 1 level of nesting

Perhaps link to rubyconf lightning talk
