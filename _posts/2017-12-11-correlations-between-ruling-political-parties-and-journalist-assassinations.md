---
id: 2124
title: Correlations between ruling political parties and journalist assassinations
date: 2017-12-11T22:48:31-05:00
author: Alan Verdugo
guid: http://www.kippel.net/blog/?p=2124
permalink: /blog/journalist-deaths
#permalink: /?p=2124
categories:
  - Uncategorized
tags:
  - data science
  - english
  - IT
  - programming
  - Python
  - Technical writing
---
<h4 style="text-align: center;">
  Abstract
</h4>

<p style="text-align: justify;">
      This research uses a dataset provided by the Committee to Protect Journalists in order to analyze the number of journalists’ deaths in Mexico and the US from 1992 to 2016, it compares both results, and tries to find out if the ruling political party is regarded as an important factor that could be the root cause of said deaths. The analysis points out that the ruling political party cannot be directly linked to the cause of the deaths, but the political strategies implemented by the government could be related indirectly.
</p>

<h4 style="text-align: center;">
  <a id="user-content-motivation" class="anchor" href="https://github.com/alanverdugo/journalists_deaths_analysis#motivation" aria-hidden="true"></a>Motivation
</h4>

<p style="text-align: justify;">
      Mexico is widely regarded as one of the most dangerous countries for journalists<sup>[1]</sup>, even comparing to countries in a state of war. Added to that, the mexican government is also famous for being corrupt and untrustworthy, either by bribing the media or by threatening it. This has happened since the 1910s<sup>[1]</sup>, and the involvement of Mexico in illegal drug traffic has only added to the dangers the journalists face.
</p>

<p style="text-align: justify;">
      Since the mexican government has been known to bride or to threaten journalists, I wanted to get actual data that could show a correlation between the ruling political parties of the past and the amount of violence towards media workers. This could help the mexican citizens to make a decision before the presidential election of 2018.
</p>

<h4 style="text-align: center;">
  <a id="user-content-dataset" class="anchor" href="https://github.com/alanverdugo/journalists_deaths_analysis#dataset" aria-hidden="true"></a>Dataset
</h4>

