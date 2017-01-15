---
title: Finally installing xcode 4
author: jpr
layout: post
permalink: /2012/05/finally-installing-xcode-4/
categories:
  - notes
  - software
tags:
  - app store
  - dev
  - mac
  - xcode
---
I&#8217;ve been avoiding the upgrade of Xcode 3 on my Mac to Xcode 4 for Lion mainly because of the whole &#8220;use the App Store&#8221; requirement.  I&#8217;ve also grown to dislike Mac&#8217;s concept of software &#8220;management&#8221;.  How can a concept of Linux software repositories and disciplined platform state-management get so perverted by Apple and Microsoft (and Android). <!--more-->

The Xcode selection hasn&#8217;t been that hard.  Googled &#8220;xcode mac&#8221; and got a page with a link that opens the app store.  That part is easy.  Keeping track of the progress of the install is much harder after the initial pretty app install overlay disappears.  Only way I found to do it it was search for xcode in the appstore and see that the drop-down has &#8220;Installing&#8221; as the current state.

Before installing I wanted to make sure to remove Xcode 3.  The aforementioned displeasure with software management concepts lead me to[ a nice post][1] that has one simple sudo command to remove the old version:

> sudo /Developer/Library/uninstall-devtools &#8211;mode=all

That&#8217;s much more like it.  I actually does what it says.  I gotta say, for a platform that likes buttons and eye candy as much as OSX, it&#8217;s hard to understand why there can&#8217;t be a simple button to invoke such a command.

 [1]: http://idoitonamac.blogspot.com/2011/03/how-to-remove-xcode-from-your-mac.html