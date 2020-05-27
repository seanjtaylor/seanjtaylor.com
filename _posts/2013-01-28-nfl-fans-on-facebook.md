---
layout: post
title: NFL Fans on Facebook
date: '2013-01-28T19:18:00-08:00'
tags: []
tumblr_url: https://seanjtaylor.tumblr.com/post/41740696607/nfl-fans-on-facebook
redirect_from: /post/41740696607/nfl-fans-on-facebook
---
[NFL Fans on Facebook](https://www.facebook.com/notes/facebook-data-science/nfl-fans-on-facebook/10151298370823859)  

I made a promise to myself when I interned at Facebook that I would write at least one blog post on the NFL. &nbsp;Today I got to publish it! &nbsp;Technically this was all quite trivial, mostly just aggregating users by teams and geography, then producing the maps using D3 (I had to rasterize them to post them on Facebook).

The NFL friendships thing involved a join on the social graph with the Like graph. &nbsp;If I had had more time, I would have looked for rivalries. &nbsp;My plan was to look for friendships that were unlikely holding relative geography fixed but changing the two teams. &nbsp;The idea was to look for some pairs of teams that despite having pairs of fans in close proximity are unlikely to have fan friendships.

The finding that winning is correlated with Likes is also interesting. &nbsp;To an economist, this would seem to be an excellent instrumental variable. &nbsp;(This is [not a new idea](http://www.nber.org/papers/w15497)). &nbsp;Conditional on the spread of the game, wins and losses are basically coin flips, and yet they seem to be correlated with big increases in team fan bases. This strategy could potentially be used to identify peer effects if one were willing to make a bundle of assumptions about dynamics.

