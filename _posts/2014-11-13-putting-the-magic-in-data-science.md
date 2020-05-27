---
layout: post
title: Putting the Magic in Data Science
date: '2014-11-13T16:38:00-08:00'
tags:
- data science
redirect_from: /post/102556088392/putting-the-magic-in-data-science
tumblr_url: https://seanjtaylor.tumblr.com/post/102556088392/putting-the-magic-in-data-science
---
Here are slides from [my talk](https://qconsf.com/presentation/putting-magic-data-science-facebook) at [QCon](https://qconsf.com/) last week:

<iframe frameborder="0" height="400" marginheight="0" marginwidth="0" scrolling="no" src="//www.slideshare.net/slideshow/embed_code/41529485" width="476"></iframe>

Here’s my talk (which was not recorded) in a nutshell:

- If we want to be valuable as data scientists, we should aspire to create as many “how did they do that?” moments as we can. &nbsp;I call these “[hoverboards](http://i.imgur.com/tsaijGH.gif).” &nbsp;If we [just count things](https://twitter.com/fredbenenson/status/370222055083753473), we are being [terrible magicians](http://imgur.com/O8d9k8S). We probably don’t want to end up being the accountants of the 21st century.
- Furthermore, these moments of magic should have impact – they should **cause** strategic or tactical decisions that people make to change.
- I argue that magic in data science often comes from combining various “tricks” in novel ways. I describe four common tricks we use at Facebook, as well as a grab bag of others that I’ve found useful.
- Tricks alone are not enough. &nbsp;People have to **use** the technology you create. &nbsp;That requires considering what I call Data Science’s [last mile problem](http://en.wikipedia.org/wiki/Last_mile). How do we make the data inform/change people’s behaviors?
- I describe four important (non-exhaustive) last mile considerations: reliability, latency/interactivity, simplicity, and interestingness. Many of these are achieved not through data science alone, but by combining data science with tricks from software engineering, design, and computer science.

**What is Data Science?**

There’s one little side-argument I made that I’d like to cover here. One thing we have trouble agreeing on is [what data science actually is](http://drewconway.com/zia/2013/3/26/the-data-science-venn-diagram). My latest theory is we all work in different parts of technology pipeline (see below), which starts with academics publishing papers at conferences like KDD and NIPS and ends with non-experts getting utility from products and services we create. We’re all probably doing “data science” but it might look a lot different (pure math, problem discovery, design/visualization, engineering) depending on what stage you’re involved in.<figure class="tmblr-full" data-orig-height="365" data-orig-width="500" data-orig-src="https://66.media.tumblr.com/fbdfaac9bec5681d054f3adaaa2ab9ee/tumblr_inline_nezynmZU321r1x9ql.png"><img alt="image" src="https://66.media.tumblr.com/d17ff60a601691d976df9a5e6875b599/tumblr_inline_p7g030vARF1r1x9ql_540.png" data-orig-height="365" data-orig-width="500" data-orig-src="https://66.media.tumblr.com/fbdfaac9bec5681d054f3adaaa2ab9ee/tumblr_inline_nezynmZU321r1x9ql.png"></figure>

