---
id: 920
title: Reporting REST data with DataTables and Bootstrap
date: 2015-09-28T16:47:07-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=920
permalink: /?p=920
---
<p style="text-align: justify;">
      Recently, I was requested to make a webpage to report data consumed via JSON to do a demonstration of RESTful architectures. I am not really a web developer so the challenge was interesting, yet easy enough so it wouldn&#8217;t take too much time.
</p>

<p style="text-align: justify;">
      Ultimately, I made a very simple table-based report with a jQuery plugin named <a href="http://www.datatables.net/" target="_blank">dataTables</a>. This plugin has very weird behaviours, but a nice look and feel. It also offers integration with <a href="http://getbootstrap.com/" target="_blank">Bootstrap</a>, and together they provide some interesting results. As you can see in the demo, the plugin allows to order by columns and do quick searches, which is nice.
</p>

<p style="text-align: justify;">
      Of course, I wanted the report to be updated every time the JSON source changed. In other words, the code should be future-proof enough that it could handle when records are added, edited or deleted from the JSON file. This may seem very obvious, but when I was doing research about how to do it, I found weird suggestions, like parsing the REST data in the backend and then basically hardcoding it in the HTML. <a href="http://kippel.net/rest_demo/locations.html" target="_blank">This is the result.</a>
</p>

<p style="text-align: justify;">
      This is the code:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false striped:false wrap:true lang:xhtml decode:true " title="HTML/JS code">&lt;!doctype html&gt;
&lt;html lang="en"&gt;
	&lt;head&gt;
		&lt;meta charset="utf-8"&gt;
		&lt;title&gt;Locations&lt;/title&gt;
		&lt;style&gt;
			img {
				height: 100px;
				float: left;
			}
		&lt;/style&gt;

		&lt;script type="text/javascript" language="javascript" src="http://code.jquery.com/jquery-1.11.3.min.js"&gt;&lt;/script&gt;
		&lt;script type="text/javascript" language="javascript" src="http://cdn.datatables.net/1.10.9/js/jquery.dataTables.min.js"&gt;&lt;/script&gt;
		&lt;script type="text/javascript" language="javascript" src="http://cdn.datatables.net/1.10.9/js/dataTables.bootstrap.min.js"&gt;&lt;/script&gt;
		&lt;script type="text/javascript" language="javascript" class="init"&gt;
         var dataSet = []; 
			$(document).ready(function() {
          	var restAPI = "http://kippel.net/rest_demo/locations.json";	
          
          $.getJSON( restAPI )
				.done(function( data ) {
             $.each( data.results, function( i, result ) {
                var newArray = [];
                newArray.push(result.city_id);
                newArray.push(result.id);
                newArray.push(result.name);
                dataSet.push(newArray);
             });
            $('#resultsTable').DataTable( {
              "data": dataSet
            });
          });
       } );
       &lt;/script&gt;
	&lt;/head&gt;
	&lt;body&gt;
		&lt;div class="container" style="margin-top: 10px"&gt;
			&lt;table id="resultsTable" class="display table table-bordered" cellspacing="0" width="100%"&gt;
				&lt;thead&gt;
					&lt;tr&gt;
						&lt;th&gt;City ID&lt;/th&gt;
						&lt;th&gt;Location ID&lt;/th&gt;
						&lt;th&gt;Location name&lt;/th&gt;
					&lt;/tr&gt;
				&lt;/thead&gt;
        		&lt;tbody&gt;
        		&lt;/tbody&gt;
				&lt;tfoot&gt;
					&lt;tr&gt;
						&lt;th&gt;City ID&lt;/th&gt;
					    &lt;th&gt;Location ID&lt;/th&gt;
						&lt;th&gt;Location name&lt;/th&gt;
					&lt;/tr&gt;
				&lt;/tfoot&gt;
			&lt;/table&gt;
		&lt;/div&gt;
		&lt;link href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css" rel="stylesheet"&gt;
		&lt;link href="http://cdn.datatables.net/1.10.9/css/dataTables.bootstrap.min.css" rel="stylesheet"&gt;
	&lt;/body&gt;
&lt;/html&gt;</pre>

This is some data from the JSON data source, just so you can see the format:

<pre class="theme:tomorrow-night font:ubuntu-mono font-size-enable:false striped:false lang:default decode:true" title="JSON data">{
  "results": [
    {
      "city_id": 9, 
      "id": 1, 
      "name": "BAR 1 DC"
    }, 
    {
      "city_id": 6, 
      "id": 25, 
      "name": "25 1 C2"
    }, 
    {
      "city_id": 6, 
      "id": 26, 
      "name": "25 1 D3"
    }, 
    {
      "city_id": 25, 
      "id": 54, 
      "name": "Ozone 3 1 GBS Server Room 145"
    }, 
    {
      "city_id": 39, 
      "id": 76, 
      "name": "XinYi Building 1F Server Room"
    }
  ]
}</pre>

This was an interesting little project, it was obviously not made by a professional web developer, so if you have any suggestions, please go ahead and leave a comment.

<p style="text-align: justify;">