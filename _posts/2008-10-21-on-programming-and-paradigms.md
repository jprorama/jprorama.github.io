---
title: On Programming and Paradigms
author: jpr
layout: post
permalink: /2008/10/on-programming-and-paradigms/
categories:
  - software
tags:
  - agile development
  - clouds
  - development
  - exterme programming
  - infrastructure
  - it
  - methodologies
  - wiki
  - xp
---
One of the challenges faced in automating infrastructure services is programming at the boundaries between systems. The connections between systems fall outside the realm of typical language libraries. Their complexity and packaging as stand-alone services also helps to hide their interfaces behind the system administrators tasked to keep them running. 

The difficulty of programming at this scale, however, is not so much a failure of programming languages, though scripting languages with relaxed typing are generally better tools, but a failure of our own ability to perceive this as a development activity. Automating infrastructure, the idea that gives rise to cloud computing, is all about building a simplified platform over many components that speeds provisioning and construction of services, both for ourselves and others.

In any development activity, following an appropriate paradigm helps identify construction targets and provides measures for progress. The realm of inter-system automation is inherently dynamic due to the nature of independently developed components. There is a need to continuously adapt to the changes between components. Change is the nature of the business. To force a static development paradigm on this environment, one that insists on knowing all requirements at the start of the game, is almost guaranteed to end in failure and will certainly be a miserable experience along the way.

Anyone building service platforms powered by the tools and development communities distributed across the Internet has developed a healthy respect for and intuition about the nature of this dynamic process. Leveraging this dynamic environment successfully requires agility. It&#8217;s hard to learn this without diving into the process. 

I&#8217;ve heard about [Agile Software Development][1] and [Extreme Programming][2] for some time but haven&#8217;t effectively connected these ideals with this environment until recently. These methodologies seek to encode the intuition of dynamic processes. Applying them to infrastructure development teams promises an effective method for sharing intuition and succeeding in the face of change. 

The Web and Wikipedia are a decent start to understanding these concepts. Extreme Programming (XP) has it&#8217;s own [website][3] and a [wiki][4]. (It&#8217;s worth noting that the first &#8220;wiki&#8221; was established to promote the values of XP.) Google, our ever present teacher, contributes with [&#8220;extreme programming&#8221;][5] and [&#8220;agile development&#8221;][6], but YouTube is also a great source for &#8220;live&#8221; instruction on [XP][7] and [agile development][8].

 [1]: http://en.wikipedia.org/wiki/Agile_programming
 [2]: http://en.wikipedia.org/wiki/Extreme_programming
 [3]: http://www.extremeprogramming.org/
 [4]: http://c2.com/cgi/wiki?ExtremeProgramming
 [5]: http://www.google.com/search?q=extreme+programming
 [6]: http://www.google.com/search?q=agile+development
 [7]: http://www.youtube.com/results?search_query=extreme+programing
 [8]: http://www.youtube.com/results?search_query=agile+development