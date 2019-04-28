---
id: 382
title: The power of echo $?
date: 2014-03-07T13:15:49-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=382
permalink: /?p=382
---
<p style="text-align: justify;">
  The correct handling of return values and echo $? made my life as a programmer much more easier, that is the whole purpose of their creation. I can write code that will check itself and will notice if any step of any program failed or produced an undesired result, and act accordingly. Checking the return values allows a programmer to write incredibly robust programs.
</p>

<p style="text-align: justify;">
  A program should always return a value. Any coding standard should have these lines in it:
</p>

> <p style="text-align: justify;">
>   A successful program should return 0 upon completition.
> </p>
> 
> <p style="text-align: justify;">
>   An unsuccessful program should return a non-zero value.
> </p>

<p style="text-align: justify;">
  For example, let&#8217;s write a shell script that creates an empty file named &#8220;file.txt&#8221; in /home/user1. The most basic version of this script would be something like this:
</p>

<pre class="lang:sh decode:true">touch /home/user1/file.txt</pre>

<p style="text-align: justify;">
  That&#8217;s it, just one line. Simple, uh? Well, maybe it is too simple. What if there is not free space in /home/user1? What if the user running the command does not have writing permission on that path? What if that path does not even exists? What if there is already a file there with the same name? Should we overwrite it?
</p>

<p style="text-align: justify;">
  <pre class="lang:sh decode:true ">#!/bin/sh

# If the file already exists...
if [ -e /home/user1/file.txt ]
then
        echo "Error: There is a file already there!"
        exit 1
else
        # The file does not exists!
        # Now let's check if the path actually exists
        if [ -e /home/user1 ]
        then
                # Now check if we can write on this path
                if [ -w /home/user1/ ]
                then

                        # We go ahead and attempt to create the file
                        touch /home/user1/file.txt

                        echo "File created succesfully!"
                        exit 0
                else
                        echo "Error: We cannot write on this path!"
                        exit 2
                fi
        else

        fi
fi</pre>
  
  <p>
    &nbsp;
  </p>
  
  <p style="text-align: justify;">
    <p style="text-align: justify;">
      The truth is, you can write a program as complicated as you want. You need to know when it is &#8220;sufficiently completed&#8221; and stop there. We could continue on and on with our little program and add things  like sending a failure report via email, creating the file in an alternative path if the first path does not allow it for some reason, etc. But let&#8217;s stop there for now.
    </p>