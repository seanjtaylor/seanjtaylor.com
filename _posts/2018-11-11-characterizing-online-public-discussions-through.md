---
layout: post
title: Characterizing Online Public Discussions through Patterns of Participant Interactions
date: '2018-11-11T14:17:43-08:00'
tags: []
tumblr_url: https://seanjtaylor.tumblr.com/post/180005514907/characterizing-online-public-discussions-through
redirect_from: /post/180005514907/characterizing-online-public-discussions-through
---
New Paper at [CSCW 2018](http://cscw.acm.org/2018/) with [Justine Zhang](http://tisjune.github.io/), Cristian Danescu-Niculescu-Mizil, and [Christy Sauper](https://research.fb.com/people/sauper-christy/) [[link to paper]](http://www.cs.cornell.edu/~cristian/Patterns_of_participant_interactions_files/patterns-of-participant-interactions.pdf)

Facebook has an incredible number of public (between non-friends) discussions that can grow quite large (# participants and # comments). A hard problem we face is understanding which discussions are going well for users. Imagine doing that for dozens of languages and use cases.

The topic of this paper is a natural extension of my work with [George Berry](https://georgeberry.github.io/) where [we study whether seeing higher quality comments causes people to write higher quality comments](https://seanjtaylor.com/post/157591122402/discussion-quality-diffuses-in-the-digital-public) (it does!). We had a very limited definition of “quality” in that paper that allowed us to focus on the social influence component.

The key idea in this new paper is to encode a discussion with multiple participants as a [hypergraph](https://en.wikipedia.org/wiki/Hypergraph). This is a generalization of earlier reply-tree and [sequence models of discussions](http://www.cs.cornell.edu/home/llee/papers/convcuration.home.html). We actually ignore text entirely and focus on interactions like reactions/replies.

<figure class="tmblr-full" data-orig-height="540" data-orig-width="1200"><img src="https://66.media.tumblr.com/221ef886e3ef41e752ca360aab233591/tumblr_inline_pi1mowW7fw1r1x9ql_540.jpg" data-orig-height="540" data-orig-width="1200"></figure>

From this hypergraph, we can extract a number of features and create a high-dimensional vector of discussion characteristics. An important idea that we employ is to count [subgraph motifs](https://en.wikipedia.org/wiki/Network_motif) that stylized types of interactions people can have in discussions.

<figure class="tmblr-full" data-orig-height="338" data-orig-width="1272"><img src="https://66.media.tumblr.com/741b89bfd1448c93da66479af3b7cba8/tumblr_inline_pi1mt8ekLP1r1x9ql_540.jpg" data-orig-height="338" data-orig-width="1272"></figure>

This high-dimensional representation of discussion structure can be easily embedded in low dimensions. What’s wild is that we can aggregate to the page level, finding certain types of pages are clearly associated with certain discussion structures. (No text/topics are used here!)

<figure class="tmblr-full" data-orig-height="638" data-orig-width="682"><img src="https://66.media.tumblr.com/9e6f957fe30fada77a32f3dfde220648/tumblr_inline_pi1mte3xZp1r1x9ql_540.jpg" data-orig-height="638" data-orig-width="682"></figure>

Our discussion embeddings allow us to do some neat tricks, like characterizing whether a conversation “style” emerges from the topic itself or its initiator (the latter!). The discussion vectors are also excellent input features for classification tasks, like predicting blocks.

<figure class="tmblr-full" data-orig-height="715" data-orig-width="1200"><img src="https://66.media.tumblr.com/94ca4a3ba9999118ff36ca478759019b/tumblr_inline_pi1mtpvduw1r1x9ql_540.jpg" data-orig-height="715" data-orig-width="1200"></figure>

The takeaway here is that the patterns of interaction in comment threads provides incredibly useful signal about what kind of discussion is happening, both in a descriptive and predictive sense. Some dimensions also have clear human interpretations, which we discuss in the paper.

<figure class="tmblr-full" data-orig-height="1200" data-orig-width="1100"><img src="https://66.media.tumblr.com/f8eb45a524a425cc0958238ba5501c02/tumblr_inline_pi1mtzFZYL1r1x9ql_540.jpg" data-orig-height="1200" data-orig-width="1100"></figure>

Our hypergraph representation of online public discussions is flexible, extensible, complementary to text representations, and (we think) is more agnostic to language/culture. [We also provide code that allows you to apply this method to Reddit data.](https://github.com/CornellNLP/Cornell-Conversational-Analysis-Toolkit/blob/master/hyperconvo_README.md)

<!-- more -->
## Abstract

Public discussions on social media platforms are an intrinsic part of online information consumption. Characterizing the diverse range of discussions that can arise is crucial for these platforms, as they may seek to organize and curate them. This paper introduces a computational framework to characterize public discussions, relying on a representation that captures a broad set of social patterns which emerge from the interactions between interlocutors, comments and audience reactions.We apply our framework to study public discussions on Facebook at two complementary scales. First, we use it to predict the eventual trajectory of individual discussions, anticipating future antisocial actions (such as participants blocking each other) and forecasting a discussion’s growth. Second, we systematically analyze the variation of discussions across thousands of Facebook sub-communities, revealing subtle differences (and unexpected similarities) in how people interact when discussing online content. We further show that this variation is driven more by participant tendencies than by the content triggering these discussions.