<p style="text-align: justify;">
      The dataset that will be used is a comma-separated file provided by the Committee to Protect Journalists (<a href="https://cpj.org" rel="nofollow">https://cpj.org</a>). It contains data about journalists assassinations committed from 1992 to 2016. The dataset contains 1782 records with 18 variables: <em>Type, Date, Name, Sex, Country_killed, Organization, Nationality, Medium, Job, Coverage, Freelance, Local_Foreign, Source_fire, Type_death, Impunity_for_murder, Taken_captive, Threatened, Tortured</em>.
</p>

<p style="text-align: justify;">
      The dataset can be downloaded from Kaggle.com: <a href="https://www.kaggle.com/cpjournalists/journalists-killed-worldwide-since-1992" rel="nofollow">https://www.kaggle.com/cpjournalists/journalists-killed-worldwide-since-1992</a>
</p>

<h4 style="text-align: center;">
  <a id="user-content-data-preparation-and-cleaning" class="anchor" href="https://github.com/alanverdugo/journalists_deaths_analysis#data-preparation-and-cleaning" aria-hidden="true"></a>Data preparation and cleaning
</h4>

<p style="text-align: justify;">
      Some of the records did not have a date for the death of the journalist (it was either labeled “Unknown” or “Date unknown”), this prevent me from assigning it to a year and thus to a presidential administration, so, sadly, I had to ignore them. Besides, the date format was relatively hard to parse since it was not in a very standard format. For example, the date was in the form “February 9, 1998”, instead of the much more international and easy to use “1998-02-09”.
</p>

<h4 style="text-align: center;">
  <a id="user-content-research-questions" class="anchor" href="https://github.com/alanverdugo/journalists_deaths_analysis#research-questions" aria-hidden="true"></a>Research questions
</h4>

<p style="text-align: justify;">
      Is there a correlation between the ruling political party and the number of journalists assassinations?
</p>

<p style="text-align: justify;">
      Can we identify a corrupt government by analyzing the acts of violence against journalists occurred during its administration?
</p>

<h4 style="text-align: center;">
  <a id="user-content-methods" class="anchor" href="https://github.com/alanverdugo/journalists_deaths_analysis#methods" aria-hidden="true"></a>Methods
</h4>

<p style="text-align: justify;">
      Using the Pandas library in Python, I filtered all records that belong to the interesting countries, then I grouped them by year and built charts using Matplotlib according to the length of each presidential administration. This allowed me to show visualizations that can easily convey any increase or decrease of journalist assassinations by the ruling political party in each period. After that, I built a pie chart showing the distribution of the “Source_fire” variable, which provides a better idea of the reason behind the assassination. This could help to understand if the death was a deliberate targeted attack on the journalists or if it could be regarded as a work-related accident.
</p>

<p style="text-align: justify;">
      The entire script that processed the data and generated the visualizations can be found here: <a href="https://github.com/alanverdugo/journalists_deaths_analysis/blob/master/cpj.py">https://github.com/alanverdugo/journalists_deaths_analysis/blob/master/cpj.py</a>
</p>

<h4 style="text-align: center;">
  <a id="user-content-findings" class="anchor" href="https://github.com/alanverdugo/journalists_deaths_analysis#findings" aria-hidden="true"></a>Findings
</h4>

[<img class="size-full wp-image-2125" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2017/12/Mexico.png" alt="Figure 1: Number of journalists killed in Mexico." width="1594" height="811" />](https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2017/12/Mexico.png)

<p style="text-align: center;">
  <em>Figure 1: Number of journalists killed in Mexico.</em>
</p>

<p style="text-align: justify;">
      In this chart we see the two parties that have been in power in Mexico (in different colors). An increase in journalists’ deaths occurred during the mid 2000s, then appeared to decrease but now seems to be increasing again.
</p>

* * *

<p style="text-align: center;">
  <a href="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2017/12/USA.png"><img class="aligncenter size-full wp-image-2126" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2017/12/USA.png" alt="Figure 2: Number of journalists killed in USA." width="1575" height="814" /></a> <em>Figure 2: Number of journalists killed in USA.</em>
</p>

<p style="text-align: justify;">
      For comparison purposes, this is the same chart, but using US data. It can be seen that the US is much safer for journalists, and that there is no clear correlation between the political party in power and journalists’ deaths.
</p>

* * *

[<img class="aligncenter size-full wp-image-2127" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2017/12/Mexico2.png" alt="Figure 3: Source of fire for journalists deaths in Mexico." width="966" height="702" />](https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2017/12/Mexico2.png)

<p style="text-align: center;">
  <em>Figure 3: Source of fire for journalists deaths in Mexico.</em>
</p>

<p style="text-align: justify;">
      This is a pie chart of the source of the fire that caused the journalists deaths in Mexico. We can clearly see that most of the deaths were caused by criminal groups (very probably drug cartels).
</p>

<h4 style="text-align: center;">
  <a id="user-content-limitations" class="anchor" href="https://github.com/alanverdugo/journalists_deaths_analysis#limitations" aria-hidden="true"></a>Limitations
</h4>

<p style="text-align: justify;">
      The dataset is fairly small. This is one of the rare cases where not having a lot of data is a good thing (after all, even a single assassination is a tragic event). However, the relative low number of deaths makes it hard to safely find patterns or correlations. Due to the mystery and inherent danger behind some of the deaths, it may be probable that many of them are not reported to the authorities and even then, acts of corruption could hinder the reach or veracity of the data. In other words, we may probably be working with incomplete data.
</p>

<h4 style="text-align: center;">
  <a id="user-content-conclusions" class="anchor" href="https://github.com/alanverdugo/journalists_deaths_analysis#conclusions" aria-hidden="true"></a>Conclusions
</h4>

<p style="text-align: justify;">
      Practicing journalism in Mexico has been, and still is, a dangerous activity. Compared against other countries, we can see the relative dangerous situation that journalists located in Mexico experience every day. A change in the mexican political status quo did not solve the problem, in fact, it appeared to have increased it. This could mean that just changing the political party in power is not enough and that serious strategic changes in security, transparency and drug-related politics need to be done in order to ensure the safety of the journalists and of the mexican citizens in general.
</p>

<p style="text-align: justify;">
      The war on drugs military campaign that started in 2006 was one of the main triggers for the increased amount in violence during the late 2000s<sup>[2]</sup>. Drug cartels fought against the military and against each other for the control of the territories. However, that does not mean that journalists did not experience attacks before the war on drugs or that they will not experience them in the future. It is unknown how many bribes or threats the journalists receive from corrupt officials or from criminal organizations, so these findings should not be regarded as definitive.
</p>

<p style="text-align: justify;">
      The geo-political and socio-economic situation of each country is also a complex subject that cannot be fully grasped using such a small set of data. For these reasons, a more complete analysis should be conducted to safely identify the possible correlation between a country ruler and the acts of violence towards the media.
</p>

<h4 style="text-align: center;">
  <a id="user-content-references" class="anchor" href="https://github.com/alanverdugo/journalists_deaths_analysis#references" aria-hidden="true"></a>References
</h4>

  1. List of journalists and media workers killed in Mexico. (2017, November 28). In Wikipedia, The Free Encyclopedia. Retrieved 17:38, December 9, 2017, from <a href="https://en.wikipedia.org/w/index.php?title=List_of_journalists_and_media_workers_killed_in_Mexico&oldid=812565094" target="_blank" rel="noopener">https://en.wikipedia.org/w/index.php?title=List_of_journalists_and_media_workers_killed_in_Mexico&oldid=812565094</a>
  2. Timeline of the Mexican Drug War. (2017, December 4). In Wikipedia, The Free Encyclopedia. Retrieved 04:52, December 9, 2017, from <a href="https://en.wikipedia.org/w/index.php?title=Timeline_of_the_Mexican_Drug_War&oldid=813681343" rel="nofollow">https://en.wikipedia.org/w/index.php?title=Timeline_of_the_Mexican_Drug_War&oldid=813681343</a>
  3. Mexican Drug War. (2017, December 4). In Wikipedia, The Free Encyclopedia. Retrieved 04:52, December 9, 2017, from <a href="https://en.wikipedia.org/w/index.php?title=Mexican_Drug_War&oldid=813724408" rel="nofollow">https://en.wikipedia.org/w/index.php?title=Mexican_Drug_War&oldid=813724408</a>
  4. List of Presidents of the United States. (2017, December 7). In Wikipedia, The Free Encyclopedia. Retrieved 05:09, December 8, 2017, from <a href="https://en.wikipedia.org/w/index.php?title=List_of_Presidents_of_the_United_States&oldid=814280717" rel="nofollow">https://en.wikipedia.org/w/index.php?title=List_of_Presidents_of_the_United_States&oldid=814280717</a>