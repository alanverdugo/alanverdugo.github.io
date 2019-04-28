---
id: 2013
title: Disaster alerting network
date: 2017-08-02T00:58:01-05:00
author: Alan Verdugo
layout: post
guid: http://www.kippel.net/blog/?p=2013
permalink: /?p=2013
categories:
  - Uncategorized
---
<p style="text-align: justify;">
  During disasters, the communications infrastructure becomes overloaded mainly due to people trying to communicate their status to the outside world, or by people in other cities trying to reach their relatives in the disaster zone.
</p>

<p style="text-align: justify;">
  We need an offline network that is able to quickly and easily communicate the status of the affected people.
</p>

<p style="text-align: justify;">
  We should prevent the communication infrastructure to become overloaded in first place. We need to stop trying to reach people in the affected areas until we know for sure that calling them will not prevent another more important call to go trough. Still, people will want to communicate their location and status to the outside world and there is no standard way to do this yet.
</p>

<p style="text-align: justify;">
  I propose the following solution: Let&#8217;s imagine a city that has been destroyed by a disaster, for example, an earthquake. During this situations, Internet, land-line and cellphone connectivity could be reduced or even become completely unavailable.
</p>

> <p style="text-align: justify;">
>   Communications were primitive at best. Cellular service was completely gone. In the first few minutes after the planes hit the towers, New York City’s 9-1-1 call centers received 3,000 calls – throughout that day, <a href="http://psc.apcointl.org/2011/09/06/911-10-years-later/">more than 55,000 came in</a>.
> </p>
> 
> <p style="text-align: justify;">
>   Thousands of law enforcement officers and firefighters were <a href="http://psc.apcointl.org/2011/08/10/10-years-later-n-y-responders-communicate-better/">trying to connect by phone, radio</a> and <a href="https://www.schneier.com/blog/archives/2009/11/leaked_911_text.html">two-way pager</a>. Devices and networks, not to mention personnel, were overloaded. <a href="http://www.cbsnews.com/news/communication-breakdown-on-9-11/">Police radios were generally working</a>, but the best information was often by word of mouth.
> </p>
> 
> <p style="text-align: justify;">
>   At our office-building clinic, the volunteers resorted to face-to-face communication, sending people to meet up with a group of responders gathering on the nearby Pace University campus and bring back what information they could.
> </p>
> 
> http://theconversation.com/disaster-communications-lessons-from-9-11-65142

<p style="text-align: justify;">
  All this means that we cannot rely on any kind of communication networks, and, if they are still available, we need to avoid overloading them with unnecessary traffic.
</p>

<p style="text-align: justify;">
  A smartphone should be able to communicate wirelessly to nearby cellphones. It would transfer the following data:
</p>

<p style="text-align: justify;">
  -Last 4 digits of the cellphone number.
</p>

<p style="text-align: justify;">
  -Name of the owner.
</p>

<p style="text-align: justify;">
  -Health status of the owner (for example: healthy, lightly wounded, seriously wounded, sick, etc.)
</p>

<p style="text-align: justify;">
  -A custom short message (for example: &#8220;I am fine, don&#8217;t worry&#8221;, &#8220;Looking for my family&#8221;, &#8220;I am sick, at shelter #42&#8221;).
</p>

<p style="text-align: justify;">
  -Timestamp of the reception of the data.
</p>

<p style="text-align: justify;">
  Since this local wireless communication would transfer between cellphones, every cellphone should have a full copy of the list of every cellphone that contacts. For example, let&#8217;s say that a massive earthquake happens in a big city, many buildings collapse and people is unable to communicate using the normal means. After the earthquake, a user (let&#8217;s call her Alice) opens the application, sets her status as &#8220;healthy&#8221; and her custom message as &#8220;I am fine. Do not worry&#8221;. Once she gets close to another person using the same application (let&#8217;s call him Bob), Alice will passively transfer her data to Bob&#8217;s cellphone, and Bob&#8217;s cellphone will transfer his data to Alice&#8217;s phone. Now both Alice and Bob have a list with two people and their respective data. Now let&#8217;s say that Bob continues walking and encounters a third user (Cathy) who is also using the application. Cathy&#8217;s phone will transfer her complete list of encounters to Bob&#8217;s cellphone, and viceversa. This way, Cathy&#8217;s phone will know that Alice (among other people) was not wounded. Once Cathy&#8217;s cellphone is able to connect to the internet, it will transfer all of its stored data to a central repository, where other people should also have uploaded similar data. In this way, Alice and Bob (in this example) would eventually have communicated their health status and their respective messages to the outside world, even if they completely lost any connectivity. Alice&#8217;s and Bob&#8217;s relatives would be able to check the central repository, where they could search for their names and see if they are doing fine. This will allow people to have peace of mind and wait until the communications infrastructure is completely restored before attempting to communicate with their affected relatives, and this, in turn, will prevent the overload of the communications networks.
</p>