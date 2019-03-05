---
layout: default
title:  "Week 4 Writeup"
date:   2019-02-03
category: [Defense Against the Dark Arts]

---

# {{page.title}}

#### [{{page.category}}](/blog/#{{page.category[0] | downcase | url_escape | strip | replace: ' ', '-' }})&mdash;{{ page.date | date: "%B %-d, %Y" }} 

—

This was a week of blanks filled and light bulbs illuminating, in a number of ways...

First of all the topic was one which everyone is likely familiar with: the buffer overrun exploit. Anyone with almost any experience in a C family language has probably heard of the security risks of C as you just can't validate input. The user can type in whatever they want, and if it exceeds your buffer then many functions in C will just keep writing, stopping the null terminator that should be at the end of your buffer, but more importantly writing into unknown memory space. The potential here (I honestly didn't realize this but probably should have since I took a course with Assembly) is to overwrite the EIP register. For those not familiar with CPU register basics, this is what is known as the instruction pointer. It is the point in memory the program will go to and execute next. It is all the power anyone needs, unless checks are in place, in order to take advantage of a system and gain "code execution", which for an eager student and researcher alike is apparently opening a calculator!

Of course anyone with even just computer *use* experience will probably realize that if I'm running code in the browser and it can open my computer's calculator without me realizing it, that's bad. To elaborate just a bit, if you can run a calculator you can run a command prompt, and from the command prompt you can do almost anything: even just a user's access is quite powerful, and of course an administrator basically spells doom for that machine if the attacker is sophisticated enough to take the advantage. I really had an "aha" moment with this one; like I said I knew about this kind of exploit, but not specifically how it would work. Of course this is not the only type of buffer overrun exploit, and certainly the instruction pointer isn't the only register that could be targeted...but it does certainly seem like the most obvious, and if security isn't in place to prevent it the easiest!

The rest of the week was how to use this knowledge to specifically get some JavaScript to do so followed by a discussion of Heap exploits and a similar lab. The freed object reuse based on a bucket allocation doesn't seem too abstract as I initially thought it would, although it did point out how little I know about things like underlying memory models (especially in Windows, but for *nix also) and other system calls. I definitely understand their API and how to interact with them, but clearly to combat malware understanding "what's under the hood" would be crucial to defending against these types of attacks. I believe Windows Internals is a topic that is upcoming, and I should learn quite a bit from that!

As a last note, even though it sounds cheesy and I swore that I wouldn't think it was cool, when I saw that calculator open I was slightly more excited than other times I've opened a Windows calculator!