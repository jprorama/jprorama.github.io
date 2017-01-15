---
title: update on RPM packaging for OSG
author: jpr
layout: post
permalink: /2011/10/update-on-rpm-packaging-for-osg/
categories:
  - software
  - update
tags:
  - cheaha
  - osg
  - packaging
  - suragrid
---
At [today&#8217;s OSG VO forum][1], OSG&#8217;s software coordinator, [Alain Roy][2], gave an update on the status of the [community packaging initiative for the OSG software stack][3].  This was a follow up to his initial overview in [August][4].  The community packaging initiative is an effort build on the software packages already being maintained by the broader community.  In more familiar terms, this is about using the native system packages on Linux distributions and benefiting from the support and labor that already go into maintaining these packages. The initial target is CentOS 5, popular on clusters, and therefore, the [RPM][5] packaging it uses. A complete set of RPMs are expected for the entire [VDT][6] by December 2011 but several packages have already stabilized.<!--more-->

Since we are just embarking on the VDT install on Cheaha, I asked Alain if we should focus on the pre-release RPMs or stick with the [Pacman][7] packaged VDT until after the RPMs are complete. (Side note to avoid confusion: the Pacman package manager which has beed used by VDT is not the same as the native package manager of ArchLinux, also called [Pacman][8].)

Alain agreed that it was a hard call at this point. For folks new to the OSG tooling and the VDT stack, today the existing production-ready Pacman packaging is still the best option. In six months&#8230;RPM. He simply asked that we remain aware that Pacman *is* being phased out and will only receive critical updates once the RPMs have stabilized. We need to keep this in mind for our system build planing.

Depending on the pace of our progress, we may find that we can contribute to vetting the RPMs as part of the [OSG integration testbed][9] activities &#8212; deep dives like this are a good way of learning internals. Installing the VDT today using Pacman doesn&#8217;t take much time, so we can assess how to move forward after that work completes.

Alain did say that the experience with VDT via Pacman would map one-to-one with the RPM experience. (Note: Pacman does have individual packages for VDT components. It is just not based on RPM.) This should help us plan where different RPMs will be needed on Cheaha in the future.  At a high level, all nodes &#8212; including compute nodes &#8212; will need the worker node (WN) and CA RPM packages. Other service nodes will leverage specific additional packages as needed.

There were initial concerns about the potential for dependency issues now that core components are provided by the underlying operating system. For example, some RPM-based VDT packages will rely on the system version of Tomcat. They haven&#8217;t seen problems with this yet.

The current stable elements for the RPMs include the OSG CA bundle (which is frequently updated by the [OSG GOC][10] to keep CA trusts current) and [VOMS][11], a component that provides VO support. Only one VOMS is needed per VO and SURAgrid&#8217;s VOMS is currently hosted at Texas Tech, so we don&#8217;t need to worry about that piece.

The RPM components with rough edges include the [compute element ][12](CE) that provides the grid job submission interface and the [HDFS package][13] that supports grid file transfers for the Hadoop Distributed File System.

Alain invites anyone to participate in the [testing][14]. The effort is particularly looking for feedback on the packages that have stabilized.

 [1]: https://twiki.grid.iu.edu/bin/view/VirtualOrganizations/VOGroupMeeting20111006
 [2]: http://pages.cs.wisc.edu/~roy/
 [3]: https://twiki.grid.iu.edu/bin/view/SoftwareTeam/CommunityPackagingProposal
 [4]: https://twiki.grid.iu.edu/bin/view/VirtualOrganizations/VOGroupMeeting20110825#VDT_Moving_to_RPMs_Alain_Roy
 [5]: http://en.wikipedia.org/wiki/RPM_Package_Manager
 [6]: https://twiki.grid.iu.edu/bin/view/ReleaseDocumentation/VdtRelease
 [7]: http://atlas.bu.edu/~youssef/pacman/
 [8]: http://www.archlinux.org/pacman/
 [9]: https://twiki.grid.iu.edu/bin/view/Integration/WebHome
 [10]: http://osggoc.blogspot.com/
 [11]: http://www.globus.org/grid_software/security/voms.php
 [12]: https://twiki.grid.iu.edu/bin/view/ReleaseDocumentation/ComputeElementInstall
 [13]: https://twiki.grid.iu.edu/bin/view/Storage/Hadoop
 [14]: http://jira.opensciencegrid.org/browse/SOFTWARE