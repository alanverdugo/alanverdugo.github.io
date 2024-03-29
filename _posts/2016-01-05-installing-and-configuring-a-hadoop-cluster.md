---
id: 1079
title: Installing and configuring a Hadoop cluster
date: 2016-01-05T18:46:48-05:00
author: Alan Verdugo
guid: http://www.kippel.net/blog/?p=1079
permalink: /blog/hadoop-cluster
#permalink: /?p=1079
categories:
  - Uncategorized
tags:
  - english
  - IT
  - Technical writing
---
<p style="text-align: justify;">
      As I mentioned in <a href="http://www.kippel.net/blog/?p=1004" target="_blank">a previous post</a>, Hadoop has great potential and is one of the best known projects for Big Data. Now, let&#8217;s take a deeper look into Hadoop and how it works. So, let&#8217;s roll up our sleeves and actually work with Hadoop. For that, we will install and configure a Hadoop cluster. Our cluster will consists on four nodes (one master and three slaves). So I provisioned four cloud servers:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false nums-toggle:false wrap:true lang:default highlight:0 decode:true">atlbz153122.cloud.example.com (IP Address: 9.9.153.122) (alias: master)
atlbz153120.cloud.example.com (IP Address: 9.9.153.120) (alias: slave-1)
atlbz153078.cloud.example.com (IP Address: 9.9.153.78)  (alias: slave-2)
atlbz153064.cloud.example.com (IP Address: 9.9.153.64)  (alias: slave-3)</pre><figure id="attachment_1081" aria-describedby="caption-attachment-1081" style="width: 712px" class="wp-caption aligncenter">

<img class="size-full wp-image-1081" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/HadoopDiagram.png" alt="Architecture diagram." width="712" height="590" /> <figcaption id="caption-attachment-1081" class="wp-caption-text">Architecture diagram.</figcaption></figure> 

<p style="text-align: justify;">
      We designated <strong>atlbz153122</strong> as the master for no reason in particular. The aliases can be modified according to your needs. I.e. If you are using these same hosts for other cluster projects, you may want to specify the aliases as &#8220;hadoop-master&#8221; or &#8220;hadoop-slave-1&#8221;. They were created using the same image, so all of them have this setup:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false wrap:true lang:default highlight:0 decode:true">Number of CPU(s): 2
Number of tenths of physical CPUs: 2
Amount of Memory: 6144 MB
OS: Red Hat Enterprise Linux Server release 6.7 (Santiago)
Java version: 1.6.0 Java(TM) SE Runtime Environment (build pxa6460sr9-20101125_01(SR9))</pre>

<p style="text-align: justify;">
  <strong>Initial setup</strong>:<br /> In every node, we will do the following:<br /> -Create a hadoop user account (Of course, you can chose to name it differently), and add it to the sudoers group.
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false wrap:true lang:sh decode:true">useradd hadoop; passwd hadoop</pre>

<p style="text-align: justify;">
  -Optionally (but extremely recommended), map all the hostnames in the respective /etc/hosts files.<br /> -Copy SSH keys between all the nodes.<br /> Obviously, first we need to make sure SSH is up and running on all the servers. This step could be different for you according to your security requirements, but the goal here is to allow Hadoop and its processes to communicate between the nodes without prompting for credentials.<br /> -Generate SSH keys.
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh decode:true">ssh-keygen -t rsa</pre>

-Copy the keys.  
What I do is to create a list of all the public keys and then add that master list to the authorized keys in all the hosts.  
-Now check that you can ssh to the localhost and all the other nodes without a passphrase:

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh highlight:0 decode:true">ssh localhost
ssh hadoop@master
ssh hadoop@slave-1
ssh hadoop@slave-2
ssh hadoop@slave-3</pre>

-Create a basic file structure and set the ownership to the Hadoop user you created before.

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh decode:true">mkdir /opt/hadoop/
sudo chown -R hadoop:hadoop /opt/hadoop/</pre>

