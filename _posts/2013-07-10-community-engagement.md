---
title: community engagement
author: jpr
layout: post
permalink: /2013/07/community-engagement/
categories:
  - around the net
  - notes
  - software
tags:
  - chef
  - crowbar
  - dell
  - development
  - devops
  - open source
  - openstack
---
Just finished attending my first [Crowbar design meeting][1].  I listened in during the call and then introduced myself and [our deploy at UAB][2] at the end of the call.  I also expressed our interest in the BIOS/RAID changes for full disk use.

The short discussion clarified a few points.  Most significantly, the focus of the Crowbar 1.x is bare metal provisioning.  It is only meant to get the fabric set up.  Any post provisioning management needs to leverage the [Chef backend][3]. The [Crowbar 2.x dev work][4] is adding management features at the crowbar layer.

This means we can pretty much focus our efforts on Chef with respect to modifying our existing config.  Also, [Grizzly will be supported in Crowbar 1.6][5] but given the 1.x focus, it likely means we are looking at a bare-metal reinstall to get Grizzly (not unexpected but much clearer).

I raised our interest in the BIOS/RAID improvements in the context of the forthcoming [open-sourcing of Dell&#8217;s barclamps for BIOS/RAID as listed on their Trello board][6].  [Rob][7] was glad to have this issue raised and felt the timing was very good since the oss release should be complete within two weeks.  He&#8217;ll put the BIOS/RAID barclamp on the agenda for the next design call in two weeks.

All in all, a fruitful community engagement.

 [1]: https://github.com/crowbar/crowbar/wiki/Meetings
 [2]: http://dev.uabgrid.uab.edu/wiki/OpenStackPlusCeph
 [3]: https://github.com/crowbar/crowbar/wiki
 [4]: https://github.com/crowbar/crowbar/wiki/Crowbar-2.0
 [5]: https://github.com/crowbar/crowbar/wiki/Roadmap
 [6]: https://trello.com/c/JOiulBsN
 [7]: http://robhirschfeld.com/