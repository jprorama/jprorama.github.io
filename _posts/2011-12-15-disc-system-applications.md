---
title: DISC system applications
author: jpr
layout: post
permalink: /2011/12/disc-system-applications/
categories:
  - paper
tags:
  - cheaha
  - commodity hardware
  - condor
  - disc
  - mapreduce
  - storage
---
The DISC systems argued for by Bryant in [Data Intensive Scalable Computing][1] (DISC) and referenced by Szalay in [Extreme Data-Intensive Scientific Computing][2] are growing in popularity in many circles.  DISC systems recognize the inherent compute capability of data storage nodes and use this configuration to push computations as close to the data as possible: onto the CPU of the data storage node.  This approach uses the fast local host networks connecting CPU to memory and disk to maximize data processing.  In this environment, the external network (GigE) takes on the role of a control channel and data staging; scheduling and storage software transparently maximize the locality of computations and data; and ever more commodity systems can be added to produce a very large scale computational platform.<!--more-->

[MapReduce][3] is one application model that can use DISC systems. It shows a lot of promise for helping users restructure analysis algorithms into parallel map and reduce steps.  MapReduce is hot and is generating a lot of interest.  You may recall, we had a short session on using [Hadoop][4], an open source MapReduce implementation, on [Cheaha][5] at our [boot camp in September][6].

