---
title: ssh jump hosts
author: jpr
layout: post
permalink: /2016/07/ssh-jump-hosts/
categories:
  - docs
  - software
tags:
  - best-practices
  - clouds
  - devops
---
Reading over the [Ansible intro][1], I learned about a very useful SSH configuration for jump hosts. A jump host is about using intermediate hosts to establish an ssh connection from a client to a server that is not directly accessible, e.g. a compute machine behind a head node. This head-node for local systems is a very common pattern in the cloud, where you might have one box with a public IP and a number of internal nodes not directly accessible to the outside world.

The typical solution is to ssh to the head node and then ssh to to the client. Instead of doing this manually, you can have the tunnel automatically created using an ssh proxy command. From the [Gentoo wiki you can simply add this to your ~/.ssh/config][2]:

> <tt>Host *+*</tt>  
> <tt> ProxyCommand ssh $(echo %h | sed<br /> 's/+[^+]*$//;s/\([^+%%]*\)%%\([^+]*\)$/\2 -l \1/;s/:/ -p /')<br /> exec nc $(echo %h | sed 's/^.*+//;/:/!s/$/ %p/;s/:/ /')</tt>

Then you can using ssh host connections like &#8220;ssh user1%host1+host2 -l user2&#8243; to connect to host2 as user2. (If you use the same user names across all the hosts, you can skip adding the user strings.)

(BTW, I removed the -w1 timeout flag from netcat to prevent the connections from being closed right away. I think this came from the [uptstream reference][3] and that author&#8217;s working on the examples. There is one example which doesn&#8217;t have the -w1 time out. The rest have it and appear to be more about walking through various tests.)

This is very convenient for tools like Ansible, which rely on SSH for their control channel, to manage a cloud cluster.  But note, if you need to maintain a long lived collection of ssh shells in your remote cluster (e.g. your developing a complex configuration), you&#8217;ll probably be better served by using the traditional ssh to the head node and start up a screen/tmux session.

 [1]: http://docs.ansible.com/ansible/intro_getting_started.html
 [2]: https://wiki.gentoo.org/wiki/SSH_jump_host
 [3]: https://glandium.org/blog/?p=303