<p style="text-align: justify;">
  -Setup Java.<br /> As mentioned above, in this image Java is pre-installed. The Java version that comes pre-installed in this RHEL image should work for us since the <a href="http://wiki.apache.org/hadoop/HadoopJavaVersions" target="_blank">Hadoop Java versions page</a> says it has been tested with IBM Java 6 SR 8. Just make sure that your Java version is compatible.<br /> -Add the following to the root and Hadoop user <strong>~/.bashrc</strong> file (and modify according to your needs):
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false nums:false wrap:true lang:sh decode:true"># -- HADOOP ENVIRONMENT VARIABLES START -- #
export HADOOP_HOME=/opt/hadoop/hadoop
export PATH=$PATH:$HADOOP_HOME/bin
export PATH=$PATH:$HADOOP_HOME/sbin
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib"
# -- HADOOP ENVIRONMENT VARIABLES END -- #</pre>

<p style="text-align: justify;">
  From now on, in order to save time, we will install and do a basic setup of Hadoop in the master node, then copy that basic setup to the slaves and then perform specific customizations in each of them.
</p>

<p style="text-align: justify;">
  From the master node, download the latest Hadoop tarball (version 2.6.2 at the time of this writing) from one of the mirrors and extract its contents in the previously created Hadoop home:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:sh decode:true ">cd /opt/hadoop/
wget http://apache.mirrors.tds.net/hadoop/common/hadoop-2.6.2/hadoop-2.6.2.tar.gz
tar xvf hadoop-2.6.2.tar.gz</pre>

<p style="text-align: justify;">
  Update <strong>core-site.xml</strong> (located in <strong>$HADOOP_HOME/hadoop/etc/hadoop/core-site.xml</strong>), we will change &#8220;localhost&#8221; to our master node hostname, IP, or alias. In our case, it would be like this:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:xhtml decode:true">&lt;configuration&gt;
    &lt;property&gt;
        &lt;name&gt;fs.default.name&lt;/name&gt;
        &lt;value&gt;hdfs://master:9000/&lt;/value&gt;
    &lt;/property&gt;
    &lt;property&gt;
        &lt;name&gt;fs.default.FS&lt;/name&gt;
        &lt;value&gt;hdfs://master:9000/&lt;/value&gt;
    &lt;/property&gt;
&lt;/configuration&gt;</pre>

<p style="text-align: justify;">
  Update <strong>hdfs-site.xml</strong> (located in <strong>$HADOOP_HOME/hadoop/etc/hadoop/hdfs-site.xml</strong>), we will change the replication factor to 3, and specify the datanode and namenodes directories (take note of these, since we will create them later), as well as add an http address:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:xhtml decode:true">&lt;property&gt;
    &lt;name&gt;dfs.datanode.data.dir&lt;/name&gt;
    &lt;value&gt;/opt/hadoop_tmp/hdfs/datanode&lt;/value&gt;
    &lt;final&gt;true&lt;/final&gt;
&lt;/property&gt;
&lt;property&gt;
    &lt;name&gt;dfs.namenode.name.dir&lt;/name&gt;
    &lt;value&gt;/opt/hadoop_tmp/hdfs/namenode&lt;/value&gt;
    &lt;final&gt;true&lt;/final&gt;
&lt;/property&gt;
&lt;property&gt;
    &lt;name&gt;dfs.namenode.http-address&lt;/name&gt;
    &lt;value&gt;master:50070&lt;/value&gt;
&lt;/property&gt;
&lt;property&gt;
    &lt;name&gt;dfs.replication&lt;/name&gt;
    &lt;value&gt;3&lt;/value&gt;
&lt;/property&gt;</pre>

<p style="text-align: justify;">
  Update <strong>yarn-site.xml</strong> (located in <strong>$HADOOP_HOME/hadoop/etc/hadoop/yarn-site.xml</strong>). There will be 3 properties that we need to update with our master node hostname or alias:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:xhtml decode:true">&lt;property&gt;
    &lt;name&gt;yarn.resourcemanager.resource-tracker.address&lt;/name&gt;
    &lt;value&gt;master:8025&lt;/value&gt;
