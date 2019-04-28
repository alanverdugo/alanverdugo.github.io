---
id: 848
title: QPX app with Python, Flask and Bluemix
date: 2017-04-23T17:58:13-05:00
author: Alan Verdugo
layout: post
guid: http://www.kippel.net/blog/?p=848
permalink: /?p=848
categories:
  - Uncategorized
---
Installed django:

&nbsp;

Made sure Django is installed correctly:

python -c &#8220;import django; print(django.get_version())&#8221;

&nbsp;

Downloaded the CloudFoundry binary for Linux 32 bits:

wget http://go-cli.s3-website-us-east-1.amazonaws.com/releases/v6.12.2/cf-linux-386.tgz

&nbsp;

Made sure CloudFoundry is working:

./cf -v  
./cf version 6.12.2-24abed3-2015-07-15T21:24:00+00:00

&nbsp;

Created a PostgreSQL database:

CREATE DATABASE qpx;

&nbsp;

installed psycopg2 (so Python can communicate with PostgreSQL):

&nbsp;

<blockquote class="reddit-card" >
  <p>
    <a href="https://www.reddit.com/r/IAmA/comments/51yiz2/were_professional_cheap_flight_finders_here_for_4/?ref_source=embed&ref=share">We&#8217;re professional cheap flight finders. Here for 4 hours to give free help finding you cheap flights! AUA</a> from <a href="https://www.reddit.com/r/IAmA/">IAmA</a>
  </p>
</blockquote>



<blockquote class="reddit-card" >
  <p>
    <a href="https://www.reddit.com/r/IWantToLearn/comments/4y6rjz/iwtl_how_to_travel_cheap/?ref_source=embed&ref=share">IWTL: How to travel cheap</a> from <a href="https://www.reddit.com/r/IWantToLearn/">IWantToLearn</a>
  </p>
</blockquote>



https://github.com/IBM-Bluemix/bluemix-python-flask-sample

http://camelcamelcamel.com/

https://skiplagged.com/

<pre class="">sudo apt-get install python-psycopg2</pre>

&nbsp;