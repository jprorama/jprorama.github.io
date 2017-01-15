---
title: 'migrating project resources: status and notes'
author: jpr
layout: post
permalink: /2010/06/migrating-project-resources-status-and-notes/
categories:
  - software
tags:
  - build process
  - controltier
  - git
  - production
  - rnet
  - trac
  - xcat
---
The current status of the projects migration, as I understand it:

*   we&#8217;re agreed on Debian5 as the base for trac. This comes back to the version of Python needed for trac-git plugin. On centos5, trac works with python but the python version for trac-git is up to snuff. 
*   We&#8217;re still working with trac .11.x. We are using trac from the source, which is good since we&#8217;re going to want to start pushing some of the features more that will necessitate tracking the upstream a little more closely and maintaining a local branch, e.g. tighter integration with group member definitions and permissions. (Trac itself will become one of the project instances we&#8217;ll manage on this platform). 
*   The migration of our trac instance from fusion to esxi isn&#8217;t reliable so we&#8217;re rebuilding on esxi. There is a debian5 box up on esxi and we&#8217;ll move forward with building that out to become &#8220;trac.&#8221; In the mean time we&#8217;ll keep serving our new projects on the current trac running within fusion. 

## Background and Context

A suggested convention, let&#8217;s call our hosts name.u, so we don&#8217;t have to fully qualify them or type uabgrid. Our intention is for these names to float rather easily anyway, so the above hosts would be projects.u, trac.u, git.u, and svn.u. We can drop the .u if our context ishostnames and just use names like projects, trac, git, and svn.

During this rebuild, I&#8217;d like to follow the convention from projects a bit more closely, and keep up the separation between the underlying system and the project data, i.e. put stuff under /srv/trac and such rather than /var/www/trac. The main reason for this is to make rebuilding the host easier. If the os (system) and apps and data are each in separately managed locations we can more easily create a runnable environment by pairing up components. This is good practice and an example can be found on the ROCKS compute nodes. ROCKS can rebuild a compute node with ease. It keeps the system in a partition on the local drive and gets the rest of the context by network mounted files. More generically, the good practice we want to follow is to support creating process environments (trees) by grafting branches (system, ui, data).

Continuing on the thread of back filling context, we should keep in mind that we aren&#8217;t abandoning projects.u in favor of trac.u. Projects will just become more of a composed node that aggregates content from a number of resources: trac, git or svn, blogs, mediawiki, mail lists, etc. This was the original goal for projects and using trac as the sole resource was an easy way of accomplishing that goal. Projects is likely to leverage some content aggregation core, e.g. drupal or joomla. It will also be the place you&#8217;d expect it to be, a node where you can find projects. Going to projects.u without any further qualification should engage the user in an opportunity to search and browse for content&#8230;not confront them with a blank page or error message. (This is a dig at myself, the blank page was an easy way to delay implementing a listing/unlisting and search feature, every project is unlisted.)

## Iterations

Getting back to the trac instance, the original [notes for building projects][1] are just loose notes. They are pretty far from the cut-n-paste ease of some of the other node build instructions.

## Iteration 1

I&#8217;d like us to start viewing the build of the &#8220;projects&#8221; tool suite as a dynamic process; a process we will iterate through many times. We should be able to spin up a feature with relative ease (either from a ground up rebuild or by pushing out an update). Regardless of how the deploy goes, a developer will need to pretty easily build up a working environment as well, so our docs need to consider this role as well. Iteration 1 will be semi-manual out of necessity so we can refine the instructions and identify the updates on debian5 and trac11x. This instance willk eep most elements on the core trac node, e.g. keep git on the same box/vm until the nas nodes are up.

Once the build step of iteration 1 is complete we can move the temp-hosted projects (biobank and cagrid) on the fusion instance of trac onto the esxi instance. We need to complete iteration 1 in short order because the fusion instance is just a stop gap solution.

## Iteration 2

Iteration 2 will include improving the build process and moving the trac instance to the hardware in rust. Pushing this to iteration 2 will provide us some lead time to get some of the dependencies out of the way (nas) and let the planning for rnet (research network) get down the road a little further. 

I&#8217;d see this process with trac as method to define a cleaner build-deploy process outline than we&#8217;ve had for biobank. (No criticism intended. Biobank was intended to be, and has very much been, a lead probe to identify issues.) 

As part of this cleaner process, iteration 2 should also start leveraging our management framework (xcat/controltier/puppet). That is, we need to start identifying where these tools come into the picture and mapping out how we will leverage their strengths.

## Going Forward

These notes should give us a better sense of direction for the next few weeks of work on the projects suite. Moving our project resources out of pilot provides good context for our production migration more generally and focuses the effort on tangible elements that also happen to be comprehensive; our project resources happen to include mail lists and the membership management tools (groups and permissions), ie. the functions piggy-backed on sympa in our pilot environment, along with other tools like blogs and mediawiki instances.

 [1]: http://dev.uabgrid.uab.edu/wiki/UABgridProjects