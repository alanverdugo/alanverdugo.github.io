---
id: 724
title: User access control based on eye-tracking
date: 2017-04-23T17:24:31-05:00
author: Alan Verdugo
layout: post
guid: http://www.kippel.net/blog/?p=724
permalink: /?p=724
categories:
  - Uncategorized
tags:
  - idea
  - IT
  - patent
---
<p style="text-align: justify;">
  <strong><a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2015/06/cellphone.png"><img class="aligncenter wp-image-820" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2015/06/cellphone.png" alt="cellphone" width="244" height="610" /></a></strong>
</p>

<p style="text-align: justify;">
  <a href="http://li106-124.members.linode.com/blog/wp-content/uploads/2015/06/eye_access.png"><img class="aligncenter size-full wp-image-824" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2015/06/eye_access.png" alt="eye_access" width="467" height="663" /></a>
</p>

<p style="text-align: justify;">
  <strong>1. Background: What is the problem solved by your invention?  Describe known solutions to this problem (if any). What are the drawbacks of such known solutions, or why is an additional solution required?  Cite any relevant technical documents or references.</strong>
</p>

<p style="text-align: justify;">
  Hardware and software systems often need to ensure that only the appropriate users can access their information or make use of system&#8217;s functionality. In order to solve this problem, many authentication methods exist and each of them have their own advantages and disadvantages. The most common method in authentication is the password (a combination of secret characters that is supposed to only be known by the approved user or users). However, password have various disadvantages: They are generally typed into a keyboard, which makes them vulnerable to several hacking methods, like shoulder-surfing, and key-logging. The fact that passwords need to be typed also is a disadvantage for people with certain disabilities (for example, the lack of precise control in their hands or even the lack of fingers or of the hand itself).
</p>

<p style="text-align: justify;">
  User-facing cameras are ubiquitous in today&#8217;s devices like laptops, cellphones and tablets. Eye-tracking software is also becoming more and more ubiquitous for different applications.
</p>

<p style="text-align: justify;">
  This document describes a new authentication method that will exploit the new hardware and software capabilities in order to provide and easier and more secure experience for users while maintaining or even improving the security of the process of authentication.
</p>

**Prior Art Search Terms:**

Eye tracking authentication.

<p style="text-align: justify;">
  Eye tracking password.
</p>

<p style="text-align: justify;">
  Visual password.
</p>

**Prior Art**  
**Search Term Used:** Eye tracking authentication.  
**Found:** Patent #<span class="patent-number">US 8506080 B2 (Unlocking a screen using eye tracking information) </span><a href="https://www.google.com/patents/US8506080" target="_blank" rel="noopener noreferrer">https://www.google.com/patents/US8506080</a>  
**Issue:** This method of authentication does relies on eye-tracking information but it is not based on the user staring at certain fixated points of the screen, it relies on the user following movement with his or her eyes, the system gathering the information about that movement and comparing it to the expected movement of user&#8217;s eyes.**  
** 

<p style="text-align: justify;">
  <strong>Search Term Used:</strong> Visual password.<br /> <strong>Found: </strong>Patent #<span class="patent-number">US 20060206918 A1 (System and method for using a visual password scheme)</span> <a href="http://www.google.com/patents/US20060206918" target="_blank" rel="noopener noreferrer">http://www.google.com/patents/US20060206918</a><br /> <strong>Issue: </strong>This method of authentication still uses a key-based input mechanism and it relies in associations of characters with graphical features.<strong><br /> </strong>
</p>

<p style="text-align: justify;">
  <strong>Search Term Used:</strong> Visual password.<br /> <strong>Found:</strong> Patent #<span class="patent-number">US 8024576 B2</span> (<span class="patent-title">Method and system for authenticating users with a one time password using an image reader</span>) <a href="http://www.google.com.ar/patents/US8024576" target="_blank" rel="noopener noreferrer">http://www.google.com.ar/patents/US8024576</a><br /> <strong>Issue: </strong>This is a method of generating password with the interaction of a screen and an image reader. It does not involve eye-tracking technology.<strong><br /> </strong>
