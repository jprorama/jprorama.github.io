---
title: 'submodules and git: reading materials'
author: jpr
layout: post
permalink: /2011/05/submodules-and-git-reading-materials/
categories:
  - docs
tags:
  - app store
  - git
  - git submodules
  - gitolite
  - kde
  - workflows
---
Continuing on the app store thread from this morning&#8217;s ops-eng meeting, I&#8217;m working to understand how git can help us manage the code ingestion, build and deploy processes for our platform(s).

There&#8217;s a [FAQ-like entry about git and submodules][1] over at the endpoint site. I was hoping for more in the way of a workflow recipe, like the abc&#8217;s of a real submodule example. The linked discussion on [Spree and submodules][2] didn&#8217;t live up to it. (But [Spree][3] seems cool.)

The [ProGit manual has a much better chapter on submodules][4] than the Git User Manual. There&#8217;s enough meat there to take the approach seriously. Interestingly, submodules exist on branches in the super repo, so if there isn&#8217;t consistency across those branches then manual moving of submodule directories might be necessary, ie. switching branches doesn&#8217;t take care of the work and may lead to confusing conflict messages.

This all sparked a search on git use in large projects and lead to an [old LWN article][5] that right away reminded me of KDE&#8217;s plans to go git. catching up on that progress is enlightning, especially in learning that [they are not going with gitorious][6] but instead building their own with gitolite + Redmine + Reviewboard. (Redmine is the new Trac):

> It <a title="http://lists.kde.org/?l=kde-scm-interest&m=127612957219466&w=2" rel="nofollow" href="http://lists.kde.org/?l=kde-scm-interest&m=127612957219466&w=2">has been decided</a> to use gitolite + Redmine + reviewboard on our own servers rather than gitorious.org. Sysadmin team is preparing git.kde.org for this.

The linked [announcement about the decision][7] ([report][8]) also offers a solid reminder of the value of an open process: people can understand your process, learn from your experience, and build trust in your solution going forward.

 [1]: http://blog.endpoint.com/2010/04/git-submodule-workflow.html "FAQ-like entry about git and submodules"
 [2]: http://blog.endpoint.com/2010/03/spree-software-development.html "Spree and submodules"
 [3]: http://spreecommerce.com/
 [4]: http://progit.org/book/ch6-6.html
 [5]: http://lwn.net/Articles/246313/
 [6]: http://techbase.kde.org/Projects/MovetoGit#Setup_git.kde.org
 [7]: http://lists.kde.org/?l=kde-scm-interest&m=127612957219466&w=2
 [8]: http://lists.kde.org/?l=kde-scm-interest&m=127612957219466&q=p3