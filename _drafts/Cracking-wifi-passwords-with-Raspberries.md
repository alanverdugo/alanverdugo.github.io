---
id: 1168
title: Cracking wifi passwords with Raspberries
date: 2016-03-10T21:27:07-05:00
author: Alan Verdugo
layout: post
guid: http://www.kippel.net/blog/?p=1168
permalink: /?p=1168
categories:
  - Uncategorized
---
<p style="text-align: justify;">
  So far I&#8217;ve been doing a few things with the Raspberries. I build a Hadoop cluster with them as a proof of concept, and I also used one for more playing videogames and watching videos.
</p>

<p style="text-align: justify;">
  However, I felt that it was time for more exciting things.
</p>

<p style="text-align: justify;">
  Since I mostly work from home, I need to be online many hours every day. To be honest, when I finish work I am online anyway, I just switch from my work laptop to my personal laptop. However, I do need to keep a work schedule and be available online in case my co-workers try to reach me or when I have meetings. In other words, I rely heavily on my internet connection. If it goes down, I need to act quickly and go to a cafe with wifi. And I don&#8217;t like that, cafes tend to be noisy, expensive and full of people.
</p>

<p style="text-align: justify;">
  So I wanted to have backup connections from home.
</p>

<p style="text-align: justify;">
  In order to crack the passwords of these connections, there are some requirements. First, I needed a USB wireless adapter that could help me to crack them. The two adapters that came included with the Raspberries I received would not work since they do not have packet injection and promiscuous mode.
</p>

<p style="text-align: justify;">
  I bought a TP-Link TL-WM722N. It was cheap (around 10-15 dlls) and it appeared on most list of recommended devices for what I wanted.
</p>

<p style="text-align: justify;">
  I found a custom ARM image of Kali Linux built specifically for the Raspberry 2. I downloaded it and validated it.
</p>

<p style="text-align: justify;">
  wget https://images.offensive-security.com/arm-images/kali-2.1-rpi2.img.xz
</p>

<p style="text-align: justify;">
  sha1sum kali-2.1-rpi2.img.xz<br /> 1940438fe85f5850e10ea6c14d0aebefc1266985  kali-2.1-rpi2.img.xz
</p>

<p style="text-align: justify;">
  Intalled it into a micro SD card.
</p>