&lt;/property&gt;
&lt;property&gt;
    &lt;name&gt;yarn.resourcemanager.scheduler.address&lt;/name&gt;
    &lt;value&gt;master:8035&lt;/value&gt;
&lt;/property&gt;
&lt;property&gt;
    &lt;name&gt;yarn.resourcemanager.address&lt;/name&gt;
    &lt;value&gt;master:8050&lt;/value&gt;
&lt;/property&gt;</pre>

Update **mapred-site.xml** (located in **$HADOOP_HOME/hadoop/etc/hadoop/mapred-site.xml**), we will add the following properties:

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:xhtml decode:true">&lt;property&gt;
    &lt;name&gt;mapreduce.job.tracker&lt;/name&gt;
    &lt;value&gt;master:5431&lt;/value&gt;
&lt;/property&gt;
&lt;property&gt;
    &lt;name&gt;mapred.framework.name&lt;/name&gt;
    &lt;value&gt;yarn&lt;/value&gt;
&lt;/property&gt;</pre>

<p style="text-align: justify;">
  Update the <strong>masters</strong> file (located in <strong>$HADOOP_HOME/hadoop/etc/masters</strong>). We only need to add the hostname or alias of the master node. So in our case this file will only contain one line:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false nums:false wrap:true lang:default highlight:0 decode:true">master</pre>

<p style="text-align: justify;">
  Update the <strong>slaves</strong> file (located in <strong>$HADOOP_HOME/hadoop/etc/slaves</strong>). I am sure you already know what to do here, we will only add our slaves nodes to the file, one alias per line. In our case:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:default highlight:0 decode:true">slave-1
slave-2
slave-3</pre>

<p style="text-align: justify;">
  This concludes the basic setup, we will now transfer all the files to the slave nodes and continue the customizations there.
</p>

<p style="text-align: justify;">
  On the master node, run the following commands in order to copy the basic setup to the slaves (you can also do this with <strong>scp</strong>):
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh decode:true">rsync -avxP &lt;$HADOOP_HOME&gt; &lt;hadoop_user&gt;@&lt;slave-hostname&gt;:&lt;$HADOOP_HOME&gt;</pre>

In our case, it would be something like this:

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false nums:false wrap:true lang:sh highlight:0 decode:true">rsync -avxP /opt/hadoop/ hadoop@slave-1:/opt/hadoop/
rsync -avxP /opt/hadoop/ hadoop@slave-2:/opt/hadoop/
rsync -avxP /opt/hadoop/ hadoop@slave-3:/opt/hadoop/</pre>

<p style="text-align: justify;">
  Now, we need to perform some changes exclusively to the master node:<br /> We will create a directory that will be used for HDFS. I decided to create it in <strong>/opt/hadoop/hadoop_tmp</strong><br /> Inside that directory, create another with the name &#8220;hdfs&#8221; and there, create yet another one named &#8220;namenode&#8221;. So you will have something like this:<br /> <strong> /opt/hadoop_tmp/hdfs/namenode</strong>
</p>

<p style="text-align: justify;">
  Once the basic installation is in all four nodes and the master is properly configured, we can go ahead and perform the customizations in the slaves nodes.<br /> We will create a directory that will be used for HDFS. I decided to create it in <strong>/opt/hadoop/hadoop_tmp</strong> (you can choose anything else, but make sure it is consistent with the contents of <strong>hdfs-site.xml</strong>)<br /> Inside that directory, create another with the name &#8220;hdfs&#8221; and there, create yet another one named &#8220;datanode&#8221;. So you will have something like this:<br /> <strong> /opt/hadoop_tmp/hdfs/datanode</strong>
</p>

<p style="text-align: justify;">
  Again, all the files inside your Hadoop home should be owned by the Hadoop user you created. Otherwise you may get &#8220;Permission denied&#8221; errors while starting the services.
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh decode:true">sudo chown hadoop:hadoop -R /opt/hadoop/hadoop_tmp</pre>

Back in the master, format the namenode:

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh highlight:0 decode:true">hadoop@master: /opt/hadoop/hadoop/bin/$ ./hdfs namenode -format</pre>

