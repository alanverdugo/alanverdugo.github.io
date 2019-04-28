---
id: 2316
title: wizeline devops challenge
date: 2018-06-29T14:33:43-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=2316
permalink: /?p=2316
---
devops.wizeline.academy  
which only prints a JSON object:  
{&#8220;instructions&#8221;: &#8220;To start, go to /guide, use SSL!!&#8221;}

https://devops.wizeline.academy/guide  
{&#8220;instructions&#8221;: &#8220;Send method defined in rfc2616 section 9.5&#8221;}

Reading RFC 2616, the method in section 9.5 is POST

import requests  
r = requests.post(&#8216;https://devops.wizeline.academy/guide&#8217;, json={&#8220;key&#8221;: &#8220;value&#8221;})  
r.json()

{u&#8217;instructions&#8217;: u&#8217;UE9TVCB0byAvbWFpbCBhZGRpbmcgeW91ciBlbWFpbCB3aXRoaW4gYSBoZWFkZXIgY2FsbGVkICdFbWFpbCc=&#8217;}

UE9TVCB0byAvbWFpbCBhZGRpbmcgeW91ciBlbWFpbCB3aXRoaW4gYSBoZWFkZXIgY2FsbGVkICdFbWFpbCc=

After some reading, I figured that it was a string encoded in Base 64. So I went to https://www.base64decode.org/  
and the decoded message turned out to be

&#8220;POST to /mail adding your email within a header called &#8216;Email'&#8221;

r = requests.post(&#8216;https://devops.wizeline.academy/mail&#8217;, json={&#8220;Email&#8221;: &#8220;verdugoalan@hotmail.com&#8221;}, headers={&#8220;Email&#8221;: &#8220;verdugoalan@hotmail.com&#8221;})

r.json()

{u&#8217;status&#8217;: u&#8217;Success&#8217;, u&#8217;instructions&#8217;: u&#8217;VGhlIFdpemVsaW5lIEJlYXJlciBpcyBpbiB0aGUgUmVzcG9uc2UgSGVhZGVyLCB5b3Ugd2lsbCBhbHdheXMgbmVlZCBpdC4gTm93IFBPU1QgdG8gL2NoYWxsZW5nZSBmb3IgaW5zdHJ1Y3Rpb25zLCB1c2UgeW91ciBCZWFyZXIgYW5kIEVtYWlsIGluIHlvdXIgaGVhZGVycyBmb3IgYWxsIGNhbGxz&#8217;}

Again, this was decoded with Base 64, which gave us:

&#8220;The Wizeline Bearer is in the Response Header, you will always need it. Now POST to /challenge for instructions, use your Bearer and Email in your headers for all calls&#8221;

r.headers  
{&#8216;Content-Length&#8217;: &#8216;265&#8217;, &#8216;WizelineBearer&#8217;: &#8216;dmVyZHVnb2FsYW5AaG90bWFpbC5jb206MTQ5NTIzMTExNjUyLjQ5OTY2&#8217;, &#8216;Server&#8217;: &#8216;nginx/1.9.11&#8217;, &#8216;Connection&#8217;: &#8216;keep-alive&#8217;, &#8216;Date&#8217;: &#8216;Fri, 19 May 2017 21:58:36 GMT&#8217;, &#8216;Content-Type&#8217;: &#8216;application/json&#8217;}

r = requests.post(&#8216;https://devops.wizeline.academy/challenge&#8217;, json={&#8220;Email&#8221;: &#8220;verdugoalan@hotmail.com&#8221;}, headers={&#8220;Email&#8221;: &#8220;verdugoalan@hotmail.com&#8221;, &#8220;WizelineBearer&#8221;: &#8220;dmVyZHVnb2FsYW5AaG90bWFpbC5jb206MTQ5NTIzMTExNjUyLjQ5OTY2&#8221;})

r.json()  
{u&#8217;status&#8217;: u&#8217;awesome&#8217;, u&#8217;instructions&#8217;: u&#8217;V293ISEuIFlvdXIgbmV4dCBlbmRwb2ludCBpcyAvd2hlbiB3aXRoIE9QVElPTlMsIHlvdSBuZWVkIGEgcGF5bG9hZCB3aXRoICJ3aGVuIiBhbmQgdGhlIGVwb2NoIHRpbWVzdGFtcCBvZiB0aGUgY291cnNl&#8217;}

Yet again, the message was decoded in Base 64:  
&#8220;Wow!!. Your next endpoint is /when with OPTIONS, you need a payload with &#8220;when&#8221; and the epoch timestamp of the course&#8221;

r = requests.options(&#8216;https://devops.wizeline.academy/when&#8217;, json={&#8220;when&#8221;: &#8220;1497709800&#8221;}, headers={&#8220;Email&#8221;: &#8220;verdugoalan@hotmail.com&#8221;, &#8220;WizelineBearer&#8221;: &#8220;dmVyZHVnb2FsYW5AaG90bWFpbC5jb206MTQ5NTIzMTExNjUyLjQ5OTY2&#8243;})

r.json()  
{u&#8217;status&#8217;: u&#8221;Excellent, you&#8217;re almost there&#8221;, u&#8217;instructions&#8217;: u&#8217;U2VuZCBHRVQgdG8gL3dob2lzIHdpdGggdGhlIG5hbWUgb2Ygb3VyIHNwZWFrZXIgdXNpbmcgJ25hbWUnIGluIHRoZSBxdWVyeSBzdHJpbmc=&#8217;}

Which translates to  
&#8220;Send GET to /whois with the name of our speaker using &#8216;name&#8217; in the query string&#8221;

r = requests.get(&#8216;https://devops.wizeline.academy/whois&#8217;, params={&#8220;name&#8221;:&#8221;Kennon Kwok&#8221;}, headers={&#8220;Email&#8221;: &#8220;verdugoalan@hotmail.com&#8221;, &#8220;WizelineBearer&#8221;: &#8220;dmVyZHVnb2FsYW5AaG90bWFpbC5jb206MTQ5NTIzMTExNjUyLjQ5OTY2&#8221;})

which responds:  
r.json()  
{u&#8217;status&#8217;: u&#8217;Great&#8217;, u&#8217;instructions&#8217;: u&#8217;Tm93IFBVVCB0aGUgc3BvbnNvciBvZiB0aGlzIGV2ZW50IHRvIC9zcG9uc29yLCB0aGUgcGF5bG9hZCBuZWVkcyB0aGUga2V5ICJzcG9uc29yIiwgY2VydGFpbmx5IHdlIGVuam95IHJlYWRpbmcgbWQ1IGluIGxvd2VyIGNhc2UgdGV4dA==&#8217;}

Which translates to: &#8220;Now PUT the sponsor of this event to /sponsor, the payload needs the key &#8220;sponsor&#8221;, certainly we enjoy reading md5 in lower case text&#8221;

MD5 hash for wizeline is : d1f5dd09a0deb735e99f9df529d33f8b

r = requests.put(&#8216;https://devops.wizeline.academy/sponsor&#8217;, json={&#8220;sponsor&#8221;:&#8221;d1f5dd09a0deb735e99f9df529d33f8b&#8221;}, headers={&#8220;Email&#8221;: &#8220;verdugoalan@hotmail.com&#8221;, &#8220;WizelineBearer&#8221;: &#8220;dmVyZHVnb2FsYW5AaG90bWFpbC5jb206MTQ5NTIzMTExNjUyLjQ5OTY2&#8243;})

Response:  
{u&#8217;status&#8217;: u&#8217;cool&#8217;, u&#8217;instructions&#8217;: u&#8217;Tm93LCBkb3dubG9hZCBhIGZ1bm55IEdJRiBpbWFnZSBsb2NhdGVkIGluIC9jcnlwdG8vZGV2b3BzLmdpZiwgYnR3IHdlIGxvdmUgc3RlZ2Fub2dyYXBoeSBhbmQgY29tcHJlc3NlZCBmaWxlcw==&#8217;}

Which translates to:  
Now, download a funny GIF image located in /crypto/devops.gif, btw we love steganography and compressed files

wget -d &#8211;header=&#8221;Email: verdugoalan@hotmail.com&#8221; &#8211;header=&#8221;WizelineBearer: dmVyZHVnb2FsYW5AaG90bWFpbC5jb206MTQ5NTIzMTExNjUyLjQ5OTY2&#8243; https://devops.wizeline.academy/crypto/devops.gif

As the hint mentioned, this .gif file was actually a zip file. I copied the file and changed the extention to zip. Inside the zip file there was a text file named secret.txt, this file contained the text &#8220;WWF5ISEuIFlvdXIgbmV4dCBlbmRwb2ludCBpcyBHRVQgL2ZpbmFsLzx5b3VyLWJlYXJlci10b2tlbj4K&#8221;

Which translates to &#8220;Yay!!. Your next endpoint is GET /final/<your-bearer-token>&#8221;

r = requests.get(&#8216;https://devops.wizeline.academy/final/dmVyZHVnb2FsYW5AaG90bWFpbC5jb206MTQ5NTIzMTExNjUyLjQ5OTY2&#8242;, headers={&#8220;Email&#8221;: &#8220;verdugoalan@hotmail.com&#8221;, &#8220;WizelineBearer&#8221;: &#8220;dmVyZHVnb2FsYW5AaG90bWFpbC5jb206MTQ5NTIzMTExNjUyLjQ5OTY2&#8221;})

Which only responded with:  
r.json()  
{u&#8217;status&#8217;: u&#8217;Congratulations&#8217;}