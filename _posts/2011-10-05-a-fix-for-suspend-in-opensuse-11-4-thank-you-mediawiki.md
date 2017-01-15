---
title: a fix for suspend in opensuse 11.4. thank you MediaWiki
author: jpr
layout: post
permalink: /2011/10/a-fix-for-suspend-in-opensuse-11-4-thank-you-mediawiki/
categories:
  - docs
tags:
  - laptop
  - mobile computing
  - opensuse
  - research notebook
  - virtualbox
  - wiki
---
I&#8217;ve always been a fan of SUSE and have run [openSUSE][1] on my Dell D420 laptop for many years. After installing 11.4 in June and adopting whole disk encryption, however, the suspend feature mysteriously stopped working. Adding / and swap partitions to the encryption regimen has been disappointing. Application start times are noticeably slower, and without the ability to suspend, the slow reboot cycle seriously impacts the viability of mobile computing.

Assuming suspend had gotten messed up with the encrypted swap and wanting to recover app load performance, I prepared to revert to /home-only encryption. Storage space constraints make any process harder than it needs to be. Why does it have to be so challenging to stash a 50GB disk image somewhere while I&#8217;m working on a fix? Why does the solution always boil down to &#8220;pick your least favorite data and delete it?&#8221; 50G isn&#8217;t really that much.<!--more-->

In order to avoid that pain, I started looking for reported problems with disk encryption and suspend. There were early signs of problems, but all recent docs pointed to &#8220;it should just work&#8221;. Great, now my problem was unique and I&#8217;d have to solve it on my own.

OpenSUSE has good [on-line documentation][2]. The suspend feature is well documented, but I was only reading about the [suspend-to-disk option][3] at first because that&#8217;s what [Google said][4]. I missed seeing what turned out to be the key ingredient. On the suspend-to-ram page were listed several known issues, the critical one being [loaded VirtualBox drivers will cause the computer to freeze while suspending][5]. The fix was easy: turn off vbox before suspend and turn it back on after. It was easy to apply, a simple stop/start script in the suspend controller command tree, and easy to adjust to detect my local start script because the suspend process documentation was solid.

The openSUSE documentation framework is [powered by the MediaWiki engine][6] and highlights the value of an open knowledge base, freely editable by anyone who logs in. I know who to thank and credit for returning me to the world of viable mobile computing. The workaround was [documented on August 14 by user Cyberorg][7] from the [opensuse-education project][8]. Thanks Cyberorg. Also, because the site can be edited by anyone who logs in, I can add the virtualbox note to the suspend-to-disk page so the next searcher will have an easier time of finding the fix.

This is called scratching your own itch and demonstrates why open information that can be easily indexed by public search engines will win out in end &#8212; there is no such thing as &#8220;only locally relevant&#8221; information. When you share knowledge everyone benefits.

 [1]: http://www.opensuse.org/en/
 [2]: http://en.opensuse.org/Main_Page
 [3]: http://en.opensuse.org/SDB:Suspend_to_disk
 [4]: http://www.google.com/search?q=opensuse+suspend+to+encrypted+disk
 [5]: http://en.opensuse.org/SDB:Suspend_to_RAM#Problem_due_to_VirtualBox_drivers
 [6]: http://en.opensuse.org/Special:Version
 [7]: http://en.opensuse.org/index.php?title=SDB%3ASuspend_to_RAM&action=historysubmit&diff=42215&oldid=37155
 [8]: http://www.opensuse-education.org/