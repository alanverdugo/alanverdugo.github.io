---
id: 858
title: Running a Flask application in an Apache subdirectory
date: 2015-10-31T17:17:59-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=858
permalink: /?p=858
---
<p style="text-align: justify;">
      I wanted to have a &#8220;main&#8221; Apache-served site with a Flask application running alongside it, but in a subdirectory. I.e. <strong>mysite.com</strong> and <strong>mysite.com/flaskapp</strong>. This was much harder than expected.
</p>

<p style="text-align: justify;">
      Most documentation I found for this issue told me to create a brand new <strong>&#8220;flaskapp.conf&#8221;</strong> file in <strong>/etc/apache2/sites-available/</strong>, this, of course, made the Flask application work, but broke my main site. That was not what I wanted. I wanted full cooperation between Flask and what I was already running.
</p>

<p style="text-align: justify;">
      I obviously have all the prerequisites already installed and/or running (Linux, Python, Apache, Flask, libapache2-mod-wsgi, wsgi, etc.). To give you an idea of my environment, this is my file structure:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false lang:default highlight:0 decode:true ">/var/www/html/
    flaskapp/
        flaskapp.wsgi
        flaskapp/
            __init__.py
            static/
            templates/</pre>

<p style="text-align: justify;">
      Basically, what I had to do was to modify my existing <strong>/etc/apache2/sites-available/000-default.conf</strong> file. I added the following lines in it:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false nums:false lang:default highlight:0 decode:true">WSGIDaemonProcess flaskapp user=www-data group=www-data threads=5 home=/var/www/html/flaskapp
WSGIScriptAlias /flaskapp /var/www/html/flaskapp/flaskapp.wsgi

&lt;Directory /var/www/html/flaskapp/flaskapp&gt;
    WSGIProcessGroup flaskapp
    WSGIApplicationGroup %{GLOBAL}
    WSGIScriptReloading On
    Order deny,allow
    Allow from all
&lt;/Directory&gt;</pre>

<p style="text-align: justify;">
      Note that the .wsgi file <em>must</em> be executable by the user specified in the user parameter in the <strong>WSGIDaemonProcess</strong> line. Pay special attention to the second line (WSGIScriptAlias), most documentation told me to write it like this:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false nums:false lang:default highlight:0 decode:true">WSGIScriptAlias / /var/www/html/flaskapp/flaskapp.wsgi</pre>

<p style="text-align: justify;">
      Doing it like that, would redirect ALL the traffic exclusively to the Flask application, and, again, the main site would stop working. As for my WSGI file (flaskapp.wsgi), these are its contents:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false nums:false lang:python decode:true">#!/usr/bin/python
import sys
sys.path.append('/var/www/html/flaskapp')
from flaskapp import app as application</pre>

After all the modifications were done, I restarted Apache:

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false nums:false lang:default highlight:0 decode:true">service apache2 restart</pre>

<p style="text-align: justify;">
      And finally, everything was working as expected. I am not sure if this is the preferred way to accomplish this, but it is working for me.
</p>

<p style="text-align: justify;">
      <strong>Conclusion:</strong> I expected to accomplish this much more easily, and for Flask to be easier to configure with Apache since the default, standalone-Flask method is not even recommended for production environments. While troubleshooting, I found many people having the same problem (either with Apache, Nginx, or other webservers). I felt a little disappointed that I had to do all these &#8220;hacks&#8221; in order to make a Python web application running in one of the most popular webservers. It seems unrealistic to have the entirety of the webserver assigned exclusively to a Flask application. Let&#8217;s hope that new versions of Flask and Apache/Nginx offer a better compatibility between them.
</p>

<p style="text-align: justify;">
      <strong>References:</strong>
</p>

<a href="https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps" target="_blank">https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps</a>

<a href="http://www.quora.com/How-can-I-deploy-a-Flask-application-to-a-subdirectory-with-Apache-2" target="_blank">http://www.quora.com/How-can-I-deploy-a-Flask-application-to-a-subdirectory-with-Apache-2</a>

<a href="http://stackoverflow.com/questions/14181364/running-a-flask-website-in-a-subdirectory-with-apache" target="_blank">http://stackoverflow.com/questions/14181364/running-a-flask-website-in-a-subdirectory-with-apache</a>