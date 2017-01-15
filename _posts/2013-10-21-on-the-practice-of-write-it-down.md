---
title: on the practice of write-it-down
author: jpr
layout: post
permalink: /2013/10/on-the-practice-of-write-it-down/
categories:
  - docs
  - notes
  - requirements
  - software
  - thinking out loud
tags:
  - best-practices
  - documentation
  - revision control
  - source code
  - wiki
  - writing
---
On the topic of IT practices, one that I hold dear is write-it-down.  There are two sides to write-it-down: feed forward and feed back.

<div class="moz-text-html" lang="x-western">
  <p>
    <strong><!--more-->Feed forward writes into the future.</strong>
  </p>
  
  <p>
    You write down the steps that solve a problem so that they can be carried out again.  This is the mechanism inherent to software development.   We codify processes so that they can be repeated again and again.
  </p>
  
  <p>
    In IT, we are experts at documenting process.  We code.  We should follow a model that celebrates coding. We should visualize documentation as an exercise in writing software. Coding is not optional.  It is what we do.
  </p>
  
  <p>
    This approach lets us bring our best practices from the world of software development to bear on the problem we are trying to solve:  maintain a definitive repository for the execution of IT processes.
  </p>
  
  <p>
    Software development practices like revision control, step-wise refinement, and refactoring are crucial to evolving the steps we have discovered into instructions a computer can carry out automatically.
  </p>
  
  <p>
    Practically,  a simple directive like write-it-down carried out by many individuals can lead to multiple copies of the same process documented for each individual case that demands it.  A FAQ, maintained in a wiki, can easily become long and unwieldy, overrun with similar entries that record specific steps followed under similar circumstances. In the heat of satisfying a request, it will often feel much easier to write-it-down-again than to look-it-up-and-revise.  Regardless, write-it-down-again is always a better decision than do-it-and-forget-it.
  </p>
  
  <p>
    Documenting a process, however, is only the first step.   As with any code base, patterns emerge over time.   It is  the responsibility of mature software practitioners to review recorded steps and identify common patterns that vary only in their parameters.
  </p>
  
  <p>
    We call this refactoring our code base. Refactoring is an exercise in identifying a definitive sequence of steps and removing repeated implementations.   Duplicated steps result in errors. It is too easy for one copy of a duplicated procedure to miss a critical update, leading to failure instead of success.
  </p>
  
  <p>
    It is our responsibility to curate and improve our repository of IT processes.
  </p>
  
  <p>
    <strong>Feed back exposes detail.</strong>
  </p>
  
  <p>
    Effective communication networks have a feed back mechanism. Feedback regulates the flow of information.  Flow control ensures the network doesn&#8217;t become flooded by upstream demand. Writing down a process feeds information back upstream and helps expose the impact of demand.
  </p>
  
  <p>
    Letting us know the impact of our requests allows us to react to capacity limitations in the network.   If we know that a network is overloaded, we can back off on our flow of requests. Some requests are critical, but understanding how requests are implemented gives us the option to increase network capacity by carrying out some of the functions ourselves.
  </p>
  
  <p>
    Let&#8217;s consider an example.   Let&#8217;s assume we have a new database application that we want to run.  We request our DBA network to set it up.    All applications need a machine to run on, so the DBA network, in turn, requests the Server network for a machine.  If the Server network is overloaded, the DBA network must wait and then monitor the Server network to recognize when it&#8217;s request is complete.
  </p>
  
  <p>
    In the mean time,  the DBA network blocks and makes us wait on our request for a new database application.  In other words, two groups are busy waiting on the same request. Additionally, each new database app request sent to the DBA network will suffer from the overloaded Server network.  Eventually, the DBA network itself will become overloaded simply from monitoring pending requests to the Server network.
  </p>
  
  <p>
    If, however, the steps to run a new database application are fed back to us, we can help take responsibility for their successful execution. We can recognize that each of our DBA network requests involves a request to the Server network.  We can then avoid generating backlogs in the DBA network by interfacing with Server network directly.
  </p>
  
  <p>
    We change our process, so that future requests to the DBA network already include the result from the Server network.  Now the DBA network can carry out our set-it-up request without immediately blocking on a downstream dependency.
  </p>
  
  <p>
    We haven&#8217;t completely solved the problem. There is still an overload condition in the Server network but we are now much more in control of our request. We are aware of the source of delays, and we can more effectively work with the Server network to resolve those delays by responding to the feedback from this network.
  </p>
  
  <p>
    It&#8217;s possible the Server network delay originated simply because insufficient information was available at the DBA network to complete the request.  A direct connection to the Server network, ensures we can satisfy such requirements at a priority that aligns with our operational goals. Furthermore, we have cleared needless tasks from the DBA network that only served to increase unrelated traffic and risk additional overload conditions.
  </p>
  
  <p>
    Write-it-down feeds forward and feeds back to build solutions and identify problems.  It is a simple directive that has far reaching impact.
  </p>
</div>