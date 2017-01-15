---
title: Going production
author: jpr
layout: post
permalink: /2007/09/going-production/
categories:
  - thinking out loud
tags:
  - development
  - globus
  - methodologies
  - open source
  - production
  - shibboleth
---
Going production means many things and the formality depends on context. Regardless of how formal, a critical measure of production work is the ability to repeat a process predictably.

The best way to get to reach production in the software world is to not just do it once. Do it many times. Do the work over and over and over and over and over. This is the quickest way to find the quirks and stress points.

If you run a service, don&#8217;t just expect to run a single instance of it. You should be running at least two instances, and even better three or more. This is a core motivation for the open source development model. Remove the penalties for producing software by allowing unfettered reproduction.

Running Shib? Run at least a couple of IdPs and many SPs. Register your services over and over. Keep creating metadata. Running web-applications? Don&#8217;t be satisfied when you have your first one running. Keep adding apps, until the app adding process becomes second nature. By the time your done, you&#8217;ll know what needs automating. Same goes with Globus. These services are complex little beasties. Their complexity is stripped away with familiarity, leaving just *little* beasties behind.

Don&#8217;t be afraid of having the system fall apart a few times. Falling apart is *good*. It let&#8217;s you know where the parts didn&#8217;t fit and the nails didn&#8217;t hold.

It&#8217;s critical to use the system to get your own work done. If you can&#8217;t use it for your own work, then neither can anyone else. If you&#8217;re building a system and not using it yourself &#8220;because your not the intended user&#8221;, then you shouldn&#8217;t be the one building the system.

Keep shaking up the system. When the dust clears and you see your system standing solid, that&#8217;s when you are ready for &#8220;production&#8221;. 

Rinse. Repeat.