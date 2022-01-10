---
id: 487
title: How to grant read and write permissions in DB2
date: 2014-04-23T12:14:25-05:00
author: Alan Verdugo
guid: http://www.kippel.net/blog/?p=487
permalink: /blog/db2-permissions
#permalink: /?p=487
categories:
  - Uncategorized
tags:
  - english
  - IT
  - Technical writing
---
<p style="text-align: justify;">
      In older versions of DB2, the ever useful command &#8220;<strong>grant dataaccess</strong>&#8221; was not implemented yet. So, in order to grant permissions over a whole database, it is needed to grant the permissions manually, object by object. There are ways to do this relatively fast. The following example details how to easily grant permissions to a user or to a group in a database which runs in DB2 version 9.5.0.5:
</p>

<p style="text-align: justify;">
      First, connect to the desired DB as the instance owner. For example, we will connect to the database named &#8220;<strong>MYSAMPLEDB</strong>&#8221; as its instance owner, named &#8220;<strong>instanceowner</strong>&#8220;:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono nums:false wrap:true lang:sh decode:true">su - instanceowner
db2 connect to MYSAMPLEDB
</pre>

<p style="text-align: justify;">
      Then, grant connect permission on the current database (in this case <strong>MYSAMPLEDB</strong>) to the desired user with the &#8220;<strong>grant connect</strong>&#8221; command. In this example we will grant connect permissions to the user named &#8220;<strong>user1</strong>&#8220;:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono nums:false wrap:true lang:sh decode:true">db2 grant connect on database to user user1</pre>

<p style="text-align: justify;">
      Next, we will grant writing permissions to &#8220;<strong>user1</strong>&#8221; in all the tabschemas except SYSTEM:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono nums:false wrap:true lang:sh decode:true">db2 "select 'GRANT SELECT,INSERT,UPDATE,DELETE ON TABLE ' || rtrim(tabschema)||'.'|| rtrim(TABNAME) || '  TO USER user1;' from syscat.tables where tabschema not like '%SYS%' " &gt; /tmp/grants.ddl</pre>

<p style="text-align: justify;">
      Instead of only one user, with the following command, permissions are granted to a group of users named &#8220;<strong>db2group</strong>&#8221; in all the schemas except SYSTEM:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono nums:false wrap:true lang:sh decode:true">db2 "select 'GRANT SELECT ON TABLE ' || rtrim(tabschema)||'.'|| rtrim(TABNAME) || '  TO GROUP db2group;' from syscat.tables where tabschema not like '%SYS%' " &gt; /tmp/grants.ddl</pre>

<p style="text-align: justify;">
      In any of those cases, the file <strong>/tmp/grants.ddl</strong> will contain a long list of commands that will need to be executed in order to actually provide the permissions. Checking the newly created file is recommended in order to see if any errors occurred. If everything is fine, we can proceed to the next step.
</p>

<p style="text-align: justify;">
      As said before, it is needed to execute the list of commands that were inserted into the <strong>/tmp/grants.ddl</strong> file. In out example, this is done like this:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono nums:false wrap:true lang:sh decode:true">db2 -tvf /tmp/grants.ddl &gt; /tmp/grants_output.txt</pre>

The **/tmp/grants_output.txt** file will contain any errors that may have occurred. This is easier, right?