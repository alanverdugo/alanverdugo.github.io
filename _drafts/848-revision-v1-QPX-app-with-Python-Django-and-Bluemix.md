---
id: 849
title: QPX app with Python, Django and Bluemix
date: 2015-08-10T16:55:12-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=849
permalink: /?p=849
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

<pre class="">sudo apt-get install python-psycopg2</pre>