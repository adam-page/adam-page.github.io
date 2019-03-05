---
layout: default
title:  "Week 1 Writeup"
date:   2019-01-09
category: [Defense Against the Dark Arts]
---

# {{page.title}}

#### [{{page.category}}](/blog/#{{page.category[0] | downcase | url_escape | strip | replace: ' ', '-' }})&mdash;{{ page.date | date: "%B %-d, %Y" }} 

---

This week's course content seemed mostly focused on the introductory terms and materials to help me familiarize myself with how to talk about things and how to investigate things. Introductions to tools and best practices were also included, as well as industry best practices for students and researchers in the field of defending against the dark arts of computer malware.

Terminology is key in any field, and cyber security is no exception. Most people are familar with terms like malware, viruses, and countermeasures, but there were plenty of other terminology I found myself unfamiliar with. Goats, for example, are a system (usually a virtual machine) in which a suspected malware sample will be run on in order to determine the scope and nature of their attack. Attack vectors refer to the medium by which malware propagates, and while I was familiar with mathematical vectors this usage of the word was new.

Handling malware is obviously no trivial thing, and the best practices I encountered this week helped me to develop a good scope of some of the practices I can take while studying. Naming conventions of malware for example is typically Type.Platform.Family.Variant!Information, and gives a hierarchical method of referencing different variants of malware. Similarly the use of virtual machine is almost always a good idea, even though some further [reading](https://security.stackexchange.com/questions/9011/does-a-virtual-machine-stop-malware-from-doing-harm) indicated that this is not a completely secure interface when dealing with particularly clever samples. Nonetheless it seems to generally be a good practice (and virtual machine snapshots make it practical for repeated tests and returning to a safe environment), as is using "infected" as a zip password unless you plan to use Gmail...

Tooling is a useful part of an investigator's kit, and this week's introduction to FlyPaper, FakeNet, Process Monitor, Process Explorer, AntiSpy, and FileInsight. I found AntiSpy and FileInsight to be particularly useful; AntiSpy has a whole host of tools for analyzing processes, registers, and more which made tracking down what a process did simple. Process Monitor was similarly useful in this area, and allowed to see exactly what a process did and when. FileInsight was also particularly helpful as it allowed an executable to be processed and its strings and certain commands to be analyzed. This allowed me to get at least a general sense of what a sample was doing, and from there the other tools provided a more in depth look.

The final piece of this week's puzzle was Advanced Persistent Threats. In short the term refers to a malware attack where the attackers are organized, have a specific goal (or goals) in mind, and have the skills to create targeted attacks in order to attain their goal. These types of attacks can take place over a long period of time and will often target large corporations or governments, although recent Twitter news may have us believe that the target can also often be large populations. 

Overall I found the week to be quite informative and a good introduction to the tools and methods by which the rest of the quarter will flow. I do wish there was a required text, but I'm sure I'll be able to find something. If nothing else, I could always reread Kevin Mitnick's The Art of Deception.