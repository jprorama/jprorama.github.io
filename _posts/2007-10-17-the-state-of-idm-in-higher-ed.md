---
title: The state of IdM in higher-ed
author: jpr
layout: post
permalink: /2007/10/the-state-of-idm-in-higher-ed/
categories:
  - around the net
tags:
  - best-practices
  - IdM
  - ldap
  - open source
  - shibboleth
  - vendor solutions
---
Last week at the Fall Internet2 Member Meeting I attended a [session covering the trend toward incorporation of commercial identity management solutions into higher education identity management processes][1]. The presentations covered ongoing efforts at University of Wisconsin-Madison, University of Alaska, and Indian University.

**Highlights**

The overall conclusions were that a hybrid approach incorporating local development, open source, and commercial products is the most successful. IdM in higher-ed is a very custom space which closely reflects the requirements and goals of a university. Commercial solutions can help but they are not turn-key. Important criteria are customization and support for existing open solutions (LDAP, WebSSO, and Shibboleth).

This space is undergoing a transformation similar to the migration from highly customized and locally developed student and HR systems to commercial based solutions. While the commercial solutions offer much needed out-of-the-box convenience, site specific business processes still need to be implemented locally. And, since these efforts take time and criteria can shift rapidly in the Internet era, it&#8217;s critical that business agility is not impacted. The commercial solutions should be thought of as identity management toolkits to support the construction of identity management solutions.

<!--more-->

**Details**

Keith Hazelton from UW-Madison gave an overview of their investigation into using PeopleSoft&#8217;s IdM product. Steve Devoti, their lead architect on this project, has worked to develop what looks to be a well thought out set of evaluation criteria to help take religious arguments out of the process and move them into an empirical model. He has written an RFP but it won&#8217;t be [public][2] until mid-Nov. [Keith&#8217;s slides from the presentation (pdf)][3] include some highlights of their evaluation criteria and the evaluation matrix used. Slides 3, 4, 12 and 13 highlight some of their evaluation approach. The UW-Madison effort is being [recorded on-line at their wiki][4].

Keith mentioned that a critical service for UW-Madison is Shibboleth, and so any vendor solution they choose will need to support it&#8217;s integration (LDAP interface). The summary from this effort so far is that it looks like a mix of local code, open source code, and commercial products is likely for the foreseeable future.

David Bantz from the University of Alaska gave an overview of the UA IdM problem space and current solution set. The UA schools are highly distributed and had many local solutions in place. They have gone with a combined solution of Oracle&#8217;s Person Registry Database, Sun&#8217;s LDAP Directory, JES Identity Manager and Password Sync, Luminis Portal, and MIT Kerberos. An interesting requirement they had was for a multi-master password store for Kerberos. Due to the distributed campuses, they couldn&#8217;t afford to have lost connectivity interrupt authentication at different campuses. None of the vendors offered this feature so they too went with a hybrid system. 

Finally, Alan Walsh of Indian University gave a rather lengthy presentation on the effort they have been pursuing for a number of years. This presentation was interesting because their solution has focused on the Microsoft Identity Lifecycle Manager product. He spoke highly of the product and noted that one area that was favorable for this product was the cost: it was licensed on a per-server instead of per-user count bases, making it more affordable. He also noted that their final solution includes a mix of local, open source, and vendor solutions. One issue he drew attention to was the self-service password reset feature which doesn&#8217;t yet exist in this product. IU wrote their own. 

**Additional References**

I requested information on where folks were talking about their approaches in greater detail and the recommendations were for the [Educause Identity Management Discussion Group][5], which is also hosting a special session at next weeks Educase meeting in Seattle. [Specifying and Choosing IdM Systems][6] is a full-day seminar on Tuesday. It is free but requires explicit registration. Steve Devoti of UW-Madison and Alan Walsh of IU will both be presenting at this meeting. There is also an [IdM Working Group][7] in Educause that is probably a good resource for on-going involvement in the evolution of these systems.

 [1]: http://events.internet2.edu/2007/fall-mm/sessionDetails.cfm?session=3419&#038;event=273
 [2]: https://wiki.doit.wisc.edu/confluence/display/AUTHNZ/UW-Madison's+Identity+and+Access+Management+RFP+Process
 [3]: http://www.internet2.edu/presentations/fall07/20071011-uwExp-hazelton.pdf
 [4]: https://wiki.doit.wisc.edu/confluence/display/AUTHNZ/Home
 [5]: http://www.educause.edu/IdentityManagementDiscussionGroup/9363
 [6]: http://www.educause.edu/E07/Program/11073?PRODUCT_CODE=E07/SEM05F
 [7]: http://www.educause.edu/idm/