---
layout: post
title: Approaching Unmantained Legacy Projects
---
Through my years working in tech, I have encountered legacy projects that have gone unmantained; usually because the system still runs but the original developers are no longer around and there is no one to pick it up. From time to time, these will require some fixes (maybe an unexpected new input) or enhancements (the data layout has expanded and there is now a use case to include it). Sadly, the previous developers left no traces of documentations or meaningful comments, and now it fall on the new developer (me) to figure things out. Surely one can go about reverse engineering the logic of the program; however no amount of digging through the code will tell what was the business context behind certain decisions. At that point, the best approach is to consult the business analysts, project managers, and others more directly exposed to the business as they would have better insight of the possible use cases that have prompted certain design decisions.

Above were very general insights from my experience, and following are some more specific steps I have taken for some projects:
1. Study the production environment. Document all running processes, environment variables, ports, etc. Understand what are the different resources available.
2. Set up a local environment, replicating production as much as possible, with exception of databases and storages.
3. If this is a microservice, make note of the different endpoints, the method of communication between services, ports, protocols, languages, etc.
4. Get production inputs and feed them into the local environment to trace the code path. Enable debugging to step through the code. While doing that, add comments, TODOs, FIXMEs, and keep adding the findings to a README.
5. After gaining some familiarity with the code, it is not unusual to find inefficiencies or parts that are unclear. This is a good time to do some light refactoring: add some unit tests, rename variables to add clarity, rewrite single lines to follow better standards, use IDE guidance, fix any immediate bugs.

If at the beginning the code seem unreadable and incomprehensible, hopefully by following the above steps should have added some light to what the system does, who uses it, how it communicates, what are the expected inputs and outputs, and with a bonus of making the code slightly more polished.