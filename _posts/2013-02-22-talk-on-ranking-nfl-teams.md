---
layout: post
title: Talk on Ranking NFL Teams
date: '2013-02-22T20:34:02-08:00'
tags: []
tumblr_url: https://seanjtaylor.tumblr.com/post/43765697820/talk-on-ranking-nfl-teams
redirect_from: /post/43765697820/talk-on-ranking-nfl-teams
---
I gave [a talk last month](http://www.meetup.com/nyhackr/events/99758422/) at the [New York Open Statistical Programming Meetup](http://www.meetup.com/nyhackr/ "New York Open Statistical Programming Meetup - New York, NY")&nbsp;on ranking systems, specifically applied to the NFL. You can find [slides](http://seanjtaylor.github.com/NFLRanking/web/slides/), [code](https://github.com/seanjtaylor/NFLRanking), and an [IPython notebook](http://nbviewer.ipython.org/urls/raw.github.com/seanjtaylor/NFLRanking/master/NFL%2520Rankings.ipynb) which contains most of the information. I encourage you to look at the slides, which I spent a lot of time on. &nbsp;They contain two embedded [interactive](http://seanjtaylor.github.com/NFLRanking/web/slides/#/6/2) [visualizations](http://seanjtaylor.github.com/NFLRanking/web/slides/#/13/1). &nbsp;I did get my Super Bowl prediction wrong, though.

There were about 200 attendees, but unfortunately&nbsp;there is no video of the talk. Thanks to everyone who came; it was incredibly fun for me.

The talk was mostly a review/comparison of different methods:

- Pythagorean wins
- Eigenvector methods
- the Bradley-Terry-Luce model
- optimal rankings

The last one warrants more explanation. &nbsp;I had [previously reviewed](http://seanjtaylor.com/post/36149816687/optimal-descriptive-nfl-rankings) the optimal descriptive ranking problem and my solution. &nbsp;It’s a fascinating application of graph theory to a problem that most people wouldn’t consider to be graph-theoretic. &nbsp;Once the ranking problem is posed as a topological sort of a graph which contains cycles, it’s easy to describe an exact (if non-unique) solution as well as find an algorithm to approximate it. &nbsp;The results are quite stunning: a 10+% increase in the number of correctly described games from the other models.