<p style="text-align: justify;">
  Finally, start the services. Previously, Hadoop used the start-all.sh script for this, but it has been deprecated and the recommended method now is to use the <strong>start-<service>.sh</strong> scripts individually. In the master node, execute the following:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh highlight:0 decode:true">/opt/hadoop/hadoop/sbin/start-dfs.sh
Starting namenodes on [master]
master: starting namenode, logging to /opt/hadoop/hadoop/logs/hadoop-root-namenode-atlbz153122.out
slave-2: starting datanode, logging to /opt/hadoop/hadoop/logs/hadoop-root-datanode-atlbz153078.out
slave-3: starting datanode, logging to /opt/hadoop/hadoop/logs/hadoop-root-datanode-atlbz153064.out
slave-1: starting datanode, logging to /opt/hadoop/hadoop/logs/hadoop-root-datanode-atlbz153120.out
Starting secondary namenodes [0.0.0.0]
0.0.0.0: starting secondarynamenode, logging to /opt/hadoop/hadoop/logs/hadoop-root-secondarynamenode-atlbz153122.out

/opt/hadoop/hadoop/sbin/start-yarn.sh
starting yarn daemons
starting resourcemanager, logging to /opt/hadoop/hadoop/logs/yarn-root-resourcemanager-atlbz153122.out
slave-2: starting nodemanager, logging to /opt/hadoop/hadoop/logs/yarn-root-nodemanager-atlbz153078.out
slave-3: starting nodemanager, logging to /opt/hadoop/hadoop/logs/yarn-root-nodemanager-atlbz153064.out
slave-1: starting nodemanager, logging to /opt/hadoop/hadoop/logs/yarn-root-nodemanager-atlbz153120.out</pre>

<p style="text-align: justify;">
      There are several ways to confirm that everything is running properly, for example, you can point your browser to http://master:50070 or http://master:8088. You can also check the Java processes in the nodes. In the master node you should see at least 3 processes: NameNode, SecondaryNameNode and ResourceManager. In the slaves you should see only two: NodeManager and DataNode. My favourite way is to use the hdfs report command. This is the output report of my configuration:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh highlight:0 decode:true">/opt/hadoop/hadoop/bin/hdfs dfsadmin -report
Configured Capacity: 189496233984 (176.48 GB)
Present Capacity: 174329384960 (162.36 GB)
DFS Remaining: 174329225216 (162.36 GB)
DFS Used: 159744 (156 KB)
DFS Used%: 0.00%
Under replicated blocks: 0
Blocks with corrupt replicas: 0
Missing blocks: 0
-------------------------------------------------
Live datanodes (3):

Name: 9.9.153.64:50010 (slave-3)
Hostname: atlbz153064.bz.atlanta.example.com
Decommission Status : Normal
Configured Capacity: 63165411328 (58.83 GB)
DFS Used: 53248 (52 KB)
Non DFS Used: 5051596800 (4.70 GB)
DFS Remaining: 58113761280 (54.12 GB)
DFS Used%: 0.00%
DFS Remaining%: 92.00%
Configured Cache Capacity: 0 (0 B)
Cache Used: 0 (0 B)
Cache Remaining: 0 (0 B)
Cache Used%: 100.00%
Cache Remaining%: 0.00%
Xceivers: 1
Last contact: Tue Jan 05 18:46:14 EST 2016

Name: 9.9.153.78:50010 (slave-2)
Hostname: atlbz153078.bz.atlanta.example.com
Decommission Status : Normal
Configured Capacity: 63165411328 (58.83 GB)
DFS Used: 53248 (52 KB)
Non DFS Used: 5051629568 (4.70 GB)
DFS Remaining: 58113728512 (54.12 GB)
DFS Used%: 0.00%
DFS Remaining%: 92.00%
Configured Cache Capacity: 0 (0 B)
Cache Used: 0 (0 B)
Cache Remaining: 0 (0 B)
Cache Used%: 100.00%
Cache Remaining%: 0.00%
Xceivers: 1
Last contact: Tue Jan 05 18:46:14 EST 2016

