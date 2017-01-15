---
title: "we're going with openstack"
author: jpr
layout: post
permalink: /2013/03/were-going-with-openstack/
categories:
  - requirements
  - software
  - update
tags:
  - architecture
  - ceph
  - clouds
  - design
  - openstack
  - rcs
---
(and so is [PayPal][1])

At the beginning of March we began an [OpenStack][2] and [Ceph][3] deployment with [Dell][4] and [Inktank][5] to build out our research cloud on the storage dense compute servers we acquired last fall.  This exciting project brings our cloud explorations to fruition on a solid implementation and support fabric.  The nature of this collaboration will allow us to continually shape our platform and build on the open development model we have [always championed][6].

[Infrastructure is our product][7].  It is everyone&#8217;s product. We customize our tools to build an environment that supports our service to others.  The power to control our infrastructure is the significance of cloud computing.  We are turning to OpenStack to continue the implementation of our [Research Computing System][8] so that we can turn control over to you.

We are building an operating system.  An [operating system][9], or better, a &#8220;system of operations&#8221; is a disciplined, intentional, organization of resources with interfaces to harness their function so you can create environments that solve your most vexing problems. We are building an operating system for you to control the technology that supports your research.<!--more-->

OpenStack and Ceph will form the heart of our newest generation of compute and storage hardware.  We are using features like [VLAN networking mode][10] to build hundreds of virtual playgrounds where you can explore ideas and build the solutions that you need.

Follow along with our work deploying [OpenStack and Ceph][11] and feel free to  share your ideas or jump in to lend a hand whenever you can. We&#8217;re open.

 [1]: http://www.forbes.com/sites/reuvencohen/2013/03/26/paypal-to-drop-vmware-from-80000-servers-and-replace-it-with-openstack/
 [2]: http://www.openstack.org/
 [3]: http://ceph.com/
 [4]: http://www.dell.com/Learn/us/en/19/dell-cloud-computing
 [5]: http://www.inktank.com/dell/
 [6]: https://dev.uabgrid.uab.edu/
 [7]: http://blogs.vmware.com/console/author/bbalkansky
 [8]: https://docs.uabgrid.uab.edu/
 [9]: http://www.ibm.com/developerworks/linux/library/l-linux-kernel/
 [10]: http://docs.openstack.org/trunk/openstack-compute/admin/content/configuring-vlan-networking.html
 [11]: https://dev.uabgrid.uab.edu/wiki/OpenStackPlusCeph