</p>

<p style="text-align: justify;">
  <strong>Search Term Used:</strong> Visual password.<br /> <strong>Found:</strong> Patent #<span class="patent-number">US 20140201832 A1</span> (<span class="patent-title">Method and apparatus for authenticating password of user terminal by using password icon</span>) <a href="http://www.google.com/patents/US20140201832" target="_blank" rel="noopener noreferrer">http://www.google.com/patents/US20140201832</a><br /> <strong>Issue: </strong>This method of authentication relies on the user moving an icon across the screen of a touch device. It does not involve eye-tracking technology.<strong><strong><br /> </strong></strong>
</p>

<p style="text-align: justify;">
  <strong>2. Summary of Invention: Briefly describe the core idea of your invention (saving the details for question #3 below).  Describe the advantage(s) of using your invention instead of the known solutions described above.</strong>
</p>

**The invention is**: A method for users of a software system to exchange information with said system. This information is the point in the device to which the user is gazing. If the point where the user is facing is currently showing a previously selected secret figure, the user is authenticated successfully and gains access to the system. If the point where the user is facing is currently showing a different figure, the user is not authenticated successfully and this actions counts as a failed attempt to log in.

**Advantages are:**

<li style="text-align: justify;">
  Improved security. This authentication method is virtually impervious to &#8220;shoulder surfing&#8221; attacks. For a human, it is almost impossible to tell the exact point where a person is looking.
</li>
<li style="text-align: justify;">
  Improved customization for passwords. The user can choose to set his or her password to a specific figure, a color, a letter or to the position of the shape. The user is also able to customize the amount of time that is required staring at the correct &#8220;password&#8221; for the authentication to complete. Any combination of these factors is also possible, improving the password strength even further. For example, the user could choose to authenticate while staring at a purple-colored square with the letter &#8220;B&#8221; in it for more than 4 seconds, making it a strong &#8220;password&#8221;. A simpler example would be to stare at any hexagon with for only two seconds, this would be an example of a weaker &#8220;password&#8221;.
</li>
<li style="text-align: justify;">
  Improved usability. Individuals with disabilities will find this authentication method easier to use. For example, typed passwords are hard to use for individuals with hand-related disabilities. In order to use this authentication method, the only requirement is to have control over his or her eye movement.
</li>
<li style="text-align: justify;">
  Future-proof. New devices like VR and AR headsets will require an authentication method that does not depend on typed passwords or voice recognition. The proposed authentication method will integrate perfectly to the nature of these devices.
</li>
<li style="text-align: justify;">
  This method offers a similar experience to the retina scan authentication method, but in a way that is much more customizable, comfortable, cheaper and easier to implement.
</li>

<p style="text-align: justify;">
  <strong>3. Description:  Describe how your invention works, and how it could be implemented, using text, diagrams and flow charts as appropriate.</strong><br /> <strong>Scenario</strong>
</p>

<p style="text-align: justify;">
  A user could grab a mobile device or sits down in front of a screen with a front-facing camera. Using eye-tracking hardware and software, the device checks the point in the screen where the user is looking at. A grid of randomized figures would appear in the screen and the user would stare and the correct figure or series of figures in order to be authenticated successfully. The user can choose to customize every factor of the shared secret in order to make it stronger to hacking attempts. For example, the user could choose to authenticate while staring at a purple-colored square with the letter &#8220;B&#8221; in it for more than 4 seconds, once that step was completed a new grid of randomized figures would appear on the screen and the user would need to stare at a blue-colored octagon with a star on it. This would be an example of a strong &#8220;password&#8221;. An easier example would be the user staring at any hexagon figure (of any color, pattern, etc.) in the grid for only two seconds in order to be authenticated, this would be an example of a weaker &#8220;password&#8221;.
</p>

<p style="text-align: justify;">
  Once the user is authenticated and gains access to the system, he or she also gains the ability to change its password, the following characteristics would be available for password customization purposes:
</p>

<p style="text-align: justify;">
  Figure: The users selects any geometric figure from a wide selection.
</p>

<p style="text-align: justify;">
  Insert: The user selects any alphanumeric character or special symbol that would be contained inside the figure selected above.
</p>

<p style="text-align: justify;">
  Color or pattern: The user selects a color or pattern (e.g. checkered, plaid, etc), the figure selected above would be associated with this color or pattern.
</p>

<p style="text-align: justify;">
  Time: The user select a number in seconds. This would be the time needed to stare at the figure with the characteristics chosen above in order to complete a successful authentication. If the user stares at the correct figure, but does so less time than the chosen in this parameter, the authentication will not complete.
</p>

<p style="text-align: justify;">
  Steps: The user could choose to repeat the same process details above more than once. For example, if the users chooses two steps, a new combination of Figure-Insert-Color/Pattern-Time combination would be needed to be selected by the user in order to gain access to the system. This would be akin to having the system protected by several passwords, and the user correctly typing one by one until all of the correct passwords are provided to the system, thus, the user is successfully authenticated.
</p>

<p style="text-align: justify;">
  Grid characteristics: The user selects how many randomized figures will be shown in the grid at the start of the authentication process. If the user selects a low number of randomized figures, it would be easier for an attacker to guess which one is the user looking at.
</p>

<p style="text-align: justify;">
  Since the proposed authentication method will not rely on passwords per se, I propose to coin the term &#8220;passpoint&#8221;, since the user needs to stare at a point (or at a group of points) in the screen for successful authentication.
</p>

<p style="text-align: justify;">
  In order to avoid &#8220;brute force&#8221; attacks (i.e. an attacker staring at all displayed symbols one by one until it finds a match), the software will treat each attempt as an invalid password. For example, if an attacker stares for more than 2 seconds to an incorrect symbol, an unsuccessful authentication attempt will be logged. The amount of time that is needed to discern if an attempt is valid or invalid, as well as the allowed number of attempts, could be customized by the user.
</p>

**for any part of the scenario that is not clear break it out into a section that shows the implementation**

**Additional Considerations**  
**The system may implement a policy and administration feature which controls the access to the invention.**

**Checklist:**  
**IS THE NOVEL PIECE HIGHLIGHTED!?!**  
**Is it descriptive enough?**  
**Does a diagram or picture explain it better?**  
**Does it have IBM business value (Cost)?**  
**Why is another solution needed?**

https://pupil-labs.com/



<blockquote class="reddit-card" >
  <p>
    <a href="https://www.reddit.com/r/dataisbeautiful/comments/66pjv2/i_wore_an_eye_tracker_while_playing_overwatch/?ref_source=embed&ref=share">I wore an eye tracker while playing Overwatch (full video in comments) [OC]</a> from <a href="https://www.reddit.com/r/dataisbeautiful/">dataisbeautiful</a>
  </p>
</blockquote>



&nbsp;

References:

<a href="http://en.wikipedia.org/wiki/Eye_tracking" target="_blank" rel="noopener noreferrer">http://en.wikipedia.org/wiki/Eye_tracking</a>

<a href="http://www.washington.edu/news/2013/07/16/eye-tracking-could-outshine-passwords-if-made-user-friendly/" target="_blank" rel="noopener noreferrer">http://www.washington.edu/news/2013/07/16/eye-tracking-could-outshine-passwords-if-made-user-friendly/</a>

<a href="https://www.google.com/patents/US8506080" target="_blank" rel="noopener noreferrer"> https://www.google.com/patents/US8506080</a>

https://github.com/JuliusSweetland/OptiKey

https://github.com/JuliusSweetland/OptiKey/wiki/Using-eye-trackers

http://dev.theeyetribe.com/general/

&nbsp;