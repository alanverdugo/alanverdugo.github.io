---
id: 618
title: How to change the resources of cloud servers using Tivoli Service Automation Manager
date: 2014-09-12T11:42:40-05:00
author: Alan Verdugo
layout: post
guid: http://www.kippel.net/blog/?p=618
permalink: /blog/resources-tsam
#permalink: /?p=618
categories:
  - Uncategorized
tags:
  - english
  - how-to
  - IT
  - Technical writing
---
<div class="entryContentContainer blogsWrapText">
  <p dir="ltr">
    In order to modify the resources of a Cloud server, you need to do the following:
  </p>
  
  <p dir="ltr">
    In this example we will add disk space to an AIX cloud server.
  </p>
  
  <p dir="ltr">
    Login into the Tivoli Service Automation Manager.
  </p>
  
  <p dir="ltr">
    Once you are logged in, in &#8220;My projects&#8221;, select &#8220;Manage Servers&#8230;&#8221;<a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/1.png"><img class="aligncenter size-full wp-image-619" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/1.png" alt="1" width="411" height="388" /></a>
  </p>
  
  <p dir="ltr">
    Search for the hostname of the desired server and select it.<a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/2.png"><img class="aligncenter wp-image-620 size-full" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/2.png" alt="2" width="620" height="181" /></a>
  </p>
  
  <p dir="ltr">
    Click on the &#8220;Modify Server Resources&#8221; button.<a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/3.png"><img class="aligncenter wp-image-621 size-full" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/3.png" alt="3" width="624" height="190" /></a>
  </p>
  
  <p dir="ltr">
    Click on the Edit button.<a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/4.png"><img class="aligncenter wp-image-622 size-full" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/4.png" alt="4" width="488" height="438" /></a>
  </p>
  
  <p dir="ltr">
    In this case we will add more space to the disk. Simply specify the desired total amount and click OK.<a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/5.png"><img class="aligncenter size-full wp-image-623" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/5.png" alt="5" width="501" height="477" /></a>
  </p>
  
  <p dir="ltr">
    Once your request has been placed, it will be resolved after a few minutes. You can check its status on the &#8220;My Requests&#8221; part of the home page. You will also get an email notification.<a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/6.png"><img class="aligncenter wp-image-624 size-full" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/09/6.png" alt="6" width="407" height="337" /></a>
  </p>
  
  <p dir="ltr">
    After that, a couple of commands need to be run in the target server in order to get the changes applied.
  </p>
  
  <p dir="ltr">
    Run:
  </p>
  
  <p dir="ltr">
    <strong>cfgmgr<br /> chvg -g rootvg</strong>
  </p>
  
  <p dir="ltr">
    With that, you should be able to see the new available space in the server with <strong>lsvg rootvg</strong>.
  </p>
  
  <p dir="ltr">
    In AIX, you can assign new space to a file system using the <strong>chfs</strong> command, like this:
  </p>
  
  <p dir="ltr">
    Change file system size:<br /> <strong>    chfs -a size=[-/+]N[GM] [/filesystem]</strong><br /> G=Gigabytes<br /> M=Megabytes
  </p>
  
  <p dir="ltr">
    Example:
  </p>
  
  <p dir="ltr">
    <strong>    chfs -a size=+200M /dev/fslv02</strong><br /> Filesystem size changed to 1835008
  </p>
</div>