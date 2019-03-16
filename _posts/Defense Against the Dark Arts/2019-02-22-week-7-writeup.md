---
layout: default
title:  "Week 7 Writeup"
date:   2019-02-22
category: [Defense Against the Dark Arts]

---

# {{page.title}}

#### [{{page.category}}](/blog/#{{page.category[0] | downcase | url_escape | strip | replace: ' ', '-' }})&mdash;{{ page.date | date: "%B %-d, %Y" }}

----

This week was just plain old-fashioned fun for me. From a topic standpoint I think it was perhaps the one I planned on learning the least about-anyone who's used the internet with a decent understanding knows the risks and exploits associated with the internet-but I didn't expect the application of that knowledge to the URL classifier to be so much fun. I went pretty in-depth in that writeup, and if I get permission I may add it as another post to this portion of the site, but I would like to talk about some of my overall thoughts of the methods I used (and are used in the industry with better performance/optimizations) and what their impact really is on the bigger picture.

Long story short I took a machine learning and statistical approach to the malicious classifier lab, and to my knowledge the industry standard is mostly this with a combination of a few well-prepared rule based efforts. I think this is the best approach to the problem and I also think that it is the best use of modern machine learning, but there are a few caveats that warrant discussion. Furthermore I think this is one of the best efforts in web security, because as I noted last week I am going to have to at a certain level trust with other actors on the web and as a result of that I think the reputation based systems to sifting through URLs is a great way to ensure that I can trust the actors I am interacting with.

The pitfalls of the machine learning approach are starting to come through not just in this application area but many-these systems can be cleverly fooled if someone knows they are in place. As all basic neural network class I've seen seems to have cat picture identification at its core we'll use it as an example: a cleverly constructed picture that *clearly* looks to a human like a cat (and thus could be correctly classified) can be cleverly crafted to intentionally fool a machine learning algorithm with certain pixels being altered in a certain way. My first reaction was to think "well that's just because its image recognition, surely it can't work in X domain", but I think upon closer thought I realized like many machine learning students like myself and practitioners (who first discovered this frailty) these systems are susceptible to attacks much like any other system.

Once an attacker knows the features, or at least some of them, that are used in a machine learning algorithm they can do something akin to the post request with a SQL query exploit from another part of this week's content. We as a human may  not know how to craft a cat picture with a few clever changes to fool a high-accuracy classifier, but a computer can find these exploits given a smart algorithm and enough time. So what do we do about it? Do we just accept that the anti-malware effort will always require some human effort for even simple tasks such as URL classification? Certainly there will always be malware sites with clever enough URLs to fool even the best classifier (or malware that makes its way into some more seemingly-legitimate points of the web), but there also in the future may be websites what specifically exploit the kind of weaknesses in the algorithms that were previously discussed.

I think the answer is that we need to learn better how to test these systems and their exploits. I think that's all I'll say about it because its actually also going to be part of a proposal for another class, so its likely to end up somewhere on this site. I will also probably seek permission to at least post my approach and results to the tests that I ran with a fairly naive machine learning approach to this problem, without the code portion most likely. I'm looking forward to the next weeks in this class but I will say on the whole this may be the peak week for me as this topic is both interesting to me intellectually and challenging and fun when I am actually programming the pieces.