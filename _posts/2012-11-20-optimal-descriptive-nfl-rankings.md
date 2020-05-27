---
layout: post
title: Optimal Descriptive NFL Rankings
date: '2012-11-20T13:47:00-08:00'
tags: []
tumblr_url: https://seanjtaylor.tumblr.com/post/36149816687/optimal-descriptive-nfl-rankings
redirect_from: /post/36149816687/optimal-descriptive-nfl-rankings
---
Most NFL fans, like myself, obsess over who’s going to win games or which players to start in our fantasy football leagues. One of the fundamental tools we use to look at this are rankings. Rankings are the simplest possible model that can represent a [total order](http://en.wikipedia.org/wiki/Total_order), which you can think of as a function that allows you to compare all possible pairs in your set.

**Update** : Though I came up with this on my own, this idea is pretty old. See [Ali, Cook and Kress (1986)](http://pubsonline.informs.org/doi/abs/10.1287/mnsc.32.6.660). Next time I’ll spend some more time on Google Scholar :)

<!-- more -->

# Describing the NFL season

In the NFL regular season, each of the 32 teams plays 16 games. The result is 256 binary outcomes, which if we assume are the same as coin flips (independent trials of a fair coin), then the entirety of the season contains at most 256 bits of [information](http://en.wikipedia.org/wiki/Entropy_(information_theory)). One way to think about this is that if you could send yourself a string of 256 1s or 0s from January back in time to Septmeber, with a simplistic coding scheme, your past self could correctly predict all 256 games.

I began to [think](https://twitter.com/seanjtaylor/status/256560211370848256): we all love rankings, but how well can you describe the season with a ranking of teams? There are 32! possible rankings, so a ranking of all 32 teams contains log2(32!) bits of information, or about 118 bits. This is the smallest amount of information you could use to describe what happens in all possible pairings of teams. How accurate is it to describe 256 bits with 118 bits? How many games would you get wrong?

This is also a good way to look at how random outcomes are. If rankings can’t describe the season well, then it’s hard to have a good intuition about which teams are the best in the league.

# Ranking algorithms

Given my training in statistics and love of the NFL, I have [tried ranking teams before](http://dehype.posterous.com/2011-regular-season-power-rankings). The model I used then is a variant of the [BTL model](http://www.mathpsyc.uni-bonn.de/doc/Maris/node25.html). These models essentially posit that teams can be assigned a real number that represents their strength (they exist in a latent “quality” space), and that the probability of team A beating team B is proportional to the differences in their strengths. Essentially this is a logistic regression with dummy variables for teams.

As I looked into the [mathematics of ranking](http://www.math.utah.edu/~keener/lectures/rankings.pdf), I found that many smart people have thought long and hard about this problem. The abstract problem is how to take a series of [pairwise comparisons](http://en.wikipedia.org/wiki/Pairwise_comparison) and generate a total order relation.

The tricky bit is that these problems have a recursive structure: first you rank teams naively, then you re-rank adjusting for strength of schedule from your naive ranking, then you re-rank using the new strengths, and so forth. It’s no surprise then that most sophisticated ranking procedures use something like the [power method](http://en.wikipedia.org/wiki/Power_method) to compute eigenvectors of a square matrix that encodes the pairwise comparisons.

The BTL model is probabilistic, while the eigenvector model is derived using linear algebra. They are computed differently but there is a deep relationship between the two in that they optimize very similar objective functions.

# Optimal ranking with graphs

The pairwise comparison matrix (the element at row i, column j is 1 if i beat j) is also a [representation](http://en.wikipedia.org/wiki/Adjacency_matrix) for a directed graph. Using this representation, the ranking problem can then be posed slightly differently.

In the BTL model and the eigenvector model, we wanted to project each team onto the real line. If we think of our pairwise comparisons as constituting a directed graph, then the ranking is actually a [path](http://en.wikipedia.org/wiki/Path_(graph_theory)) through the graph. At first I thought this path might be related to the [TSP](http://en.wikipedia.org/wiki/Travelling_salesman_problem) with appropriate edge-weights, but this was a bit off.

The algorithm to find this path is called a [topological sort](http://en.wikipedia.org/wiki/Topological_sorting), the directed graph equivalent of a minimum spanning tree for an undirected graph. The problem is, you can’t perform a topological sort when there are cycles in the graph. Cycles are a generalization of transitivity violations: situation where A beat B, B beat C, but C beat A. We can’t sort the graph if these exist. If they don’t, the sort can take place in linear time.

The set of edges (games) which introduce cycles into the graph is called the [feedback arc set](http://en.wikipedia.org/wiki/Feedback_arc_set) (FAS). You can think of this as the set of cases the ranking model is too simplistic to explain. It seems a bit backwards, but if we can get rid of all the upsets in advance, then we can rank the teams easily and quickly. Finding the minimum FAS is an NP-hard problem (of course!), but for a 256 edge graph, it’s not a problem to compute it with [igraph](http://igraph.sourceforge.net/) among others packages. The minimal FAS set is not guaranteed to be unique (for a trival example, the minimal FAS set for a 3-cycle can be any of the three edges [[1]](#id2)), so unfortuntately the ranking may not be unique.

After removing the FAS, the topological sort produces the optimal ranking in the following sense: no other ranking will make fewer mistakes when applied to the 256 games. This is essentially minimizing [0-1 loss](http://en.wikipedia.org/wiki/Loss_function) of the model, which is exactly our objective function if we want rankings that make the fewest mistakes. This ranking may not be unique, but you cannot describe the season better with any ranking model.

# Results

I implemented a few ranking systems in Python. You can checkout the [code on github](https://github.com/seanjtaylor/NFLRanking). What I find amazing is how poorly BTL and eigenvector methods compare, at least descriptively, to optimal ranking. These rankings only are only about 70-75% accurate, while optimal ranking almost always breaks 80%. This are about 10-20 games which would be considered upsets under BTL and eigenvector methods that would not be considered upsets under the optimal ranking.

# Visualizing

I put together a visualization of the win-matrix using [d3.js](http://d3js.org/). Squares are colored if the row team beat the column team. Our “loss” comes from wins that are inconsistent with our ranking model–any square beneath the diagonal. You can also look at a [bigger](/nfl-win-matrix)&nbsp;and interactive&nbsp;version of the visualization.

Name&nbsp;Wins&nbsp;BTL&nbsp;Optimal Rank
Loss: 
<script src="http://d3js.org/d3.v2.min.js?2.8.1" type="text/javascript"></script><script src="http://static.tumblr.com/ewblwo4/tiEmdsw4v/graphics.js" type="text/javascript"></script><script src="http://static.tumblr.com/ewblwo4/w2Pmdsw6x/run.graphics.js" type="text/javascript"></script>

# A Challenge: minimum description length

I have shown that, at least for the task of _description_, a graph-based algorithm which minimizes the correct loss function is superior to probabilistic models which don’t actually minimize the right thing. But the ranking is still not a perfect representation of the NFL season, getting about 20% of the games wrong on average. My question to you is: describe a 100% accurate encoding of the NFL season that uses the fewest possible bits. I have thought hard about this and still don’t have a satisfying answer.