Name: 9.9.153.120:50010 (atlbz153120.bz.atlanta.example.com)
Hostname: atlbz153120.bz.atlanta.ibm.com
Decommission Status : Normal
Configured Capacity: 63165411328 (58.83 GB)
DFS Used: 53248 (52 KB)
Non DFS Used: 5063622656 (4.72 GB)
DFS Remaining: 58101735424 (54.11 GB)
DFS Used%: 0.00%
DFS Remaining%: 91.98%
Configured Cache Capacity: 0 (0 B)
Cache Used: 0 (0 B)
Cache Remaining: 0 (0 B)
Cache Used%: 100.00%
Cache Remaining%: 0.00%
Xceivers: 1
Last contact: Tue Jan 05 18:46:15 EST 2016</pre>

<p style="text-align: justify;">
      Congratulations! At this point, Hadoop is configured and running. You can stop here, but I would prefer to run a test, just to make sure everything is working correctly. We will upload some files to the HDFS.
</p>

Check the disk usage:

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false nums:false wrap:true lang:sh decode:true">/opt/hadoop/hadoop/bin/hadoop fs -df -h
Filesystem             Size   Used  Available  Use%
hdfs://master:9000  176.5 G  156 K    162.4 G    0%</pre>

Make a test directory:

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh decode:true">/opt/hadoop/hadoop/bin/hadoop fs -mkdir hdfs://master:9000/testdir0</pre>

[<img class="aligncenter wp-image-1082 size-full" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/hadoopFS1.png" alt="hadoopFS1" width="1403" height="445" />](https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/hadoopFS1.png)

List the contents of root:

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh decode:true">/opt/hadoop/hadoop/bin/hadoop fs -ls hdfs://master:9000/
Found 1 items
drwxr-xr-x   - root supergroup          0 2016-01-05 18:19 hdfs://master:9000/testdir0</pre>

<p style="text-align: justify;">
  Let&#8217;s create a file locally and add text to it (courtesy of <a href="http://loremgibson.com" target="_blank">loremgibson.com</a>) just so we see it is replicated to all the nodes:
</p>

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false toolbar:2 nums:false wrap:true lang:sh highlight:0 decode:true">vim /tmp/testdir1/loremGibson.txt</pre>

Then add our text file to our new directory:

<pre class="theme:sublime-text font:ubuntu-mono font-size-enable:false nums:false wrap:true lang:sh decode:true">/opt/hadoop/hadoop/bin/hadoop fs -copyFromLocal /tmp/testdir1/loremGibson.txt hdfs://master:9000/testdir0/loremGibson.txt</pre>

[<img class="aligncenter wp-image-1083 size-full" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/hadoopFS2.png" alt="hadoopFS2" width="1395" height="451" />](https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/hadoopFS2.png)

Now you can see that our file has been automatically replicated to all 3 nodes!

<img class="aligncenter size-full wp-image-1084" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/01/hadoopFS3.png" alt="hadoopFS3" width="610" height="612" /> 

**Conclusion:**

<p style="text-align: justify;">
      Hadoop is not hard to install nor configure, but you need to pay very close attention to many aspects, otherwise you will get obscure errors and since this is a &#8220;new&#8221; technology, the amount of useful help you can get is not great. Also, since this a complex technology, many problems can arise and are hard to troubleshoot. Sadly, there are not many online resources that are easy to follow, or the ones that are written properly are mostly outdated already. Personally, I had to read many tutorials and do a lot of troubleshooting in order to setup this correctly because many of the tutorials I read omitted bits of important information. There are, however, other projects that can help with the administration of Hadoop and its components. Two good examples are IBM BigInsights and Ambari. Even without those tools, adding and removing Hadoop nodes is very easy once the basic setup is correctly configured. I am nowhere near of being an expert on Big Data yet, but I tried my best to write this post as clear as possible and I truly hope it is useful. Big Data is undoubtedly here to stay and this kind of publications are indeed a valuable resource for newcomers.
</p>