There are no general-purpose solutions, however, for automatically converting procedures into a parallel equivalent.  Just like with MPI (what the articles refer to as &#8220;traditional HPC&#8221;), GPU computing or any technologies that support simultaneous activity on individual tasks, someone must decompose the problem space to identify the parallel components that can leverage these technologies.  Doing so takes skill and disciplined effort.

Over the course of time, more and more programs will be developed that are capable of using these models, and these programs will be available to researchers here at UAB and other campuses. We are at the early stages of broad interest in DISC-like systems, so it&#8217;s a good time for us to adopt and prepare.  
<span id="prior-art"><br /> </span>

### Prior Art

The DISC model is not new, however.  [Data decomposition][7] is a well understood model for achieving parallelism.  What is new, is the broad market appeal of these solutions. This is happening because many of the problems confronted today are data parallel: an identical action over many independent pieces of data.

Earlier examples of DISC-like systems are already familiar.  It could be argued that [Beowulf computers][8], the de facto commodity cluster model in use today, is an early example of a DISC system.  The original Beowulf systems were just commodity computers, each with their own local RAM and disk storage, interconnected by commodity networking.  This is the same fabric we have on Cheaha. There are 136 computers with local disks and RAM interconnected by a 1 gigabit Ethernet network.

The high-speed Infiniband networks and central shared storage on Cheaha are really just tweaks to the traditional, DISC-like Beowulf cluster. These tweaks are designed to support special applications (e.g. simulations that demand low-latency, inter-process communication) and to simplify programming by providing a global data namespace via a common shared file system.  These tweaks, refined over a decade-and-a-half of adoption, are what have made clusters using commodity hardware the preferred replacement for the custom hardware supercomputers of the late 20th century.

Looking at Cheaha stripped bare of the special purpose Infiniband networking and storage hardware, leaves us with a fabric that is readily used for the class of problems popular with DISC systems, e.g. MapReduce.  In this context, Cheaha&#8217;s architecture mirrors the warehouse-scale computer illustrated in Figure 1 of [Bryant[1]][1].

Cheaha can, in fact, be used for solving DISC-oriented problems today.  The role of Cheaha&#8217;s resource reservation service, [SGE][9], is to allow applications to reserve a set of computers.  What an application does with those computers depends on the nature of the application and the hardware available on the reserved computers.

The simulation-class applications typically use MPI to leverage the high-speed Infiniband network to coordinate the action of tightly coupled computations. It is this simulation-class of applications that has occupied much of the attention of and funding for scientific computing over the past decade, viz. [TeraGrid][10].

### Flexible Layers

Data intensive applications, however, could just as easily use SGE on Cheaha to instantiate an Hadoop environment with [HDFS][11], a distributed file system composed of the disks local to the reserved compute nodes.  The data set would be staged into HDFS and Hadoop would then use the MapReduce model to affect the desired analysis, assigning computations to nodes selected by their proximity to the data being analyzed. That is, computations would be assigned to the compute nodes that have had the relevant data staged on their local disk drives.

This layering of SGE with Hadoop or MPI may appear complex at first, but it is the standard model for isolating responsibilities in complex environments. It also allows a common set of hardware to serve the needs of many different types of scientific computing.

This layering also lets us swap out components to enhance or grow our compute fabric.  For example, we could use [Condor][12] as a scheduler instead of SGE.  On dedicated hardware, Condor can support the same range of applications that SGE does, but it shines above others in harnessing dynamic pools of compute resources, e.g. idle cycles on desktops and workstations.  Taking a close look at the hardware architecture of these systems, reveals that they too match the criteria for DISC systems. They are CPU-RAM-Disk tuples that can compute very efficiently over data that is either local to the system or close by, for example on other systems that share the same network switch.

With Condor&#8217;s ability to enlist non-dedicated resources into large compute pools, we could even view the campus network as the communication fabric of a very large DISC system with thousands of nodes, especially when the campus network fabric has been architected to complement computational frameworks, like Hadoop+HDFS, which are designed to leverage such platforms. (It&#8217;s worth noting that, Condor is not limited to harnessing resources local to a campus, as it&#8217;s success in OSG adequately demonstrates.)  Using Condor to reserve resource pools for MapReduce computations is [outlined in the original paper on MapReduce][13] and again highlights the importance of the complementary services in layered fabrics.

In the campus network example, a network fabric would complement the DISC model by recognizing that most inter-system communication for such computations can be isolated to the computers that share the same network switch, and therefore, the trunk lines between switches are needed primarily for less frequent data movement operations between layers, e.g. data staging and result gathering. This means that the capacity of a 1GigE trunk line between switches is unlikely to be exceeded due to over subscription of the compute nodes on an individual network switch, where each compute node connected to the switch also has a 1GigE network connection. Network switches have ample internal switching capacity to facilitate communication between nodes on the same switch and that is where computations are concentrated. The distributed file system fabrics used by compute frameworks like MapReduce are capable of maximizing compute-data locality by using network topology information to keep computations near the data staged on the compute node itself or on nodes that share the same switch.  
<span id="cost-shift-to-software"><br /> </span>

### Cost Shift to Software

By leveraging software to hide the details of managing resource reservation and data-computation distribution, we can further benefit from the aggressive price points of commodity hardware by not having to overbuild individual components of the system.  We simply put relatively cheap commodity components to work for us and recycle them when they no longer offer sufficient utility.  This philosophy promoted by the DISC systems is the exact same philosophy that drove the original construction and adoption of Beowulf clusters.

The more features demanded in hardware, the higher it&#8217;s price and the less flexible the resulting components.  Aggressive use of commodity hardware is one way to push cost down significantly.

Linking commodity hardware with software designed to hide the underlying complexity not only hides the complexity of the distributed environment but introduces significant costs savings from hardware acquisition economies of scale.  The same hardware can drive many different types applications.

For example, we can use the same commodity components to build the core platform for simulation fabrics (reserving special-purpose hardware like Infiniband or GPUs for applications that benefit from it), to build a DISC computing environment, to build virtual machine fabrics, or to build large scale storage systems. The systems are differentiated by the application software that defines the services they provide.

DISC systems can also be used to construct large, traditional file systems.  Software like Gluster and Luster can tie many storage systems together to aggregate their capacity.  Even traditional solutions like NFS can harness many independent storage nodes of a DISC system, if we accept a greater expense of re-balancing file system trees and distributing loads.

On the cost advantage of generic of commodity hardware components, Szalay[2] references [Backblaze&#8217;s price point for 1Petabyte of storage][14]. They claim a hardware and operation cost of [$100K/PetaByte/3years][15]. This is a good example of how DISC systems can provide significant storage resources.  While such systems do require on-site hardware construction, these skills are common in desktop support groups. Driving down the cost for raw hardware is well worth consideration, given the component flexibility.

The Backblaze example does highlight, however, that costs shift to software development and maintenance.  Integrating the hardware becomes a software development activity. It is the software that distinguishes the services of the hardware, whether the system exposes a file store, a MapReduce platform, a resource reservation system, or some other abstraction that facilitate recombination by users of the platform into novel solutions that address research needs.

DISC is benefiting from the abundance of commodity hardware already present in our environment.  By tuning existing network and system configurations and continuing to push the adoption of low-cost commodity hardware, we can build a very flexible storage and computing fabric that can address the needs of many of today&#8217;s applications and support the develop of transformative science in the future.

* * *

Updated: 2012-01-13 &#8211; Add many hyperlinks to expand on the links to the papers. Clarified wording in final paragraph before &#8220;Prior Art&#8221; section.

Updated: 2011-12-22 &#8211; Add sub-section headers for easier navigation and reference.

 [1]: http://dx.doi.org/10.1109/MCSE.2011.73
 [2]: http://dx.doi.org/10.1109/MCSE.2011.74
 [3]: http://en.wikipedia.org/wiki/MapReduce
 [4]: http://hadoop.apache.org/
 [5]: http://docs.uabgrid.uab.edu/wiki/Cheaha
 [6]: http://docs.uabgrid.uab.edu/wiki/2011_HPC_Boot_Camp
 [7]: http://www.thinkingparallel.com/2007/09/06/how-to-split-a-problem-into-tasks/
 [8]: http://en.wikipedia.org/wiki/Beowulf_cluster
 [9]: http://en.wikipedia.org/wiki/Oracle_Grid_Engine
 [10]: https://www.xsede.org/tg-archives
 [11]: http://hadoop.apache.org/hdfs/
 [12]: http://research.cs.wisc.edu/condor/
 [13]: http://research.google.com/archive/mapreduce.html
 [14]: http://blog.backblaze.com/2009/09/01/petabytes-on-a-budget-how-to-build-cheap-cloud-storage/
 [15]: http://blog.backblaze.com/2011/07/20/petabytes-on-a-budget-v2-0revealing-more-secrets/