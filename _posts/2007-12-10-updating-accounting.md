---
title: updating accounting
author: jpr
layout: post
permalink: /2007/12/updating-accounting/
categories:
  - around the net
tags:
  - development
  - gpir
  - sg-accounting
  - sgas
  - suragrid
  - uabgrid
---
After a spurt of activity getting [GPIR support for SGE][1] and further [exploring the GPIR provider framework for possible use in the SURAgrid Accounting Working Group][2], I&#8217;ve hit a lull awaiting the resolution of a central question: what&#8217;s the most appropriate accounting tool to build upon?

Coincidentally, the [OGF December 2007 Newsletter included a review of some interoperability demo&#8217;s they hosted as part of SC07][3]. The summary references an [interoperability demo][4] of the [DGAS][5] and [SGAS][6] grid accounting systems using the URF. The demo does a nice job of describing the components that are used to complement local data from the scheduler with grid-specific data, upload, store, and retreive URF records. It&#8217;s significant because the URF is the OGF&#8217;s accounting record format we have been developing against in [SG-Accounting][7]. It&#8217;s good to see exploration of this format. Also, SGAS is the SweGrid Accounting Service that is now a tech preview in Globus. The general interest in the intersection URF with these tools, may also be a good synergy for our efforts to build URF formatters for the popular schedulers.

Poking around Google led me to an [accounting systems review by JISC (UK) from July 2007 (pdf)][8]. This looks like an excellent report to help answer some of the lingering questions about the accounting tools because it includes a comparison of several of the major players. 

Notably absent is any mention of GPIR. To be fair, this is not really an accounting system, it&#8217;s an information repository. Given this, it&#8217;s probably a good indication to focus on accounting for accounting rather than trying to build accounting into non-accounting systems. I&#8217;m guessing we could still use some of the client-side GPIR provider tools, since they look like a good way to manage the updating of information via SOAP. It might be useful to have a consistent client side configuration that simply extends an already deployed client-side tool. An new question: how does SGAS (or other tool) support uploading data from the client side?

 [1]: http://projects.uabgrid.uab.edu/gpir-sge
 [2]: http://projects.uabgrid.uab.edu/gpir-sge/wiki/SuragridAccounting
 [3]: http://www.ogf.org/News/newscal_enews.php?dec07
 [4]: http://www.omii-europe.org/wiki/Wiki.jsp?page=DGASSGASInteropDemo
 [5]: http://www.to.infn.it/grid/accounting/main.html
 [6]: http://www.sgas.se/
 [7]: http://projects.uabgrid.uab.edu/sg-accounting/wiki/SURAgridAccounting
 [8]: http://www.jisc.ac.uk/media/documents/programmes/einfrastructure/jisc_aum_final_report_wth.pdf