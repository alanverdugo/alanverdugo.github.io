---
id: 2348
title: An introduction to Docker containers
date: 2018-10-11T18:37:25-05:00
author: Alan Verdugo
layout: post
guid: http://www.kippel.net/blog/?p=2348
permalink: /?p=2348
responsive_meta_box_designation:
  - ""
responsive_meta_box_facebook:
  - ""
responsive_meta_box_twitter:
  - ""
responsive_meta_box_googleplus:
  - ""
responsive_meta_box_text_linkedin:
  - ""
categories:
  - Uncategorized
---
IT architects have always been striving to create infrastructure that is easier to manage. This is has resulted also in infrastructure that is cheaper and much more configurable. The &#8220;infrastructure as code&#8221; goal was much more than a buzzword, it was something that the IT world desperately needed, even if we didn&#8217;t realize it back then.

The idea behind containers is not new, for example, technologies like LXC precede Docker by five years. Virtualization is much older than that but the goal has always been the same: to isolate processes, dependencies and configurations in order create environments for applications.

What I like about containers is precisely what you are talking about: If I want to test an application in some version of some flavor of Linux, I can just &#8220;pull&#8221; that image from the Docker hub, run my code on it and see how it works. The same if I just want to test some need technology. Before containers, I would have to 1) provision a server or Install a VM 2) Configure that OS 3) Download and/or update libraries, packages, etc 3) Configure the application 4) Deploy my code 5) Hire a sysadmin or install security patches on my own&#8230;. and so on. Docker allows us to get to the interesting parts much faster (and cheaper) and the best thing is that we can modify, document, share and compare these containers as if they were pieces of code. And as you know, I am a big fan of open source and keeping things organized.

images are supposed to be downloaded, inspected, improved and shared again. This is the reason why Docker popularity exploded

It is the way out of the dependency hell

by leveraging other image layers in the dockerfile, optimizations can be made in the build process. For example, an two different Python applications would share a common Python layer, and the diferences would be only the source code for each application. This is the reason why images can have a small size compared to virtual machines. Docker is smart enough to use cache of the layers that has already built