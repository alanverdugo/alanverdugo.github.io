---
id: 1004
title: Introduction to Apache Hadoop
date: 2015-12-02T16:28:47-05:00
author: Alan Verdugo
guid: http://www.kippel.net/blog/?p=1004
permalink: /blog/hadoop-introduction
#permalink: /?p=1004
categories:
  - Uncategorized
tags:
  - english
  - IT
  - Technical writing
---
<p style="text-align: justify;">
      Hadoop is an open source project from the Apache foundation that was created thinking that hardware components in a network are prone to failure and that there should be a component handling those failures automatically in a way that does not create downtime for the system or affects the users in any way. Hadoop is mainly written in Java and it can run on the main operating systems. It was originally created by Doug Cutting while he was working on Yahoo. It was named after a toy elephant that belongs to Doug&#8217;s son.
</p>

<p style="text-align: justify;">
      The ever-growing need of data storage is also a big part of the Hadoop inception. In this day and age, a company storing user data cannot afford to lose any of it due to hardware failures. Just imagine getting an email saying <em>&#8220;We just lost all your photos/messages/work/art/portfolio/reports/money because one of our servers failed. Sorry!&#8221;</em>. That is simply unacceptable, and Hadoop was created to prevent that problem.
</p>

<p style="text-align: justify;">
      Just the task of storing that data is an enormous challenge. Being responsible for handling sensitive data in large amounts can be very intimidating. Just imagine being the architect of a successful startup that suddenly is required to not store and handle Gigabytes, but Terabytes, or even Petabytes of data. And more importantly, you are required to do it in a manner that is secure, cheap, fast, easy, scalable, and failure-proof. How would you accomplish that? Requesting larger and larger budgets for servers and hard-drives, all of them having a life-span of a few months? Or would you prefer to use commodity hardware with a framework that handles all that for you? If you chose the later, Hadoop may be the answer. Hadoop is the software component that allows the IT infrastructure to grow organically and easily when it needs to do it. It prevents individual hardware failures to cause any real impact to the IT services and, ultimately, to the user experience.
</p>

<p style="text-align: justify;">
      Not convinced yet? What if I told you that you can use Hadoop to do parallel processing and leverage all that combined horsepower from your commodity hardware? We will talk about how Hadoop accomplishes all these wonderful things later, but for now, let&#8217;s talk about the main Hadoop components.
</p>

<h3 style="text-align: justify;">
  Hadoop components
</h3>

<p style="text-align: justify;">
      Hadoop has two main components, not counting the Hadoop core functionality and YARN (Yet Another Resource Negotiator, a resource-management platform responsible for managing computing resources in clusters). These two main components are MapReduce and HDFS.
</p>

<p style="text-align: justify;">
      MapReduce is a framework for performing calculations on the data in the distributed file system. With MapReduce, applications can process vast amounts (multiple terabytes) of data in parallel on large clusters in a reliable, fault-tolerant manner. MapReduce uses one &#8220;JobTracker&#8221; node, to which applications submit MapReduce jobs. The JobTracker &#8220;maps&#8221; or assigns work and pushes it out to available &#8220;TaskTracker&#8221; nodes in the cluster, striving to keep the work as close to the data as possible. Each TaskTracker performs the required processing and then the results are retrieved by the JobTracker node (this is the &#8220;reduce&#8221; part).
</p>

<p style="text-align: justify;">
      The distributed filesystem component, the main example of which is HDFS (Hadoop Distributed File System), though other file systems, such as IBM GPFS-FPO, are supported. In HDFS, there is a &#8220;NameNode&#8221; keeping track of all the locations of all the data across the cluster. The other nodes are called &#8220;DataNodes&#8221; and store the data in &#8220;blocks&#8221; of information. The same blocks are copied in several DataNodes (generally in another DataNode in the same rack and also in another DataNode in a different rack). Obviously, the higher the data redundancy in the cluster, the safer the data is in case one or several DataNodes go down or suffer irreparable damage. A Hadoop user can easily specify the amount of replication that is needed and customize the way the blocks are handled.
</p><figure id="attachment_1018" aria-describedby="caption-attachment-1018" style="width: 671px" class="wp-caption aligncenter">

<img class="wp-image-1018" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2015/12/IHS.jpg" alt="High level architecture" width="671" height="483" /> <figcaption id="caption-attachment-1018" class="wp-caption-text">Fig. 1: High level architecture diagram showing the the MapReduce and the HDFS layers.</figcaption></figure> 

<h3 style="text-align: justify;">
  Related projects
</h3>

<p style="text-align: justify;">
      Due to its potential and usefulness, Hadoop is one of the most famous projects related to big data and it has inspired many related projects. Many implementations of Hadoop use some (or many) of these projects in order to build a robust ad-hoc infrastructure. Some of them are:
</p>

