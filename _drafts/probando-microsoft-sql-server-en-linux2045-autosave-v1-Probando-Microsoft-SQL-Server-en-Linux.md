---
id: 2047
title: Probando Microsoft SQL Server en Linux
date: 2017-08-18T13:26:11-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=2047
permalink: /?p=2047
---
<p style="text-align: justify;">
      Hace años, nunca hubiera pensado escribir un título como ese, pero las cosas cambian y Microsoft ahora está prestando atención a otros ambientes que no son los suyos. Esto nos ha dado la oportunidad de probar algunas de sus herramientas sin tener que vernos obligados a instalar Windows, lo cual se agradece mucho.
</p>

<p style="text-align: justify;">
      Voy a instalar SQL Server en Linux (específicamente en Linux Mint). Aquí voy a detallar el proceso de instsalación a modo de tutorial y también voy a ejecutar algunas consultas sencillas para demostrar el uso de SQL Server.
</p>

<p style="text-align: justify;">
      Durante el proceso de instalación, necesitaremos permisos de administrador, así que nos cambiaremos a nuestra cuenta root:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:default decode:true">sudo su - root</pre>

<p style="text-align: justify;">
      Creamos un directorio destinado para herramientas y notas sobre SQL Server y nos cambiamos a él (este paso es totalmente opcional):
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:default decode:true">mkdir sql_server
cd sql_server/</pre>

<p style="text-align: justify;">
      Bajamos e instalamos las llaves de los repositorios de Microsoft:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false wrap:true lang:default decode:true">sql_server # curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
% Total % Received % Xferd Average Speed   Time     Time     Time     Current
                           Dload   Upload  Total    Spent    Left     Speed
100 983 100 983    0  0    2420    0       --:--:-- --:--:-- --:--:-- 2427
OK</pre>

<p style="text-align: justify;">
      Añadimos el repositorio de Microsoft:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false wrap:true lang:default decode:true">sql_server # sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list)"
% Total % Received % Xferd Average Speed   Time     Time     Time     Current
                           Dload   Upload  Total    Spent    Left     Speed
100 87 100 87      0  0    179     0       --:--:-- --:--:-- --:--:-- 179
OK</pre>

<p style="text-align: justify;">
      Actualizamos nuestra lista de repositorios:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false wrap:true lang:default decode:true ">sql_server # sudo apt-get update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu xenial InRelease
Hit:3 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102kB]
Get:5 https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial InRelease [2 828 B]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102kB]
Ign:7 http://packages.linuxmint.com serena InRelease
Hit:8 http://packages.linuxmint.com serena Release
Get:10 https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial/main amd64 Packages [5 687 B]
Get:11 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102kB]
Fetched 315 kB in 1s (233 kB/s)
Reading package lists... Done</pre>

<p style="text-align: justify;">
      Finalmente, instalamos SQL Server:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false wrap:true lang:default decode:true">sql_server # sudo apt-get install -y mssql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
libc++1 libcurl3 libjemalloc1 libsss-nss-idmap0

Suggested packages:
clang
The following NEW packages will be installed:
libc++1 libcurl3 libjemalloc1 libsss-nss-idmap0 mssql-server
0 upgraded, 5 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 172 MB of archives.
After this operation, 907 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64
libcurl3 amd64 7.47.0-1ubuntu2.2 [186 kB]
Get:2 https://packages.microsoft.com/ubuntu/16.04/mssql-server
xenial/main amd64 mssql-server amd64 14.0.800.90-2 [172 MB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/universe amd64 libc++1
amd64 3.7.0-1 [226 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial/universe amd64
libjemalloc1 amd64 3.6.0-9ubuntu1 [78.9 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64
libsss-nss-idmap0 amd64 1.13.4-1ubuntu1.6 [11.8 kB]
Fetched 172 MB in 3min 24s (842 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libcurl3:amd64.
(Reading database ... 354049 files and directories currently
installed.)
Preparing to unpack .../libcurl3_7.47.0-1ubuntu2.2_amd64.deb ...
Unpacking libcurl3:amd64 (7.47.0-1ubuntu2.2) ...
Selecting previously unselected package libc++1:amd64.
Preparing to unpack .../libc++1_3.7.0-1_amd64.deb ...
Unpacking libc++1:amd64 (3.7.0-1) ...
Selecting previously unselected package libjemalloc1.
Preparing to unpack .../libjemalloc1_3.6.0-9ubuntu1_amd64.deb ...
Unpacking libjemalloc1 (3.6.0-9ubuntu1) ...
Selecting previously unselected package libsss-nss-idmap0.
Preparing to unpack
.../libsss-nss-idmap0_1.13.4-1ubuntu1.6_amd64.deb ...
Unpacking libsss-nss-idmap0 (1.13.4-1ubuntu1.6) ...
Selecting previously unselected package mssql-server.
Preparing to unpack .../mssql-server_14.0.800.90-2_amd64.deb ...
Unpacking mssql-server (14.0.800.90-2) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up mysql-apt-config (0.8.7-1) ...
OK
Setting up libcurl3:amd64 (7.47.0-1ubuntu2.2) ...
Setting up libc++1:amd64 (3.7.0-1) ...
Setting up libjemalloc1 (3.6.0-9ubuntu1) ...
Setting up libsss-nss-idmap0 (1.13.4-1ubuntu1.6) ...
Setting up mssql-server (14.0.800.90-2) ...
+--------------------------------------------------------------+
Please run 'sudo /opt/mssql/bin/mssql-conf setup'
to complete the setup of Microsoft SQL Server
+--------------------------------------------------------------+
Processing triggers for libc-bin (2.23-0ubuntu9) ...
</pre>

<p style="text-align: justify;">
      Ejecutamos la herramienta de configuración:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:default decode:true">sql_server # sudo /opt/mssql/bin/mssql-conf setup
The license terms for this product can be downloaded from
http://go.microsoft.com/fwlink/?LinkId=746388
and found in /usr/share/doc/mssql-server/LICENSE.TXT.
Do you accept the license terms? [Yes/No]:yes
Choose an edition of SQL Server:
1) Evaluation (free, no production use rights, 180-day limit)
2) Developer (free, no production use rights)
3) Express (free)
4) Web (PAID)
5) Standard (PAID)
6) Enterprise (PAID)
7) I bought a license through a retail sales channel and have a
product key to enter.

