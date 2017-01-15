---
title: a benefit of an open infrastructure
author: jpr
layout: post
permalink: /2016/01/a-benefit-of-an-open-infrastructure/
categories:
  - requirements
  - software
tags:
  - best-practices
  - devops
  - hpc
  - infrastructure
  - rcs
---
It supports reviewing processes that lead to change in a project.

The [puppet-openstackci][1] project is working to create a build hook for third party contributors to OpenStack. It&#8217;s also an entry point into building your own [CI/CD devops system][2].

Here&#8217;s a recent contribution to the project documentation. It added Sphynx formatted documentation to make it part of the published OpenStack docs.

You can [review the contribution][3] to improve Sphynx documentation in Gerrit, the OpenStack code review tool. It was contributed on Dec 17 2015 and  accepted with a +2 by the code review on Jan 5 2016.  This merged the change into the official repo and became part of site.  Now you can [read it online][4].

Because the repos also are published to GitHub for convenience, you can also see the accepted diff in the [puppet-openstackci git repo][5].

 [1]: https://github.com/openstack-infra/puppet-openstackci
 [2]: http://devops.com/2015/03/03/i-want-to-do-continuous-deployment
 [3]: https://review.openstack.org/#/c/259245/
 [4]: http://docs.openstack.org/infra/openstackci/third_party_ci.html
 [5]: https://github.com/openstack-infra/puppet-openstackci/commit/6f0d8c2e643e419c4cabdd27162cce764fcda6d6