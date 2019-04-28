---
id: 834
title: The power of the return code
date: 2015-07-27T19:53:39-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=834
permalink: /?p=834
---
<p style="text-align: justify;">
      The correct handling of return values made my life as a programmer much easier. That is the whole purpose of their creation. I can write code that will check itself and will notice if any step of any program failed or produced an undesired result, and act accordingly. Checking the return values allows a programmer to write incredibly robust programs.
</p>

<p style="text-align: justify;">
      I wanted to write a post about this, thinking in rookie programmers. I tried to make it as useful and easy to understand as possible.
</p>

<p style="text-align: justify;">
  <strong>    echo</strong> is a UNIX/Linux command that will show a message in the screen. <strong>$?</strong> is a special variable that stores the return code of the last ran command. Together they are a powerful tool used for programming and systems administration.
</p>

<p style="text-align: justify;">
      A program should <em>always</em> return a value. Any coding standard should have these lines in it:
</p>

> <p style="text-align: justify;">
>   A successful program should return 0 upon correct completion.
> </p>
> 
> <p style="text-align: justify;">
>   An unsuccessful program should return a non-zero value.
> </p>

<p style="text-align: justify;">
      For example, let&#8217;s write a shell script that creates an empty file named &#8220;file.txt&#8221; in /home/user1. The most basic version of this script would be something like this:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false lang:sh decode:true">touch /home/user1/file.txt</pre>

<p style="text-align: justify;">
      That&#8217;s it, just one line. Simple, uh? Well, maybe it is <em>too</em> simple. What if there is no free space in the file system? What if the user running the command does not have writing permission on that path? What if that path does not even exists? What if there is already a file there with the same name? Should we overwrite it?
</p>

<p style="text-align: justify;">
      The following is a shell script that is a little more robust (but still very simple). It completes the same task but it checks for more possible failure scenarios:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false lang:sh decode:true ">#!/bin/sh

# Author: Alan Verdugo
# 
# Return codes:
# 0 - Great success! The file was created.
# 1 - There is already a file with that name there.
# 2 - We attempted to create the file but it was not created.
# 3 - We attempted to create the file but we cannot write on that path.
# 4 - The path itself does not exist.

# Check if the file already exists...
if [ -e /home/user1/file.txt ]
then
	echo "ERROR: There is a file in that path with the same name!"
	exit 1
else
	# Great, the file does not exists.
	# Now let's check if the path actually exists.
	if [ -e /home/user1 ]
	then
		# Now check if we can write on this path.
		if [ -w /home/user1/ ]
		then
			# We go ahead and attempt to create the file.
			touch /home/user1/file.txt
			# Check if the file was created succesfully.
			if [ -e /home/user1/file.txt ]
			then
				echo "File created successfully!"
				exit 0
			else
				echo "ERROR: File was unable to be created!"
				exit 2
			fi
		else
			echo "ERROR: We cannot write on this path!"
			exit 3
		fi
	else
		echo "ERROR: The path does not exists!"
		exit 4
	fi
fi</pre>

<p style="text-align: justify;">
      The &#8220;exit&#8221; command means to abort the program and return to the OS with the integer that follows the &#8220;exit&#8221; keyword. You may notice that the only successful scenario ends the program with &#8220;exit 0&#8221; and all the other (failed) scenarios end with &#8220;exit&#8221; and a positive integer. So, after the program ends, the programmer or sysadmin can easily check if the program succeeded or not. For example, something like this could happen:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false lang:sh decode:true">$ ./return_codes.sh
ERROR: The path does not exists!
$ echo $?
4</pre>

<p style="text-align: justify;">
       In the example above, the script failed and it showed us a pretty message explaining why. It also returned the value 4. If our script is called by another script, that caller script can check easily if a non-zero value is returned (i.e. if the script failed). The following is an example of a successful execution:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false lang:sh decode:true">$ ./return_codes.sh
File created successfully!
$ echo $?
0</pre>

<p style="text-align: justify;">
      If you play with the &#8220;stock&#8221; programs in a default UNIX/Linux installation, you can see this behaviour as well. For example:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false lang:sh decode:true">$ date
Mon Jul 27 12:13:46 CDT 2015
$ echo $?
0
</pre>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false lang:sh decode:true">$ find . -name helloWorld.sh
$ echo $?
0</pre>

<p style="text-align: justify;">
       Wait! Why did the &#8220;find&#8221; command returned a zero?! It did not find the file we asked it to find! The reason is because the execution of the &#8220;find&#8221; program completed successfully. The fact that it was unable to find a file named &#8220;helloWorld.sh&#8221; is another matter entirely. In other words, this means the &#8220;find&#8221; program is telling us that it is functioning properly, it is not its fault that the file you try to find does not exist there. A nice thing to have in mind&#8211; Computers will do what you tell them to do, not always what you wish they will do.
</p>

<p style="text-align: justify;">
       Code like this makes our programs more robust, and can help us to avoid catastrophic failures and emergency calls late at night. Different programming languages and paradigms offer different ways to accomplish this same idea. The &#8220;try-catch&#8221; statements are good examples of this.
</p>

<p style="text-align: justify;">
      The truth is, you can write a program as complicated as you want. There are many ways to improve the previous script. You need to know when it is &#8220;sufficiently completed&#8221; and stop there. We could continue on and on with our little script and add fancy functionality like sending a failure report via email, creating the file in an alternative path if the first path does not allow it for some reason, etc. But let&#8217;s stop there for now.
</p>