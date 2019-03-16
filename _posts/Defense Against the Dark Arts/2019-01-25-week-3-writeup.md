---
layout: default
title:  "Week 3 Writeup"
date:   2019-01-25
category: [Defense Against the Dark Arts]

---

# {{page.title}}

#### [{{page.category}}](/blog/#{{page.category[0] | downcase | url_escape | strip | replace: ' ', '-' }})&mdash;{{ page.date | date: "%B %-d, %Y" }} 

----

This week finally felt like I was firing on all cylinders for both the material and the lab. The week's focus was mostly on malware defense and high level concepts in multi-level coverage as well as an introduction to Yara, a language-based approach to malware categorization and identification. Overall I had a much easier time processing this information at a theoretical level as well as putting it into practice by using Yara to filter malware from regular system files.

At a glance malware these days seems to take on the form many other applications take: a full stack of different software inter operating. This makes enough sense I think; in order to combat malware coming from these types of applications, you'll need coverage at all levels (network firewall and analysis, system firewall, system memory analysis, and system file scanning to name a few notable levels) in order to stand a chance at malware that will utilize any and all of these levels to propagate. Gone are the days of only static file analysis or a firewall that can protect you from a majority of threats. As technology pushes forward I would suspect that this trend will continue; more complex technology will bring more complex attacks.

I really felt like the Yara lab where we tried to catch three malware files but not hit anything else in the system (I used System32) was the first part of this class to "speak my language" (bad pun I know, as it *is* a language). This was something with a simple syntax and a lot of power as a result of string matching logic, and it was easily to test and augment. With a little bit of help from FileInsight's string script and Notepad++ to help with searching/filtering candidate strings, I made fairly quick work of all three samples in the Yara lab. At the end of the day I see a lot of power to Yara: it has simple syntax and well-recognize logical operators that search through an executable in order to classify it from the many system binaries that make up normal operating system operations. Without a tool like this we would have to search by hand through all system files in order to identify malware, and this is a task that would likely leave defenders well behind the aggressive pace of attackers.

As I look back at the week I'm definitely looking forward to doing more with Yara and defense in general. The analysis and volatility is both good to know and has its uses, but as I don't plan to be a malware inspector or forensics investigator the applications of related tools will likely not be as useful as something like Yara. Defense in general is a topic any user can know more about, and certainly its something every programmer should be thinking of whenever they design systems that could potentially be exploited. I did find it interesting that again whenever a student suggested education as a potential means of avoiding malware, this idea was dismissed with an air of silliness about it. Is this because it is truly hopeless to educate everyone about how to protect themselves? Or perhaps malware researchers and practitioners just see software as a more fruitful endeavor than education? That's a question I'll continue to keep in the back of my mind as the course continues.