<p style="text-align: justify;">
      <a href="https://ambari.apache.org/" target="_blank">Ambari</a>: A web-based tool for provisioning, managing, and monitoring Apache Hadoop clusters which includes support for Hadoop HDFS, Hadoop MapReduce, Hive, HCatalog, HBase, ZooKeeper, Oozie, Pig and Sqoop. Ambari also provides a dashboard for viewing cluster health such as heatmaps and ability to view MapReduce, Pig and Hive applications visually along with features to diagnose their performance characteristics in a user-friendly manner.
</p>

<p style="text-align: justify;">
      <a href="https://avro.apache.org/" target="_blank">Avro</a>: A data serialization system.
</p>

<p style="text-align: justify;">
      <a href="https://cassandra.apache.org/" target="_blank">Cassandra</a>: A scalable multi-master database with no single points of failure.
</p>

<p style="text-align: justify;">
      <a href="http://chukwa.apache.org/" target="_blank">Chukwa</a>: A data collection system for managing large distributed systems.
</p>

<p style="text-align: justify;">
      <a href="http://flume.apache.org/" target="_blank">Flume</a>: A distributed, reliable, and highly available service for efficiently moving large amounts of data around a cluster.
</p>

<p style="text-align: justify;">
      <a href="http://hbase.apache.org/" target="_blank">HBase</a>: A non-relational, scalable, distributed database that supports structured data storage for large tables.
</p>

<p style="text-align: justify;">
      <a href="https://hive.apache.org/" target="_blank">Hive</a>: A data warehouse infrastructure that provides data summarization and ad-hoc querying.
</p>

