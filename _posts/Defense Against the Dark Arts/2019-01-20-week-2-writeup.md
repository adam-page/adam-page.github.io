---
layout: default
title:  "Week 2 Writeup"
date:   2019-01-20
category: [Defense Against the Dark Arts]

---

# {{page.title}}

#### [{{page.category}}](/blog/#{{page.category[0] | downcase | url_escape | strip | replace: ' ', '-' }})&mdash;{{ page.date | date: "%B %-d, %Y" }} 

----

This week's content for Defense Against the Dark Arts seemed to have two big ideas linked by one overarching theme: volatility. First off the open source software Volatility is a useful snapshot tool that can be used to grab snapshots of memory; useful for the cyber analyst that may not want to stay on site where malware is found. Beyond that the hierarchy of volatility is an important metric for anyone looking to recover sensitive and potentially harmful files as it allows a pragmatic approach to saving live data that will not survive a power restart. The other big picture item this week was the USB stick that contained some of the malware used in the Sony breach; this was a look at how this volatility can be important, as well as how hard drive file recovery tools allow the investigator to recover things an attacker may have wanted disposed of.

It should be fairly evident to anyone with basic knowledge about computers and malware that the volatility of data storage devices do matter, and for a malware investigator understanding exactly how this memory works and in what ways it is volatile is of the utmost importance. Enter the Order of Volatility. According to my notes it goes something like (high priority to low): system memory, temporary file systems, process table/network connections, network routing info/ARP cache, forensics acquisition of disks, remote logging/monitoring, physical configuration/network topology, and finally backups. While much of this is pretty obvious, its important to remember this heirarchy when analyzing any malware attack; either as an incident responder or as a forensics investigator. It seems likely that the investigator will deal with it more often through the lens of knowing the gaps/lack of information. If system memory and hard drive(s) of a system are snapshotted, then it is likely things in the upper part of the order will be retained and thus can be analyzed. In the case of what is to come (the Sony case), one would think things lower down on the scale, such as remote logging/monitoring would have caught this malware, but as it turns out this was not immediately recognized through these files, and perhaps a shift in policy was made after the attack. Either way the information here was already somewhat evident to me, but keeping it mind always when analyzing and when thinking about how to recover information is important.

The next big picture item this week was the Sony malware, and while I'm not going to do a full analysis/writeup on it I think the six questions posed as the challenge offer a unique perspective on this piece of malware and what it aimed to do.

### 1. What is/are the target(s) found on the USB-stick?

It seems as though my initial analysis was wrong, however it later seems as though the targets were a number of South Korean oil companies, such as S-oil and Gscaltex.

### 2. Investigate possible malware and describe the working.

This malware seemed to be mostly concerned with propagation among the system (I even found a server executable which seemed to serve up the files of the malware, potentially to other systems in the Sony network) and with ip/username/password retrieval. In short this was an intellectual property attack and this piece of malware is what allowed the attacker to get that property. In ReadPSW.cpp we can see that the malware was written in VC++ 6.0 and although the comments aren't readable to me, the code seems to make system environment calls, password access calls, and then stores this data. I think at a high level that pretty much covers it, and its pretty apparent that once an attacker had TCP access with usernames and passwords, they could easily get many of Sony's most sensitive secrets.

### 3. Display the list of usernames/passwords.

I don't think this post is the right medium to do this, but I will note a few things about these files: 1. There were a ton of IP addresses among the deleted files, and many of them included subnet masks, indicating that this malware was within an isolated network. 2. There weren't many unique passwords (the largest file was 11kb) and considering they were stored in multiple places in different chunks of what seemed like a master list it seems the malware was especially concerned with exiting the network with as much data as could be collected, for it to be consolidated later. Passwords like "123456" and "qwerty" were among the most lazy, but even the admins were lazy with passwords like "admin", "admin111", and "admin123456" indicating that even those in network administrator roles weren't doing a great job of security! Nonetheless the whole file was fairly small, and a brute force attack likely wouldn't take long with only 11kb of passwords to search.

As far as the passwords specifically relating to the targets currently on the USB I am still searching...we'll see if anything comes of that...

### 4. What offset value did you find them?

f0391000 was where the first list was found, but I also found another record in the DUBrute folder, which contained much of the data about the malware itself. Personally I'd name this malware DUBrute. Again as to the passwords for the current attack, it is to me unknown at this time.

### 5. What files were deleted and can you replicate them?

Most of the files I've talked about above were deleted, and the photorec software did an excellent job of recovering it. In fact I just recovered the whole disk without reference to a specific partition and I got all of the files and folders I found if I grabbed a certain partition of the disk. I also mounted it as a removable media and was sure not to format the disk as Windows wanted me to...

### 6. What strategy would you advise the targets?

I would shut off the company's internal network from any outside access, and scrub for all iterations of this bug (I found quite a few on the usb disks, all with different names but with the same apparent purpose). After the malware has been removed I would run some operations like normal and use something like FakeNet (but for the routers linking to the external web) to ensure that nothing was trying to send out more data. After this I'd block the ports which were used (I found at least one, although I can't remember it off the top of my head) and finally I would conduct a mandatory password change, dual authentication for all logins, and training on choosing effective passwords! While this breach wasn't necessarily caused by a weak password, after looking over the list I wouldn't be surprised if it was.

In closing I think this piece of malware is particularly enlightening because of how simple and distributed it is. It doesn't aim to completely remote control a computer, nor does it try to dump all of the hardware contents in one shot. Rather it seems most concerned with proliferation and account compromise, leaving the attackers to then choose which information to steal. The hackers obviously thought the USB drive was wiped, but obviously only the handles were removed and they failed to overwrite the underlying data, leaving it ready for recovery. Both the malware and how it was found prove that simple, innocuous things (like account compromising or a lack of understanding as to how to completely wipe a hard drive) can often be the things that in the computerized dark arts can make the biggest difference.