---
title: Database-managed Grid-enabled analysis of neuroimaging data
author: jpr
layout: post
permalink: /2011/11/database-managed-grid-enabled-analysis-of-neuroimaging-data/
categories:
  - paper
  - software
tags:
  - cnari
  - community research networks
  - grid
  - neuroimaging
  - osg
  - papers
---
[Database-managed Grid-enabled analysis of neuroimaging][1] ([Small, 2009][2]) describes the [Computational Neuroscience Applications Research Infrastructure, CNARI,][3] from the [Human Neuroscience Laboratory][4] at The Universty of Chicago.  The paper describes the CNARI infrastructure, shares some examples of its use, compares CNARI to serveral other project and speculates on opportunities.<!--more-->

I discovered the paper during a search for neuroimaging technology frameworks, specifically looking to see if there are any nanoHUB  instances, or rather [HUBzero][5] instances.  I actually found the paper in a related search on &#8220;[neuroimaging and osg][6]&#8220;.  The paper is well structured, letting me focus on the parts that are interesting and allowing a quick read of the material to keep the content organized mentally.

Given my approach from an infrastructures for neuroscience perspective, I focused on the CNARI description to fill in a picture of what other sites are doing to support neuroimaging with advanced technologies.  CNARI uses RDMS storage for data associated with fMRI studies to allow data sets to be explored from many angles and avoid the fractured storage models, hence fractured metadata, typical of neuroimaging analysis workflows (as documented in the paper). CNARI also uses the [Swift][7] programing language to allow for easy distribution of common neuroimaging analysis steps across a large fabric of grid computing resources (OSG and TeraGrid).

Several points stand out:

*   The introduction and overview of the infrastructure does a nice job of highlighting several common data management and analysis practices that I&#8217;ve been introduced to through casual conversations with neuroscientists in the field.
*   It is enlightening to see the distribution of RDBMS queries across a large (and distributed) compute infrastructure as part of the CNARI data segmentation and distribution mechanism.  The relational queries, performed via standard Python DBI API calls at the compute nodes, allow the data to be split up easily and have only the small subset of data returned by the query transferred to the compute node that issued the query.  This implies that the RDBMS interface is also accessible across the Internet.
*   Also enlightening is the reliance on the [grid security infrastructure (GSI, aka. certs)][8] to ensure transport privacy and authn/z.  This is a nice example of GSI meeting the needs for HIPAA, so it can be done if folks really want to enable this kind of science.

I&#8217;ve been curious  about Swift since the [Swift tutorial][9] [I attended][10] at [MardiGras &#8217;08][11].  Seeing it used for neuroimaging workflows is a good reminder of its flexibility and yet another example of the need for process orchestration in many science domains.

While there might be some debate on the use of RDBMS queries from the compute clients, vs say today&#8217;s more popular techniques like [RDF stores][12], there&#8217;s no debate that being able to ask questions across a dataset based on the relationships expressed within the data is transformative.  This use in CNARI is a good indicator that concepts like relational data stores are still on the adoption curve in many branches of science.  It&#8217;s a reminder that just because something is old hat in the CS world, doesn&#8217;t mean it has been universally adopted.

Finally, the paper compares CNARI  to the [Extensible Neuroimaging Archive Toolkit (XNAT)][13] which I recall from discussions at a technical issues meeting.  Something to look at in more detail in the future.

 [1]: www.ci.uchicago.edu/~uhasson/small09.cnarirev.pdf
 [2]: http://scholar.google.com/scholar?hl=en&q="database-managed+grid-enabled+analysis+of+neuroimaging+data"
 [3]: http://www.google.com/search?q=cnari+neuroimaging
 [4]: http://www.ci.uchicago.edu/research/project_detail.php?id=95
 [5]: http://hubzero.org/
 [6]: http://www.google.com/search?q=nueroimaging+osg
 [7]: http://www.ci.uchicago.edu/swift/main/
 [8]: http://www.globus.org/security/overview.html
 [9]: http://www.mardigrasconference.org//conf_2008/tutorials.php#swift
 [10]: http://www.mardigrasconference.org//conf_2008/program.php
 [11]: http://www.mardigrasconference.org/conf_2008/
 [12]: http://en.wikipedia.org/wiki/Resource_Description_Framework
 [13]: http://xnat.org/