<p style="text-align: justify;">
      <a href="https://code.google.com/p/jaql/" target="_blank">Jaql</a>: A query language designed for JavaScript Object Notation (JSON), is primarily used to analyze large-scale semi-structured data. It is an open source project from Google, IBM took it over as primary data processing language for their Hadoop software package BigInsights (see the &#8220;Hadoop and IBM&#8221; section below).
</p>

<p style="text-align: justify;">
      <a href="https://mahout.apache.org/" target="_blank">Mahout</a>: A Scalable machine learning and data mining library.
</p>

<p style="text-align: justify;">
      <a href="http://oozie.apache.org/" target="_blank">Oozie</a>: A workflow coordination manager.
</p>

<p style="text-align: justify;">
      <a href="https://pig.apache.org/" target="_blank">Pig</a>: A high-level data-flow language and execution framework for parallel computation.
</p>

<p style="text-align: justify;">
     <a href="https://spark.apache.org/" target="_blank">Spark</a>: A fast and general compute engine for Hadoop data. Spark provides a simple and expressive programming model that supports a wide range of applications, including ETL, machine learning, stream processing, and graph computation. I will also be talking about Spark very soon.
</p>

<p style="text-align: justify;">
      <a href="https://sqoop.apache.org/" target="_blank">Sqoop</a>: A command-line interface application for transferring data between relational databases and Hadoop.
</p>

<p style="text-align: justify;">
      <a href="http://tez.apache.org/" target="_blank">Tez</a>: A generalized data-flow programming framework, built on Hadoop YARN, which provides a powerful and flexible engine to execute an arbitrary DAG of tasks to process data for both batch and interactive use-cases. Tez is being adopted by Hive, Pig and other frameworks in the Hadoop ecosystem, and also by other commercial software (e.g. ETL tools), to replace Hadoop MapReduce as the underlying execution engine.
</p>

<p style="text-align: justify;">
      <a href="https://zookeeper.apache.org/" target="_blank">ZooKeeper</a>: A high-performance coordination service for distributed applications.
</p><figure id="attachment_1020" aria-describedby="caption-attachment-1020" style="width: 538px" class="wp-caption aligncenter">

<img class="wp-image-1020 size-full" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2015/12/EcoSys_yarn.png" alt="EcoSys_yarn" width="538" height="355" /> <figcaption id="caption-attachment-1020" class="wp-caption-text">Fig. 2: An example of a Hadoop environment using several related projects.</figcaption></figure> 

<h3 style="text-align: justify;">
  Who is using Hadoop?
</h3>

<p style="text-align: justify;">
      Take a look at <a href="http://wiki.apache.org/hadoop/PoweredBy" target="_blank">the &#8220;Powered by&#8221; page at the Hadoop site</a> and <a href="https://en.wikipedia.org/wiki/Apache_Hadoop#Prominent_users" target="_blank">the Hadoop page in Wikipedia</a>. You will notice a very large list of important names and some very impressive numbers. For example, on June of 2010, Facebook announced to store 100 Petabytes of its data on Hadoop clusters, and on November 8 of 2012, they announced the data gathered in their warehouse grows by roughly half a Petabyte per day.
</p>

<p style="text-align: justify;">
      Yahoo is by far the largest contributor to Hadoop, and there is a good reason for that. Yahoo Mail uses Hadoop to find spam. The Yahoo front page as well as the links and ads displayed to every user are both optimized using Hadoop.<sup>[1]</sup> Yahoo contributes all the work it does on Hadoop to the open-source community.
</p>

<p style="text-align: justify;">
      Besides contributors to the Hadoop environment, the usage is widely spread among other companies which are merely users. Proof of that is that more than half of the Fortune 50 use Hadoop.<sup>[2]<br /> </sup>
</p>

<h3 style="text-align: justify;">
</h3>

<h3 style="text-align: justify;">
  Hadoop and IBM
</h3>

<p style="text-align: justify;">
      IBM is aware of the potential in Hadoop and is leveraging it in some of its projects. For example, <a href="http://www.ibmwatson.com/" target="_blank">Watson</a> uses IBM&#8217;s <a href="http://www.research.ibm.com/deepqa/deepqa.shtml" target="_blank">DeepQA</a> software and the <a href="http://uima.apache.org/" target="_blank">Apache UIMA</a> (Unstructured Information Management Architecture) framework. The system was written in various languages, including Java, C++, and Prolog, and runs on the SUSE Linux Enterprise Server 11 operating system using the Hadoop framework to provide distributed computing.<sup>[3]</sup> Hadoop enables Watson to access, sort, and process data in a massively parallel system (90+ server cluster/2,880 processor cores/16 terabytes of RAM/4 terabytes of disk storage).<sup>[4]</sup>
</p>

<p style="text-align: justify;">
      <a href="http://www-03.ibm.com/software/products/en/ibm-biginsights-for-apache-hadoop" target="_blank">IBM BigInsights</a> is a platform for the analysis and visualization of Internet-scale data volumes. It is powered by Hadoop and it offers makes easier to install and administer Hadoop cluster using a web GUI. BigInsights makes it trivial to start and stop Hadoop services and adding, removing nodes to the cluster.
</p>

<p style="text-align: justify;">
      In 2009, IBM discussed running Hadoop over the <a href="https://en.wikipedia.org/wiki/IBM_General_Parallel_File_System" target="_blank">IBM General Parallel File System</a>.<sup>[5]</sup> The source code was published in October 2009.<sup>[6]</sup>
</p>

<h3 style="text-align: justify;">
</h3>

<h3 style="text-align: justify;">
  Conclusion
</h3>

<p style="text-align: justify;">
      Supporting Hadoop will be critical in the near future. The advantages it offers are too many to just ignore it. As the use of big data grows (alongside with customer&#8217;s expectations), most companies will inevitably gravitate to Big Data, Hadoop and/or Hadoop-related technologies in the near future. This is probably not a end-user facing technology like a mobile application or a website, but Hadoop is already ingrained in the back-end of many popular services like Facebook, Twitter, Yahoo, Linkedin, Spotify and many others.
</p>

<p style="text-align: justify;">
      In other words, Hadoop is not a prototype technology anymore, it is already an integral part of the infrastructure for live production applications with millions of concurrent users. Being capable to understand and support Hadoop and all the related technologies will be essential for any IT team very soon, because either clients will request it or it will be a necessity for the internal operations of the organization itself.
</p>

<p style="text-align: justify;">
  References:
</p>

  1. <a href="https://developer.yahoo.com/blogs/hadoop/ll-hadoop-400-alex-3901.html" target="_blank">https://developer.yahoo.com/blogs/hadoop/ll-hadoop-400-alex-3901.html</a>
  2. <a href="http://www.prnewswire.com/news-releases/altiors-altrastar---hadoop-storage-accelerator-and-optimizer-now-certified-on-cdh4-clouderas-distribution-including-apache-hadoop-version-4-183906141.html" target="_blank">http://www.prnewswire.com/news-releases/altiors-altrastar&#8212;hadoop-storage-accelerator-and-optimizer-now-certified-on-cdh4-clouderas-distribution-including-apache-hadoop-version-4-183906141.html</a>
  3. <a href="https://en.wikipedia.org/wiki/Watson_%28computer%29" target="_blank">https://en.wikipedia.org/wiki/Watson_%28computer%29</a>
  4. <a href="https://blogs.apache.org/foundation/entry/apache_innovation_bolsters_ibm_s" target="_blank">https://blogs.apache.org/foundation/entry/apache_innovation_bolsters_ibm_s</a>
  5. <a href="https://www.usenix.org/legacy/events/hotcloud09/tech/full_papers/ananthanarayanan.pdf" target="_blank">https://www.usenix.org/legacy/events/hotcloud09/tech/full_papers/ananthanarayanan.pdf</a>
  6. <a href="https://issues.apache.org/jira/browse/HADOOP-6330" target="_blank">https://issues.apache.org/jira/browse/HADOOP-6330</a>