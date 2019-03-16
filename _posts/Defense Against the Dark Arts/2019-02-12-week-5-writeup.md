---
layout: default
title:  "Week 5 Writeup"
date:   2019-02-12
category: [Defense Against the Dark Arts]

---

# {{page.title}}

#### [{{page.category}}](/blog/#{{page.category[0] | downcase | url_escape | strip | replace: ' ', '-' }})&mdash;{{ page.date | date: "%B %-d, %Y" }} 

----

This week was focused on bootkits and rootkits and how an unsuspecting user may be fooled into allowing a hacker to have administrator privileges or simply bypass the need by being a part of the boot process. Its an interesting topic and on the whole I actually enjoyed this week as much as any other in the course, but the thing that really caught my attention and seems worth discussing is the whole secure boot business that came up briefly when the lecturer mentioned Microsoft's efforts to stop bootloaders from having a foot in the door.

The problem here is of course that it ignores a whole host of issues. First of all before Linux caught up and had Microsoft either sign their binaries or created their own keys to allow secure boot to work independently of Microsoft, they were effectively shoved out of the market on any piece of hardware with this in place, unless the user wanted to disable secure boot altogether, which obviously I'm not qualified to say is even possible on every system with it installed.

Issue two is perhaps the issue that I find more compelling, and its simply that secure boot doesn't verify anything other than I likely don't have some *low-level* boot kit in my software. That is to say; what stops the binary signed by Microsoft, Fedora, or anyone  else involved from containing some kind of malware? From privacy monitoring to information stealing, there's no guarantee that the person(s) working to make these keys has my best interest in mind. In fact, Microsoft is notorious for taking whatever dirty business practice they can against Linux, so who's to say they wouldn't target the users? Furthermore in recent years we are often not dealing with only security threats from small-time hackers trying to get a bootloader installed to control a small botnet for say DDOS attacks, but also from the large companies that hold much of our data are likely to sell or give it away in what are becoming all too common data breeches.

So who's to say my signed binary is safe? Is having Microsoft, or Fedora, or Ubuntu sign it and that signature matching a key my hardware vendor put onto my machine mean I'm safe? At the risk of sounding paranoid, no it doesn't. Nothing will replace an informed user who can monitor their PC and use it wisely to avoid malware in the first place. These security measures (and I know, the lecturer mentions it almost in passing, but I felt like it was given a little too much credence considering the paranoia associated with the rest of the class) are not sufficient to believe that no malware exists within the system, and indeed it is just a choice of who you trust, or rather when and where you decide to trust them...I've never met the guy who built my computer, and its likely those using secure boot haven't either.