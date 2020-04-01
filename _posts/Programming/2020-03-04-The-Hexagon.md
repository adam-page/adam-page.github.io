---
layout: default
title:  "The Hexagon"
date:   2020-03-04
category: [Programming]

---

# {{page.title}}

## The Project

Domain Driven Design (DDD) is an often heard word in any modern programming shop. It makes sense-if we encapsulate the things the PAs (Product Analysts) deem important to the business in one centralized location, we can alter it and capture it and the rest of the concerns are with the technologies to interact with those business rules. That interaction involves essentially the rest of the technology stack from UI/UX all the way down to data storage. It also, with aggregates, does a nice job of ensuring that certain transactional boundaries stay intact, ensuring that data is never corrupted, mismatched, or otherwise in an invalid state due to multi-user technologies.

I'm currently working on an information system for use with myself and perhaps my friends as we play DnD which uses this as the core design pattern for the business logic, with Commands and Events as the means to "talk" to the domain. It seems like a good pattern to learn whether you think its a good one or not (as I mentioned, it can be found somewhere in almost every modern software shop), and while where I work is no different I would like to get a more intimate and perhaps more idyllic example in a personal project.



## A Hexagon?

The idea with this analogy for the pattern (really it could probably be any shape) is that you have the core business rules, and everything else interacts with the system through a well-organized API that knows nothing of the outside world. I'm choosing events and commands with a sense of versioning for my domains as it seems like a clean way to deal with updates from multiple sources, and it also seems like an easy boundary by which the external world can act on the domain. Whether I implement quick and dirty reads as some patterns do remains to be seen as its largely a performance concern, but the versioning system gives interactions a nice way to try to do something and receive a response either that an event was emitted and the expected change was made, or an exception gets returned as what the caller thinks about that entity is no longer true.

This kind of event-driven system also solves many of the difficulties of DDD that are hard to overcome-namely that things like repository storage or UI interaction cause the domain to have to know something about the software systems that implement it. I plan to make the domain have no knowledge of anything but itself, and every ancillary technology will have all of its dependencies constructed in such a way that if something in the system needs to change then it can. We often believe that systems won't need to change, but this almost always is proven false by anything from changing business rules to changing technologies and deployment strategies.



## Concerns

My biggest concern is the UI layer. I've chosen Python as I write very little of it at work and I find it a pleasing language to write in a personal project, but its UI frameworks that are multi-platform don't seem well developed or mature. At best they seem tentatively on the way out the door, or they're tying to really firmly get in the door. Additionally I don't have a good sense of scope so I think some of the storage means could need to rapidly change. Luckily if these pieces are composed within the system and interact through a certain preset boundary, they can be swapped out relatively easily.

Another concern is that while at the start creating an event-driven system sounds wonderful, building a system that can rebuild itself by replaying every event (or by replaying every event from a checkpoint) is a non-trivial matter both from concern as well as consistency through update processes and expansion of entities. I think my strategy now is to just ensure that the domain written and the events are fairly robust and inclusive and more long-term there are answers for many of these problems in ways that, while they require a bit of work, do solve the problem without hindering the benefits this kind of system can bring.

Nicely enough I can just choose to not use the system or store the data until I'm really ready to. Additionally the particular entities at play in the system can be rebuilt fairly easily and dropped in as a snapshot or simply reloaded in. There is a world however where once the kind of note and history system I would like to build is implemented, this becomes a less viable solution to the problem, and so I  have no doubts that before I am through I will have to employ some of the methods I mentioned at the end of the last paragraph.



## Going Forward

Right now I'm still just writing the initial domain and trying to ensure that I have solid unit test coverage (establishing a strong test pyramid is another plan I have for this system), but I think after that I'll deal with the event system. It really is the layer that sits right outside the domain itself, and without the messaging bus the rest of the system can't interact with the domain, which is where the interesting stuff lives. Next some basic utilities like logging, dependency resolution, and other niceties that allow a system to scale well. After that persistence will become a quick detour as I plan to do mostly on-disk storage for now rather than tackle some centralized server, and then I will spend a good deal of time after that on the initial UI.

Once all that is in place I would like to expand the domain and the functionality of the system, and once the initial domains and UI is in place there is probably an argument to be made to start creating some kind of service that can deal with storage, multi-user interaction, etc. This will also allow for furthering the domain into other problems in the space and using the current solution to interact with those, but before I can dream about that I have plenty of code to write. I have enjoyed the work so far though and I do see a lot of promise and use cases I can solve for myself and maybe some friends once I approach a usable solution.

Up next on this portion of my blog will likely be some initial notes about the testing pyramid, which I do plan to write an initial blurb about much like this post, as well as update on as the project goes along. The basic idea with the test pyramid is that you want the bulk of the logic in the system tested with smaller, less dependent, and easier to run tests. Unit, Integration, and System levels is one way to look at it, and other definitions include Service or UI tests as a portion of this as well. I personally will probably stick with Unit, Integration, and System as it seems reasonably general and doesn't tie itself to UI or services exclusively.