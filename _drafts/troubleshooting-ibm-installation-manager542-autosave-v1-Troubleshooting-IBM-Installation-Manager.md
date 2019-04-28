---
id: 550
title: Troubleshooting IBM Installation Manager
date: 2014-06-30T11:05:00-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=550
permalink: /?p=550
---
<p style="text-align: justify;">
      Sometimes, when you try to run IBM Installation Manager (IM), you may get an error like this:
</p>

<pre class="theme:terminal font:ubuntu-mono striped:false nums:false wrap:true lang:default decode:true ">00:43.15 ERROR [main] org.eclipse.equinox.log.internal.ExtendedLogReaderServiceFactory safeLogged
Could not load SWT library. Reasons:
/opt/IBM/WebSphere/IM/eclipse/configuration/org.eclipse.osgi/bundles/288/1/.cp/libswt-pi-gtk-4234.so (libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory)
swt-pi-gtk (Not found in java.library.path)
/root/.swt/lib/linux/s390/libswt-pi-gtk-4234.so (libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory)
/root/.swt/lib/linux/s390/libswt-pi-gtk.so (/root/.swt/lib/linux/s390/liblibswt-pi-gtk.so.so: cannot open shared object file: No such file or directory)
............
</pre>

<p style="text-align: justify;">
      This is due to IM not being able to run because the server does not have a proper graphical environment configured. The most probable reason for this is because GTK2 is not installed. IM is based on Eclipse and they rely heavily on graphical libraries.
</p>

<p dir="ltr" style="text-align: justify;">
      The following example is based on a SUSE Linux Enterprise Server 10 SP4 (s390x). The version of IBM Installation Manager we will fix is 1.6.2. Other configurations may or may not work and may or may not apply to this guide. Let me know in the comments section if it worked for you.
</p>

<p dir="ltr" style="text-align: justify;">
      You could try to install GTK2 using <strong>rpm -i</strong> but if you decide to follow this path you need to be prepared to enter the Dependency Hell. Abandon all hope, ye who enter here.
</p>

<p dir="ltr" style="text-align: justify;">
      In this guide we will use YaST in order to properly install GTK2 and all its dependencies, this should be enough to get IM up and running. According to your OS, you could use smitty, yum, or any other available means. The goal here is to install all the dependencies correctly and without conflicts. If you do it manually, it may take a long time, and you run the risk of not getting anywhere or breaking stuff that was already working.
</p>

<p dir="ltr" style="text-align: justify;">
      Enter into the server via SSH and execute YaST (just type &#8220;yast&#8221; and hit enter). Make sure to login using the -X or -Y flag in SSH. E.g. <strong>ssh -X root@hostname</strong>
</p>

<p dir="ltr" style="text-align: justify;">
      A beautiful blue screen should appear. This is YaST, where you move with the tab key and the arrow keys, and select options with enter.
</p>

<p dir="ltr" style="text-align: justify;">
      Select <strong>Software</strong> and then <strong>Software Management</strong>. It may take a while to initialize and you may get warnings or error messages about the software repository.
</p>

<p dir="ltr" style="text-align: justify;">
  <a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/06/yast1.png"><img class="aligncenter  wp-image-544" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/06/yast1.png" alt="yast1" width="584" height="224" /></a>
</p>

<p dir="ltr" style="text-align: justify;">
      After that, select <strong>Search</strong> and type &#8220;<strong>gtk</strong>&#8220;, the select <strong>OK</strong>.
</p>

<p dir="ltr" style="text-align: justify;">
  <a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/06/yast2.png"><img class="aligncenter  wp-image-545" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/06/yast2.png" alt="yast2" width="512" height="468" /></a>
</p>

<p dir="ltr" style="text-align: justify;">
      The following are the packages that I installed in my zLinux server (the ones marked with &#8220;i&#8221; in the first column). You may not need all of them, and some of them may not apply in your case but this is a good reference for what should be installed for IM to work.
</p>

<p dir="ltr" style="text-align: justify;">
      Note that this server has a 64 bits architecture and thus we mostly ignore the 32 bits packages.
</p>

<p dir="ltr" style="text-align: justify;">
  <a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/06/gtk2.png"><img class="aligncenter  wp-image-546" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/06/gtk1.png" alt="gtk1" width="755" height="273" /><img class="aligncenter wp-image-547" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/06/gtk2.png" alt="gtk2" width="755" height="179" /></a>
</p>

<p dir="ltr" style="text-align: justify;">
      Once you have marked all the packages you want to install (they will be marked with a plus sign) select <strong>Accept</strong> and they should be installed.
</p>

<p dir="ltr" style="text-align: justify;">
      With the packages installed, try to run IM again and this time it should work.
</p>

<p dir="ltr" style="text-align: justify;">
  <a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/06/IM.png"><img class="aligncenter size-full wp-image-543" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2014/06/IM.png" alt="IM" width="796" height="571" /></a>
</p>

<p dir="ltr" style="text-align: justify;">
      This solution seems simple and maybe obvious but you can spend many hours trying to fix this problem. I have been there and I have seen many people struggling with IM. In the past I approached this problem trying to change the library paths and doing other desperate things I found on the Internet, but this is the only solution that finally worked for me. I hope this helps.
</p>