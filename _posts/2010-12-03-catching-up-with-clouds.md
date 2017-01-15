---
title: catching up with clouds
author: jpr
layout: post
permalink: /2010/12/catching-up-with-clouds/
categories:
  - around the net
  - notes
  - software
tags:
  - art
  - clouds
  - development
  - globus
  - infrastructure
  - it
  - open source
  - production
  - systems
  - uabgrid
  - xcat
---
Making sense of clouds is tricky business. Shape-shifting is in their very nature, often morphing right in front of your eyes. Understanding clouds becomes a lot easier when you let the fog clear a bit and realize they are just hiding the details of our long term migration to distributed systems.

Dr. Bangalore recently shared a [nice little video (sorry for the advert)][1] that paints a pretty picture of clouds and highlights their already familiar shapes. It makes a great starting point for any discussion and reminds us why we like clouds: when it comes to doing ***my*** work, I&#8217;d really rather not know how ***they*** work.

Clouds are the latest effort to encapsulate what it means to work with the distributed systems that have been evolving for decades. Instead of trying to excite folks by talking about [the tools we&#8217;re using to do amazing things][2], watching their eyes glaze over, and trying [win them back with analogies][3], we&#8217;ve opted to simply say, &#8220;It&#8217;s a cloud, make it look however you want.&#8221;<!--more-->

This is great when your looking at clouds, but someone still needs to make the magic happen and turn those visions into reality. This post is about creating clouds, so let&#8217;s blow away some of the nebulous shapes and take a closer look at the elements that form a cloud.

What is a cloud&#8230;*really*

A recent paper in the IEEE Journal *Internet Computing* [&#8220;Virtual Infrastructure Management in Private and Hybrid Clouds&#8221;][4] ([PDF Draft][5]) summarizes the requirements for building your own cloud:

> To provide the same features found in commercial clouds, private/hybrid cloud software must meet a variety of requirements: provide a uniform and homogeneous view of virtualized resources, regardless of the underlying virtualization platform (e.g., [Xen][6], [KVM][7], [VMWare][8], etc.); manage the full lifecycle of a virtual machine, including setting up networks dynamically for groups of VMs and managing the storage requirements of VMs, such as deployment of VM disk images or on-the-ﬂy creation of software environments; support for conﬁgurable resource allocation policies to meet the speciﬁc goals of the organization (e.g., high availability, server consolidation to minimize power usage, etc.); and adaptability to an organization’s changing resource needs, including peaks where local resources are insufﬁcient, and changing resources, including addition or failure of physical resources.

Significant investments in software automation are central to any cloud construction in order to accomplish this level of customized provisioning. We are approaching this effort from solid foundations in HPC, grid, and collaborative computing. [ROCKS][9], the management fabric that has run our HPC clusters for years, exposes a cohesive set of services common to any automation fabric. We are selectively teasing apart those services and augmenting them with the features from other automation fabrics. We&#8217;ve internally discussed the merits of [xCAT][10] and the [Virtual Computing Lab (VCL)][11] ([VCL@NCSU][12]) as guideposts for our destination. With the physical resource layout stabilized, we can delve into the cloud-focused resource managers among them:

*   [OpenNebula][13] &#8211; this virtual infrastructure manager, described in the IEEE paper, is part of the [RESERVOIR][14]([YouTube][15]) project and is an extensible virtual infrastructure management fabric that can be used to manage and provision resource across a number of internal and external back-end providers, including Amazon&#8217;s EC2. It shares a history with the development team behind the GridWay resource scheduler, given [our experience with GridWay][16], I trust that team to develop well-architected software.
*   [Eucalyptus][17] &#8211; is another cloud management fabric. It too can provision locally owned resources and augment the supply with EC2 offerings. The model for the internal arrangement of resources seems to be slightly different from OpenNebula, but it appears to be equally capable.
*   [Nimbus][18] &#8211; this is the 3rd of the open source cloud platforms featured here and builds on existing cluster deployments and augments them with the ability to provision virtual machines. This project is emerged from the Globus project.
*   [Nimbula][19] &#8211; is an exclusively commercial cloud platform offering from the original developers of Amazon&#8217;s EC2 cloud. It&#8217;s listed here for completeness. Amazon EC2 is the de facto standard for infrastructure as a service cloud offerings. In fact, this and all the tools above support the Amazon EC2 web services API for controlling cloud resources from a the customer side. This is direct access to resources is a key appeal of cloud computing. The [Nimbula data sheet][20] is also well worth reading as it provides a very good high level overview of the components of a cloud infrastructure. It is a good companion to the quote above.

An important complement to these tools is the environment used to develop and maintain these components, I&#8217;ll have more to say about that in a future post, suffice it to say that our work will continue to build upon the [open infrastructure model][21] we have promoted throughout our [resource development efforts][2].

The authors of the paper conclude their description of the advanced reservation extension they built for OpenNebula by addressing a question that is often raised at the confluence of research and production:

> &#8230; our [goal] is to produce production-quality releases that meet the needs of other communities. In fact, we feel strongly about using a development model that, ﬁrst and foremost, produces stable software, suitable for production environments, which we can also use for our own research, incorporating the results of our research into the next stable version. This allows us to support the requirements of virtual infrastructure users, while incorporating novel techniques and solutions into our releases.

I couldn&#8217;t agree more.

 [1]: http://us.cnn.com/video/?/video/tech/2009/11/03/cloud.computing.test.cnn
 [2]: http://dev.uabgrid.uab.edu
 [3]: http://blogs.uabgrid.uab.edu/jpr/?p=23
 [4]: http://dx.doi.org/10.1109/MIC.2009.119
 [5]: http://www.mcs.anl.gov/uploads/cels/papers/P1649.pdf
 [6]: http://www.xen.org/
 [7]: http://www.linux-kvm.org/page/Main_Page
 [8]: http://www.vmware.com/
 [9]: http://www.rocksclusters.org/wordpress/
 [10]: http://xcat.sourceforge.net/
 [11]: https://cwiki.apache.org/VCL/
 [12]: http://vcl.ncsu.edu/
 [13]: http://opennebula.org/
 [14]: http://www.reservoir-fp7.eu/
 [15]: http://www.youtube.com/watch?v=l40Iny4xwuo
 [16]: http://dev.uabgrid.uab.edu/uabgrid-stage
 [17]: http://open.eucalyptus.com
 [18]: http://www.nimbusproject.org/
 [19]: http://nimbula.com
 [20]: http://nimbula.com/products/datasheet
 [21]: http://docs.uabgrid.uab.edu/wiki/Welcome