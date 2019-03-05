---
layout: default
title:  "Another Category Test"
date:   2019-03-04 22:45:00 -0800
category: second
---
# {{page.title}}

#### [{{page.category}}](/blog/#{{page.category[0] | downcase | url_escape | strip | replace: ' ', '-' }})&mdash;{{ page.date | date: "%B %-d, %Y" }} 

Does this work?
Welcome to the second category!
Some stuff here I guess...
