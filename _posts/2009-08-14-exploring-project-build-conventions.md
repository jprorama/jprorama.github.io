---
title: exploring project build conventions
author: jpr
layout: post
permalink: /2009/08/exploring-project-build-conventions/
categories:
  - notes
tags:
  - architecture
  - build process
  - documentation
  - linux
  - org
  - systems
  - uabgrid
---
Spent the afternoon looking into build management systems for Linux to get a sense for how the projects manage this process. Started looking at project management tools first but this lead more toward the ms-project end of the world (useful but not what i wanted). BTW, see [openworkbench ][1]as a potential desktop tool and [project open][2] for a possible larger scale tool to track across multiple projects &#8212; they also have a [vm image][3] for easy eval.

Getting back to the investigation of build process management, 

A nice [highlevel over view of best practices][4]. As always, part of the challenge of finding the material you need from a new research area is to find the right questions to ask [question1 (project managment source code best practices)][5], [question2 (how to build build a linux distribution)][6], [question3 (debian build system)][7].

Each question has partial answers that help dissolve the fog. Little snippets in the result lead you along and shed new light on familiar fixtures.

> [Maven][8] aims to gather current principles for best practices development, &#8230; Keeping your test source code in a separate, but parallel source tree &#8230; Maven also aims to assist in project workflow such as release management and issue &#8230;

It&#8217;s good to know what&#8217;s there when your landscape is Java world. It&#8217;s also good to follow leads and then circle back to earlier results. That&#8217;s how I found the [quick summary of project best practices][4], which does a nice job of contextualizing all the reading materials gathered here.

Sometimes even [http://www.ibm.com/developerworks/linux/library/os-lfs/ poorly writen articles] help you along the way. DeveloperWorks is a good site if not always perfect, but even a hazy 30k ft view is better than no view at all. 

I&#8217;ve long considered the linux distribution model as an ideal example for what it means to build a &#8220;system&#8221;. The [Linux From Scratch (LFS)][9] project provides a book to help you through the process. It&#8217;s more of a learning exercise and doesn&#8217;t delve into examples of best practices but does show [what&#8217;s at the heart of the whole process][10]: 

> Download or otherwise obtain the following packages:

It&#8217;s the &#8220;&#8230;or otherwise obtain&#8230;&#8221; comment that provides the most guidance. Much of what we are facing in the uabgrid platform build process touches on multiple stages and best practices. Some of our source is a pure and from the originating project. In those cases we can mostly just pull the code directly from the project and use whatever packaging system might already be in place: RPM+yum+kickstart for CentOS, Pacman for VDT, GPT for Globus. It&#8217;s a bit of a pain to know all these systems. Certainly more of a pain to have to pick and choose. But experience and time helps build some intuition on what&#8217;s needed where. 

Other parts of our source are custom forks of projects. The forks need their own revision tracking. It&#8217;s still not clear if we should have one big happy repo or a bunch of individual projects. More time and experience will reveal this, I&#8217;m sure.In the meantime, the [LFS book on building a system][11] is a good example of what our own build documentation should cover.

Seeing other&#8217;s processes helps build experience and reveals the edges of the pathway: the dividing lines between stages and responsibilities. [ROCK Linux][12] is about helping you build a distribution. Browsing their source tree quickly reveals [the important files][13]: it&#8217;s not the source package but your local diff and build process for it. 

**A build process from upstream sources will have a basic structure**:

*   the upstream source
*   a collection of patches
*   a build options file
*   the commands to execute the build
*   some structured info about the process (like dependencies)
*   a description of how your project categorizes this tool

***All these files need to be tracked in our build environment***. The upstream source may not need to be, unless we can&#8217;t trust the persistance of the upstream supplier or are wanting to ensure the perpetual availability of a specific version. All-in-all it looks like [ROCK Linux will be a really good model of how to proceed][14].

Smaller systems like ROCK Linux are sometimes disparaged as being immature by their more mature cousins, ie. compare what RedHat must do to manage their distro. (They aren&#8217;t very open about it, so it&#8217;s hard to learn from them.) Smaller systems are easier to understand, however, and reveal their processes more quickly. They can more easily lend you a hand because they aren&#8217;t too far ahead of you.

Mature processes are helpful measures, too, provide hints about what you might not be considering. Thankfully, Debian has a large scale and mature build process that can help us avoid stumbling on know obsticles. The [Common Debian Build System (CDBS)][15] is a solid beacon that can l help shed light on the more complex scenarios faced by mature systems. Maturity sometimes means the documentation can lead you into the weeds (see also [Debian package mgmt][16]). [Wikipedia provides a nice highlevel view of CDBS][17] that also servs shores up some of the abstractions.

 [1]: http://www.openworkbench.org/
 [2]: http://www.project-open.org/
 [3]: http://www.project-open.org/documentation/install_vm
 [4]: http://www.codeproject.com/KB/architecture/Coding_Best_Practices.aspx
 [5]: http://www.google.com/search?q=project%20management%20source%20code%20best%20practices&#038;ie=UTF-8&#038;oe=UTF-8
 [6]: http://www.google.com/search?q=how%20to%20build%20a%20linux%20distribution&#038;ie=UTF-8&#038;oe=UTF-8
 [7]: http://www.google.com/search?q=debian%20build%20system&#038;ie=UTF-8&#038;oe=UTF-8
 [8]: http://maven.apache.org/what-is-maven.html
 [9]: http://www.linuxfromscratch.org
 [10]: http://www.linuxfromscratch.org/lfs/view/stable/chapter03/packages.html
 [11]: http://www.linuxfromscratch.org/lfs/view/stable/
 [12]: http://rocklinux.net/
 [13]: http://www.rocklinux.net/svn/rock-linux/trunk/package/public/jasper/
 [14]: https://www.rocklinux.net/wiki/Main_Page
 [15]: http://build-common.alioth.debian.org/cdbs-doc.html
 [16]: http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html
 [17]: http://en.wikipedia.org/wiki/Debian_build_toolchain