Details about editions can be found at
https://www.microsoft.com/en-us/sql-server/sql-server-2016-editions
Use of PAID editions of this software requires separate licensing
through a
Microsoft Volume Licensing program.
By choosing a PAID edition, you are verifying that you have the
appropriate
number of licenses in place to install and run this software.
Enter your edition(1-7): 1
Enter the SQL Server system administrator password:
Confirm the SQL Server system administrator password:
Configuring SQL Server...
This is an evaluation version.
There are [171] days left in the
evaluation period.
The licensing PID was successfully processed. The new edition is
[Enterprise Evaluation Edition].
Created symlink from
/etc/systemd/system/multi-user.target.wants/mssql-server.service to
/lib/systemd/system/mssql-server.service.
Setup has completed successfully. SQL Server is now starting.
</pre>

<p style="text-align: justify;">
      Verificamos que el servicio de SQL Server está ejecutándose correctamente:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:default decode:true">sql_server # systemctl status mssql-server
mssql-server.service - Microsoft SQL Server Database Engine
Loaded: loaded (/lib/systemd/system/mssql-server.service; enabled;
vendor preset: enabled)
Active: active (running) since Sat 2017-07-22 21:07:10 CDT; 1min 33s ago
Docs: https://docs.microsoft.com/en-us/sql/linux
Main PID: 5318 (sqlservr)
Tasks: 142

Memory: 680.9M
CPU: 7.379s
CGroup: /system.slice/mssql-server.service
├─5318 /opt/mssql/bin/sqlservr
└─5344 /opt/mssql/bin/sqlservr
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [78B blob data]
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [84B blob data]
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [122B blob data]
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [145B blob data]
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [66B blob data]
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [75B blob data]
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [96B blob data]
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [100B blob data]
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [71B blob data]
Jul 22 21:07:14 ono-sendai sqlservr[5318]: [124B blob data]


sql_server # ps -ef | grep mssql
mssql 5318 1 0 21:07 ? 00:00:00 /opt/mssql/bin/sqlservr
mssql 5344 5318 5 21:07 ? 00:00:08 /opt/mssql/bin/sqlservr</pre>

<p style="text-align: justify;">
      Ahora instalaremos las herramientas para la línea de comandos:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:default decode:true">sql_server # curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
% Total % Received % Xferd Average Speed   Time     Time     Time     Current
                           Dload   Upload  Total    Spent    Left     Speed
100 983 100 983    0  0    1103    0       --:--:-- --:--:-- --:--:-- 1104
OK</pre>

<p style="text-align: justify;">
      Nos conectamos a nuestra instancia local:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:default decode:true">sql_server # sqlcmd -S localhost -U SA
Password:
1&gt;
</pre>

<p style="text-align: justify;">
      Creamos una base de datos de prueba y mostramos las bases de datos existentes:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:default decode:true">1&gt; create database testdb
2&gt; SELECT Name from sys.Databases
3&gt; go
Name
-----------------------------------------------------------------------
master
tempdb
model
msdb
testdb
(5 rows affected)</pre>

<p style="text-align: justify;">
      En nuestra nueva base de datos, creamos una tabla de prueba e insertamos un registro:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false wrap:true lang:default decode:true">1&gt; use testdb
2&gt; CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
3&gt; INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
4&gt; go
Changed database context to 'testdb'.
(1 rows affected)</pre>

<p style="text-align: justify;">
      Hacemos una consulta de prueba:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:default decode:true">1&gt; SELECT * FROM Inventory WHERE quantity &gt; 152;
2&gt; go
id          name                                               quantity
----------- -------------------------------------------------- -----------
2           orange                                             154
(1 rows affected)</pre>

<p style="text-align: justify;">
     Como se puede ver, SQL Server fue inesperadamente sencillo de instalar, configurar y utilizar, sobre todo teniendo en mente que utilizamos un sistema operativo que no es del propio Microsoft. En esta práctica aprendimos a crear tablas y hacer consultas con las herramientas de SQL Server, las cuales son muy parecidas a otras herramientas de otros RDBMS, como MySQL.
</p>