---
id: 1094
title: Introduction to Raspberry Pi, OpenELEC and RetroPie
date: 2016-01-08T19:30:14-05:00
author: Alan Verdugo
guid: http://www.kippel.net/blog/?p=1094
permalink: /blog/raspberry-openelec
#permalink: /?p=1094
categories:
  - Uncategorized
tags:
  - english
  - IT
---
<p style="text-align: justify;">
      Being such a good boy finally was worth it, and last Christmas <del>Santa</del> <a href="http://metzonalli.net/" target="_blank">Briana</a> gave me a <a href="https://www.raspberrypi.org/products/raspberry-pi-2-model-b/" target="_blank">Raspberry Pi 2 Model B</a>. Not only that, but she went the extra mile and got me an <a href="http://www.canakit.com/raspberry-pi-starter-ultimate-kit.html" target="_blank">Ultimate kit</a> from <a href="http://www.canakit.com/" target="_blank">Canakit</a>, which includes many extra toys to play with. This is easily one of the best gifts I&#8217;ve ever received, and after I got it I knew that I will get more Raspberries sooner or later.
</p>

<p style="text-align: justify;">
      If you have been living under a rock in Mars, I&#8217;ll briefly explain what a Raspberry is and why they are so popular with the <a href="http://hackaday.com/category/raspberry-pi-2/" target="_blank">hacker/maker/DIY</a> scene. A Raspberry (besides a fruit) is basically just a tiny computer, about the size of a credit card. It doesn&#8217;t even come inside a case (you have to buy extra accessories separately, or buy a custom kit). Due to the small form factor. It does not have a lot of processing power, but this offers advantages like a low price, and low power consumption. All this makes it perfect to use it in education, electronics, clustering or embedded projects.
</p><figure id="attachment_1103" aria-describedby="caption-attachment-1103" style="width: 548px" class="wp-caption aligncenter">

<img class="size-full wp-image-1103" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/Pi2ModB1GB_-comp.jpeg" alt="Yes, that is the whole thing." width="548" height="300" /> <figcaption id="caption-attachment-1103" class="wp-caption-text">Yes, that is the whole thing.</figcaption></figure> 

<p style="text-align: justify;">
      After thinking a couple of minutes about what to do with it, I choose two initial projects: OpenELEC and RetroPie. The Ultimate kit comes with an 8GB micro-SD card that comes pre-installed with &#8220;<a href="https://www.raspberrypi.org/help/noobs-setup/" target="_blank">NOOBS</a>&#8221; (New Out Of the Box Software), an utility that installs Raspbian into the same micro-SD card so you are good to play with it. One of the best things with Raspberries is that you can switch micro-SD cards to instantly have a new OS or set of tools. So, I went ahead and bought two 32GB micro-SD cards.
</p>

<p style="text-align: justify;">
  <img class="aligncenter  wp-image-1099" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/raspbian.png" alt="raspbian" width="157" height="157" />
</p>

<p style="text-align: justify;">
      <a href="http://www.raspbian.org/" target="_blank">Raspbian</a> is an operating system based on Debian, optimized for use in a Raspberry. Together, Raspbian and a Raspberry provide more than enough resources for people who may want to learn Linux, programming, or just basic computer usage at a very low cost. I could see this being distributed to young kids as a way to encourage their education, in fact, this was <a href="https://www.raspberrypi.org/about/" target="_blank">the vision</a> of the Raspberry creators. I know I would have killed to have access to something like this when I was younger. Raspbian does need some basic setup for things like setup the wifi, so you may need a keyboard, mouse, and an ethernet cable. Then you can connect remotely to the Raspberry. I was lucky to have a wireless keyboard that <a href="http://elavena.mx/" target="_blank">Avena</a> brought from Japan, so I used that.
</p>

<p style="text-align: justify;">
  <img class="aligncenter size-full wp-image-1102" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/openelec.png" alt="openelec" width="242" height="69" />
