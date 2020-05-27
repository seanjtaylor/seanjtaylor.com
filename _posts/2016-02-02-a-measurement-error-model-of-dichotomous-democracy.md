---
layout: post
title: A Measurement Error Model of Dichotomous Democracy Status
date: '2016-02-02T21:48:18-08:00'
tags: []
tumblr_url: https://seanjtaylor.tumblr.com/post/138580817602/a-measurement-error-model-of-dichotomous-democracy
redirect_from: /post/138580817602/a-measurement-error-model-of-dichotomous-democracy
---
I’m not actually a political scientist, but I like to pretend I am sometimes. &nbsp;[Jay Ulfelder](https://dartthrowingchimp.wordpress.com/about/) and I just submitted a [draft of our paper to SSRN](http://papers.ssrn.com/sol3/papers.cfm?abstract_id=2726962) that you can check out. &nbsp;Here’s the abstract:

> We use a Bayesian measurement error model to derive a probabilistic measure of democracy from several existing dichotomous data sets. This approach accepts the premise that democracy may usefully be construed as a bivalent concept for certain theoretical and technical purposes, but it also makes more explicit our collective uncertainty about where some cases fall in that binary scheme. We believe the resulting data provide a firmer foundation than measures of countries’ degree of democracy for studies that require a dichotomous measure of regime type.

This allows us to do things like, measure the probabilistic concept like “an expert would say a country in a region is democratic,” borrowing information across time to produce plots like this one:

<figure data-orig-width="874" data-orig-height="492" class="tmblr-full"><img src="https://66.media.tumblr.com/4a36f553ae49b685e77704dd19e76f85/tumblr_inline_o1yag8pCco1r1x9ql_540.png" alt="image" data-orig-width="874" data-orig-height="492"></figure>
##   

<!-- more -->
## How we did it

This research is totally open and reproducible. &nbsp;We used R and Python as well as some&nbsp;[Stan](http://mc-stan.org/) to to implement our HMC estimation. &nbsp;The&nbsp;[code and the source data are available on github](https://github.com/ulfelder/democracy-measurement-model).

## How this came about

I met [Jay Ulfelder](https://dartthrowingchimp.wordpress.com/about/)&nbsp;on Twitter a couple years ago and we periodically discuss research over email. &nbsp;He emailed me last year to ask:

> Is there a statistical model or process you know that solves the following problem?
> 
> Say you have 2 to 5 more or less independent, binary measures of the same thing in a time-series cross-sectional data set. Let’s call those measures “votes” and think of them as each sources’ best guess at the yes/no status of each record on some feature of interest. Is there a way—probably some kind of Bayesian model that didn’t even exist when I was in grad school—to use those votes to generate a unified probabilistic measure or z-score or something similar of each case’s status?

I had an idea about how to do this right away: item-response models provide a nice framework for thinking about this and all we had to do was model the underlying time series process. Bayesian inference was a perfect fit for this problem.

