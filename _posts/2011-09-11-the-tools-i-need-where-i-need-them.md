---
title: the tools I need, where I need them
author: jpr
layout: post
permalink: /2011/09/the-tools-i-need-where-i-need-them/
categories:
  - software
tags:
  - architecture
  - best-practices
  - centos
  - cheaha
  - desktop
  - research notebook
  - workbench
---
Yesterday I was digging into the [firefox startup issue][1] in my home dir on Cheaha within my VNC session. I looked at the /var/log/glusterfs/nfs.log file in on nas-02, the only gluster log on nas-01 or nas-02 that had a timestamp close to the time I was testing, and it didn&#8217;t reveal any secrets about locking.

This morning I looked up &#8220;firefox gluster lock&#8221; and saw references to really old firefox versions and realized the Centos5 is still running 3.5.x versions, quickly reminding me of RHEL limited support for a modern end-user desktop. (There&#8217;s a reason why folks prefer FedoraCore, Ubuntu, and openSUSE for desktops. <img src='http://blogs.uabgrid.uab.edu/jpr/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' /> )<!--more-->

This lead to, &#8220;Hey, I&#8217;ll just install the latest firefox6&#8243;.  Took a bit of doing to get the actual tarball URL (thanks firebug), since the downloads are simplified to autodetect platforms from the client and wget doesn&#8217;t send out such headers by default.  After unpacking the tarball, I tried to run firefox and got an error about a missing library, even after updating LD\_LIBRARY\_PATH to include the firefox install location.

<pre>[jpr@cheaha ~]$ LD_LIBRARY_PATH=/home/jpr/opt/firefox/:$LD_LIBRARY_PATH
[jpr@cheaha ~]$ bin/firefox
/home/jpr/opt/firefox/firefox-bin: error while loading shared libraries:
libcairo.so.2: cannot open shared object file: No such file or directory</pre>

This lead to, &#8220;Hey, all I really need is a [light weight browser][2] not firefox&#8221;.  Chrome? Nope &#8212; not readily available as a tarball for CentOS.  (Yes it&#8217;s possible to run my own RPM database, but I wanted a browser not an admin experience.)  Then I saw a note &#8220;Epiphany comes with Gnome&#8221;.  Nope &#8212; not yet installed on Cheaha.  Then I&#8217;m back to scratching my head&#8230;[what are some of those old competitors to firefox focused on simplicity and speed][3]? Seamonkey &#8212; don&#8217;t want all that other stuff like email.  Netsurf sounds good&#8230;eh, only available as source?  Heck if I&#8217;m going to go that route I just want something simple &#8212; I&#8217;ll go with [lynx][4].

<pre>cd
mkdir src dist
cd dist
wget http://lynx.isc.org/lynx2.8.7/lynx2.8.7.tar.gz
cd ../src
tar -xzf ../dist/lynx2.8.7.tar.gz
cd lynx2.8.7
# setup clean build env
bash
PATH=/bin:/usr/bin; unset LD_LIBRARY_PATH
./configure --prefix=$HOME/opt/lynx  # allow uninstall with rm -rf $HOME/opt/lynx
make
make install
cd ~/bin
ln -s ~/opt/lynx/bin/lynx
exit
lynx
# now I'm happy and ready to move on with the original task
# -- looking at my hadoop cluster stats</pre>

I&#8217;m sharing this session thread, not as complaint but as an insight into the problem that confronts us whenever we start working on a new platform and don&#8217;t have the tools we need. When we are on a system without admin privileges or want to keep a clean separation between our (possibly experimental work) and the stable environment that is our platform. This is true on Linux, Mac, or Windows (think cygwin). It is as true for a simple desktop utility as it is for a computational toolkit.

This is the hurdle as we start to build support for interactive use.  A system platform shouldn&#8217;t become a throttle point for progress.  People should be able to add tools they want to their environment. What&#8217;s a workbench worth when you can only use the tools someone else thinks are important?  Yes, we can certainly encourage folks to run their own rich client desktop (and they do) but each entry point into the cluster has value for different use-cases: command-line, X, or VNC.  There are many solutions out there.  [Homebrew][5] on the Mac is one model for lightweight packaging. Regardless of the solution, the point of the research notebook is to allow people to collaborate. In all cases we should be able to share our labor. &#8220;Hey! Here&#8217;s a link to the tool I just added to my workbench, use it or fork it.&#8221;

 [1]: http://trac.uabgrid.uab.edu/atlab/ticket/204
 [2]: http://www.techrepublic.com/blog/10things/10-web-browsers-for-the-linux-operating-system/2120
 [3]: http://www.makeuseof.com/tag/12-worthy-alternative-browsers-for-linux/
 [4]: http://lynx.isc.org/lynx2.8.7/index.html
 [5]: http://mxcl.github.com/homebrew/