</p>

<p style="text-align: justify;">
      <a href="http://openelec.tv/" target="_blank">OpenELEC</a> (Open Embedded Linux Entertainment Center) is a beautiful attempt at creating a free, open source and very complete media center. It uses <a href="https://www.kodi-xbmc.com/" target="_blank">Kodi</a> (formerly known as XBMC) to do the heavy lifting, which is another very mature open source project. It is not exclusive to run on Raspberries (although it offers an optimized image for them), so it can be installed on any hardware that you may not use anymore and convert it into a full-fledged entertainment center. I was very impressed with the results and I think it even surpasses things like Netflix, AppleTV or Google&#8217;s Chromecast. It has many features, like support for wide variety of video, audio and image formats, subtitles support (it can even connect to the internet and look for subtitles for the movies you are watching), auto-updates and many things that I haven&#8217;t discovered yet.
</p>

<p style="text-align: justify;">
  <img class="aligncenter  wp-image-1100" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/retropie.png" alt="retropie" width="169" height="226" />
</p>

<p style="text-align: justify;">
      <a href="http://blog.petrockblock.com/retropie/" target="_blank">RetroPie</a> is an open source project aimed specifically to convert a Raspberry into the ultimate emulating machine. In the same way OpenELEC uses Kodi, RetroPie uses <a href="http://www.emulationstation.org/" target="_blank">EmulationStation</a>, which is, as you must guess by now, another open source project. You basically download a Debian-based image that includes pre-installed emulators for old games, install it into a micro-SD card, add your ROMs, and you are good to go. A lot of effort has been put into this project and it shows in how easy it is to use. After probably 30 minutes I was already playing my favourite old games with a controller in my HD screen. Since this project is specifically designed for standardized Raspberry hardware, any compatibility problems have been solved long ago. The majority of the games play flawlessly, maybe even better than on PCs, so far I&#8217;ve only had problems with a few N64 games and a few hacked ROMs for the SNES. I am eager to test it with Dreamcast games and see if the tiny Raspberry can handle them, however, I don&#8217;t think there should be any problems since it can natively run 3D games like Quake 3 Arena without any drop in fps. My old wired Acteck USB gamepad was recognized instantly. However, I wanted to play wirelessly so I got a TRENDnet Bluetooth (TBW-107UB) adapter and configured a Dualshock 3 to work with it. Now I can just turn on my Raspberry, turn on my TV, choose a game, and start playing. The only thing I regret is only getting a 32GB micro-SD card. I should have gotten a 64GB or even 128GB card (I got around 14,000 ROMs just for the SNES and they barely fit on my card). RetroPie was created by people who, like me, grew up with old videogames and wanted to enjoy them again as they were meant to be played, on a TV and with a gamepad, but not using a high-end PC for it. Those people and their passion have made this a very polished and complete project, which, for me, makes the Raspberry pay itself instantly.
</p>

<p style="text-align: justify;">
  <strong>Conclusion:</strong>
</p>

<p style="text-align: justify;">
      Raspberries were a game-changer. The unexpected approach of selling a low-cost and low-resource hardware has been proven very successful and many have tried to replicate it. If you think about it, this is the opposite of the high-specs, high-price closed-source model that some companies like Apple have tried to shove down our throats for years. And this is good, some parts of the world and some economic sectors just need an easy and cheap way into computer literacy. In order to learn, people (specially kids) need a proving ground that they can break without the worry of wasting hundreds of dollars, and what better way than to leverage the open source projects for that. As a side effect, the FLOSS community (and with it, all of the IT industry) has been improved thanks to the Raspberry project, which in turn has spawned many software and hardware projects on its own. Any of the related projects (From Linux to Kodi, OpenELEC, RetroPie, EmulationStation, and the Raspberry) have an astounding quality and deserve any and all the contributions. As for me, I will think about what to do next, since Raspberries have a lot of potential, it is hard to decide what to do with them.
</p>