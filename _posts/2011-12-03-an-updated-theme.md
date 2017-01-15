---
title: an updated theme
author: jpr
layout: post
permalink: /2011/12/an-updated-theme/
categories:
  - software
  - update
tags:
  - joomla
  - mediawiki
  - skins
  - theming
  - uabgrid-theme
  - uabtheme
---
I&#8217;d like to share an update on the theming work I&#8217;m doing. I&#8217;ve been following the layout of the pages at <http://www.uab.edu/brand>. I&#8217;ve finished the first draft pass at laying out docs using the UAB theme.  
[<img class="alignright size-full wp-image-154" title="Screen shot 2011-12-02 at 6.42.16 PM" src="http://blogs.uabgrid.uab.edu/jpr/files/2011/12/Screen-shot-2011-12-02-at-6.42.16-PM1.png" alt="" width="400" height="410" />][1]

<!--more-->The work is on my mac in git under ~jpr/Applications/mampstack-1.2-4/apps/mediawiki/htdocs.  Most of the work is on the uabvector-page-layout-edit branch.  The current draft is the HEAD of that branch.

The logo and graphics work is under ~jpr/projects/uabgrid-theme .  There&#8217;s only like two files in that dir.  One is the draft work on the logo/icons.  From this file I select elements and do an export to png to create specific icons.   I haven&#8217;t gotten far enough along to break the content up across files.

The other file is a rough draft of the UAB page structure. It&#8217;s a false color layout of the different page elements that cover the core structure elements of that theme.   It needs some cleaning up.

I tried several approaches to adapt the UAB Joomla theme to MediaWiki.  The first was just mapping css tag, seeing what was what and how to move stuff around.  Playing with the template in php, however, turned out to be the easiest in the end.

In order to avoid working out all the technical layout modifications, altering the css to redo the layout, I ended up moving the page construction order around so that it fit better with the existing uab css rules.  This made it fairly easy to get the parts in the right place and then override only the few MediaWiki style rules or properties that interfere.

There&#8217;s still plenty of work to do on this.  Still need to work on the font styling.  The footer needs layout modifications, my banner (the docs logo) and powered-by icon need work.  Where the tabs should go needs to be figured out.  What ribbon menus need to exist?  How should the leftpanel be structured?

And, ultimately, could we do the layout changes more in css, so at least the output order of the page content wouldn&#8217;t need to change so much?   The current solution, moves the actual page content after a lot of irrelevant page structure elements.  That&#8217;s not so good for search engine ranking and the utility of the data to others.  The meat of the content should come first.  It&#8217;s likely not hard to reorder the layout, but it suggests some heavy forking of the uab stylesheet.

In the near term it&#8217;s going to be easier to suffer a little page structuring messing about than it is to debug stylesheets.  It will be easier to start a theme from the ground up and keep it clean, but that&#8217;s going to require a little more learning on my end.  The current approach should help teach me.

Let me know what you think and have a nice weekend.

 [1]: http://blogs.uabgrid.uab.edu/jpr/?attachment_id=154