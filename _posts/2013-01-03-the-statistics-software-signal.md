---
layout: post
title: The Statistics Software Signal
date: '2013-01-03T11:52:00-08:00'
tags: []
tumblr_url: https://seanjtaylor.tumblr.com/post/39573264781/the-statistics-software-signal
redirect_from: /post/39573264781/the-statistics-software-signal
---
Last night on Twitter, I went on a bit of a rant about statistics packages (namely Stata and SPSS). &nbsp;My point was not that these software packages are bad per se, but that I have found them to be correlated with bad quality science. &nbsp;Here is my theory why.

<!-- more -->

1. **When you don’t have to code your own estimators, you probably won’t understand what you’re doing.** I’m not saying that you definitely won’t, but push-button analyses make it easy to compute numbers that you are not equipped to interpret.
2. **When it’s extremely low cost to perform inference, you are likely to perform a lot of inferences.&nbsp;** When your first regression gives a non-result, you run a second one, and a third one, etc. This leads untrained researchers to run into [multiple comparisons problems](http://en.wikipedia.org/wiki/Multiple_comparisons) and increases the risk of Type I errors.
3. **When operating software doesn’t require a lot of training, users of that software are likely to be poorly trained.&nbsp;** This is an [adverse selection issue](http://en.wikipedia.org/wiki/Adverse_selection). Researchers who care about statistics enough should have gravitated toward R at some point. &nbsp;I also trust results produced using R, not because it is better software, but because it is difficult to learn. &nbsp;The software is not causing you to be a better scientist, but better scientists will be using it.
4. **When you use proprietary software, you are sending the message that you don’t care about whether people can replicate your analyses or verify that the code was correct.&nbsp;** Most commercial software is closed source and expensive. &nbsp;We can never know if the statisticians at Stata have a bug in their code unless we trust them to tell us. &nbsp;Also consider researchers from schools or companies which can’t afford expensive commercial software. &nbsp;Should they not be able to reproduce your results?

I do think these packages are valuable can be used for good. I have used Stata and it has saved me plenty of time. &nbsp;My main point is that there are a number of mechanisms through which bad science can be correlated with&nbsp;using push-button statistics software, not that one is a direct consequence of the other.

* * *

What your statistical software says about you (to me):

- **R** : You are willing to invest in learning something difficult. &nbsp;You do not care about aesthetics, only availability of packages and getting results quickly.&nbsp;
- **Python or JVM languages** : You are a hacker who may have already been a programmer before you delved into statistics. You are probably willing to run alpha or beta-quality algorithms because the statistical package ecosystem is still evolving. You care about integrating your statistics code into a production codebase.
- **Julia** : You are [John Myles White](http://johnmyleswhite.com/).
- **Stata** : You are an economist who doesn’t care to code your own estimators, probably because your comparative advantage lies elsewhere. &nbsp;Possibly you are doing sophisticated work with panel data where Stata is the only game in town. &nbsp;You don’t care that you can’t do proper programming because you’re not a programmer.
- **SPSS** : You love using your mouse and discovering options using menus. You are nervous about writing code and probably manage your data in Microsoft Excel.
- **Matlab** : You definitely know what you’re doing and you care about performance. You know Matlab is expensive but you aren’t the one paying for it. You live in a bubble where everyone you know uses Matlab.
- **Mathematica** : You are an aesthete who [believes everything Stephen Wolfram says](http://blog.wolfram.com/2012/11/28/mathematica-9-is-released-today/).
- **SAS** : You are an analyst for a large pharmaceutical company, and SAS is all you have ever known. You have a large library of custom SAS macros, so that (clearly) makes you a programmer. That anyone would want to hand-code statistical methods leaves you utterly baffled. If SAS does not ship with a particular statistical method, then it probably isn’t important.&nbsp;(h/t [Chris Fonnesbeck](https://twitter.com/fonnesbeck))
