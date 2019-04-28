---
id: 1852
title: Massively modifying images with ImageMagick
date: 2016-12-12T11:48:22-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=1852
permalink: /?p=1852
---
<p style="text-align: justify;">
      Web editors often have the need to edit a large number of images. For example, the large image size of professional cameras tends to be overkill for most sites. I wanted a quick and easy way to resize large images and that was how I found <a href="http://www.imagemagick.org/script/index.php" target="_blank">ImageMagick</a>.
</p>

<p style="text-align: justify;">
      ImageMagick is a suite of tools and according to the man page, we can &#8220;use it to convert between image formats as  well  as  resize  an image, blur, crop, despeckle, dither, draw on, flip, join, re-sample, and much more&#8221;. First, let&#8217;s install imagemagick:
</p>

<pre class="theme:son-of-obsidian font:droid-sans-mono font-size-enable:false toolbar:2 striped:false nums:false wrap:true lang:sh decode:true">sudo apt-get install imagemagick</pre>

<p style="text-align: justify;">
      Then, we can use the <strong>convert</strong> command to do the actual edition. Check the man page to see the astounding number of options this command has. For example, if I want to resize all the JPG images in the current directory to a width of 1280 pixels and save the resulting images as the same name but with &#8220;min-&#8221; before the name I would execute the following command:
</p>

<pre class="theme:son-of-obsidian font:droid-sans-mono font-size-enable:false toolbar:2 striped:false nums:false wrap:true lang:sh decode:true">for file in *.JPG; do convert $file -resize 1280 min-$file; done</pre>

<p style="text-align: justify;">
      And here lies the advantage of ImageMagick: it can be used in a script to edit images extremely quickly. ImageMagick can also be used on Mac OS X and Windows. For more information about the convert command, refer to <a href="http://www.imagemagick.org/script/convert.php" target="_blank">http://www.imagemagick.org/script/convert.php</a>
</p>