---
id: 1024
title: Introduction to Apache Spark
date: 2016-02-09T15:40:28-05:00
author: Alan Verdugo
guid: http://www.kippel.net/blog/?p=1024
permalink: /blog/spark-introduction
#permalink: /?p=1024
categories:
  - Uncategorized
tags:
  - english
  - IT
  - open source
  - Technical writing
---
<p style="text-align: justify;">
  <img class="alignleft size-full wp-image-1140" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/02/SPARKlogosmall-1.jpeg" alt="SPARKlogosmall" width="199" height="104" />    Spark is an open source cluster computing framework widely known for being extremely fast. It was started by AMPLab at UC Berkeley in 2009. Now it is an Apache top-level project. Spark can run on its own or can run, for example, in Hadoop or <a href="https://mesos.apache.org/" target="_blank">Mesos</a>, and it can access data from diverse sources, including HDFS, Cassandra, HBase and Hive. Spark shares some characteristics with Apache Hadoop but they have important differences. Spark was developed to overcome the limitations of Hadoop&#8217;s MapReduce in regards of iterative algorithms and interactive data analysis.
</p><figure id="attachment_1133" aria-describedby="caption-attachment-1133" style="width: 251px" class="wp-caption alignright">

<img class="size-full wp-image-1133" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/02/spark7.png" alt="Logistic regression in Hadoop and Spark." width="251" height="140" /> <figcaption id="caption-attachment-1133" class="wp-caption-text">Logistic regression in Hadoop and Spark.</figcaption></figure> 

<p style="text-align: justify;">
     Since the very beginning, Spark showed great potential. Soon after its creation, Spark was already showing that it was being ten or twenty times faster than MapReduce for certain jobs. If is often said that it can be as 100 times faster, and this has been proven many times. For that reason, it is now widely used in areas where analysis is fundamental, like retail, astronomy, biomedicine, physics, marketing, and of course, IT. Thanks to this, Spark has become synonymous with a new term: &#8220;Fast data&#8221;. This means having the capability to process large amounts of data as fast as possible. Let&#8217;s not forget Spark&#8217;s motto and raison d&#8217;être: &#8220;Lightning-fast cluster computing&#8221;.
</p>

<p style="text-align: justify;">
     Spark can efficiently scale up and down using minimal resources, and developers enjoy a more concise API, which helps them be more productive. Spark supports Scala, Java, Python, and R. While it also offers interactive shells for Scala and Python.
</p>

<p style="text-align: justify;">
  <strong>Components:</strong>
</p>

<li style="text-align: justify;">
  Spark Core and Resilient Distributed Datasets. As its name implies, Spark Core contains the basic Spark functionality, it includes task scheduling, memory management, fault recovery, interaction with storage systems, and more. Resilient Distributed Datasets (RDDs) are Spark&#8217;s main programming abstraction, they are logical collections of data partitioned across nodes. RDDs can be seen as the &#8220;base unit&#8221; in Spark. Generally, RDDs reside in memory and will only use the disc as a last resource. This is the reason why Spark is usually much faster than MapReduce jobs.
</li>
<li style="text-align: justify;">
  Spark SQL. This is how Spark interacts with structured data (like SQL or HQL). Shark was a previous effort in doing this, which was later abandoned in favor of Spark SQL. Spark SQL allows developers to intermix SQL with any of Spark’s supported programming languages.
</li>
<li style="text-align: justify;">
  Spark Streaming. Streaming, in the context of Big Data, is not to be confused with video or audio streaming, even if they are similar concepts. Spark Streaming handles any kind of data instead of only video or audio feeds. So, it is used to process data that does not stop coming at any time in particular (like a stream). For example, Tweets or logs from production web servers.
</li>
<li style="text-align: justify;">
  MLlib. It is a Machine Learning library, it contains the common functionality of machine learning algorithms like classification, regression, clustering, and collaborative filtering. All of these algorithms are designed to scale out across the cluster.
</li>
<li style="text-align: justify;">
  GraphX. Apache Spark&#8217;s API for graphs and graph-parallel computation, it comes with a variety of graph algorithms.
</li>

<img class="aligncenter size-full wp-image-1125" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/02/spark2.png" alt="spark2" width="1113" height="371" /> 

<p style="text-align: justify;">
     Spark can recover failed nodes by recomputing the Directed Acyclic Graph (DAG) of the RDDs, and it also supports a recovery method using &#8220;checkpoints&#8221;. This is a clever way of guaranteeing fault tolerance that minimizes network I/O. RDDs achieve this by using lineage, i.e. if an RDD is lost, the RDD has enough information about how it was derived from other RDD (i.e. the DAGs are &#8220;replayed&#8221;), so it can be rebuilt easily. This works better than fetching data from disk every time. In this way, fault tolerance is achieved without using replication.
</p>

<p style="text-align: justify;">
  <strong>Spark usage metrics:</strong>
</p>

<p style="text-align: justify;">
     In late December 2014, <a href="http://www.typesafe.com/" target="_blank">Typesafe</a> created <a href="https://info.typesafe.com/COLL-20XX-Spark-Survey-Report_LP.html?lst=DZ&lsd=COLL-20XX-Spark-Survey-Trends-Adoption-Report" target="_blank">a survey</a> about Spark, and they noticed a &#8220;hockey-stick-like&#8221; growth in its use<sup>[1]</sup>, with many people already using Spark in production or planning to do it soon. The survey reached 2,136 technology professionals. These are some of their conclusions:
</p>

<li style="text-align: justify;">
  13% of respondents currently use Spark in production, while 31% are evaluating Spark and 20% planned to use it in 2015.
</li>
<li style="text-align: justify;">
  78% of Spark users hope to use the tool to solve issues with fast batch processing of large data sets.
</li>
<li style="text-align: justify;">
  Low awareness and/or experience is currently the biggest barrier for users implementing Spark effectively.
</li>
<li style="text-align: justify;">
  Top 3 industries represented: Telecoms, Banks, Retail.
</li><figure id="attachment_1131" aria-describedby="caption-attachment-1131" style="width: 800px" class="wp-caption aligncenter">

<img class="wp-image-1131 size-full" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/02/spark5.png" alt="Typesafe survey results snapshot." width="800" height="450" /> <figcaption id="caption-attachment-1131" class="wp-caption-text">Typesafe survey results snapshot.</figcaption></figure> 

<p style="text-align: justify;">
     So, is Spark better than Hadoop? This is a question that is very difficult to answer. This is a topic that is frequently discussed, and the only conclusion is that there is no clear winner. Both technologies offer different advantages and they can be used alongside perfectly. That is the reason why the Apache foundation has not merged both projects, and this will likely not happen, at least not anytime soon. Hadoop reputation was cemented as the Big Data poster child, and with good reason. And for that, with every new project that emerges, people wonder how it relates to Hadoop. Is it a complement for Hadoop? A competitor? An enabler? something that could leverage Hadoop&#8217;s capabilities? all of the above?
</p><figure id="attachment_1124" aria-describedby="caption-attachment-1124" style="width: 618px" class="wp-caption aligncenter">

<img class="wp-image-1124 size-full" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2016/02/spark.png" alt="Comparison of Spark's stack and alternatives." width="618" height="259" /> <figcaption id="caption-attachment-1124" class="wp-caption-text">Comparison of Spark&#8217;s stack and alternatives.</figcaption></figure> 

<p style="text-align: justify;">
     As you can see in the table above, Spark offers a lot of functionality out of the box. If you wanted to build an environment with the same capabilities, you would need to install, configure and maintain several projects at the same time. This is one of the great advantages in Spark: having a full-fledged data engine ready to work out of the box. Of course, many of the projects are interchangeable. For example, you could easily use HDFS for storage instead of Tachyon, or use YARN instead of Mesos. The fact that all of these are open source projects means they have a lot of versatility, and this means the users can have many options available, so they can have their cake <em>and</em> eat it. For example, if you are used to program in Pig and want to use it in Spark, a new project called Spork (you got to love the name) was created so you can do it. Hive, Hue, Mahout and many other tools from the Hadoop ecosystem already work or soon will work with Spark.<sup>[2]</sup>
</p>

<p style="text-align: justify;">
     Let&#8217;s say you want to build a cluster, and you want it to be cheap. Since Spark uses memory heavily, and RAM is relatively expensive, one could think that Hadoop MapReduce is cheaper, since MapReduce relies more on disc space than on RAM. However, the potentially more expensive Spark cluster could finish the job faster precisely because it uses RAM heavily. So, you could end up paying a few hours of usage for the Spark cluster instead of days for the Hadoop cluster. The official Spark FAQ page talks about how Spark was used to sort 100 TB of data three times faster than Hadoop MapReduce on 1/10th of the machines, winning the <a href="https://databricks.com/blog/2014/11/05/spark-officially-sets-a-new-record-in-large-scale-sorting.html" target="_blank">2014 Daytona Graysort Benchmark</a><sup>[3]</sup>.
</p>

<p style="text-align: justify;">
     If you have specific needs (like running machine learning algorithms, for example) you may decide over one technology or the other. It all really depends of what you need to do and how you are paying for resources. It is basically a case-by-case decision. Neither Spark nor Hadoop are silver bullets. In fact, I would say that there are no silver bullets in Big Data yet. For example, while Spark has streaming capabilities, Apache Storm generally is considered better at it.
</p>

<p style="text-align: justify;">
  <strong>Real-world use-cases:</strong>
</p>

<p style="text-align: justify;">
     There are many ingenious and useful examples of Spark in the wild. Let&#8217;s talk about some of them.
</p>

<p style="text-align: justify;">
     IBM has been working with NASA and the <a href="http://www.seti.org/" target="_blank">SETI Institute</a> using Spark in order to analyze 100 million radio events detected over several years. This analysis could lead to the discovery of intelligent extraterrestrial life. <sup>[4] [5] [6]</sup>
</p>

<p style="text-align: justify;">
     The analytic capabilities of Spark are also being used to identify suspicious vehicles mentioned in AMBER alerts. Basically, video feeds are entered into a Spark cluster using Spark Streaming, then they are processed with OpenCV for image recognition and MLlib for machine learning. Together, they would identify the model and color of cars. Which in turn could help to find missing children.<sup>[4]</sup> Spark&#8217;s speed here is crucial. In this example, huge amounts of live data need to be processed as quickly as possible and it also needs to be done continually, i.e. processing as the data is being collected, hence the use of Spark Streaming. <sup>[7]</sup>
</p>

<p style="text-align: justify;">
     <a href="http://www.berkshirehathaway.com/" target="_blank">Warren Buffet</a> created an application where social network analysis is performed in order to predict stock trends. Based on this, the user of the application gets recommendations from the application about when and how to buy, sell or hold stocks. It is obvious that a lot of people would be interested in suggestions like this, and specially when they are taken from live, real data like Tweets. All this is accomplished with Spark Streaming and MLlib.<sup>[4]</sup>
</p>

<p style="text-align: justify;">
     Of course, there is also a long list of companies using Spark for their day-to-day analytics, the <a href="https://cwiki.apache.org/confluence/display/SPARK/Powered+By+Spark" target="_blank">&#8220;Powered by Spark&#8221;</a> page has a lot of important names like Yahoo, eBay, Amazon, NASA, Nokia, IBM Almaden, UC Berkeley, TripAdvisor, among many others.
</p>

<p dir="ltr" style="text-align: justify;">
     Take, for example, mapping Twitter activity based on streaming data. In the video below you can see a Spark Notebook that is consuming the Twitter stream, filtering the tweets that have geospatial information and plotting them on a map that is narrowing the view to the minimal bounding box enclosing the last batch&#8217;s tweets. It is very easy to imagine the collaboration that streaming technologies and the Internet of Things will end up doing. All that data generated by IoT devices will need to be processed and streaming tools like Spark Streaming and/or Apache Storm will be there to do the job.
</p>



<p style="text-align: justify;">
  <strong>Conclusion:</strong>
</p>

<p style="text-align: justify;">
     Spark was designed in a very intelligent way. Since it is newer, the architects used the learned lessons from other projects (mainly from Hadoop). The emergence of the Internet of Things is already producing a constant flow of large amounts of data. There will be a need to gather that data, process it and draw conclusions on it. Spark can do all of this and do it blindingly fast.
</p>

<p style="text-align: justify;">
     IBM has shown a tremendous amount of interest and commitment to Spark. For example, they founded the <a href="http://www.spark.tc/" target="_blank">Spark Technology Center</a> in San Francisco, enabled a Spark-As-A-Service model on <a href="http://bit.ly/fromblogtosite" target="_blank">Bluemix</a>, and organized Spark hackatons<sup>[8]</sup>. They also committed to train more than 1 million of data scientists, and donated <a href="https://developer.ibm.com/open/systemml/" target="_blank">SystemML</a> (a machine learning technology) to further advance Spark&#8217;s development <sup>[9]</sup>. That doesn’t happen if an initiative doesn&#8217;t have support at the highest levels of the company. In fact, they have called it &#8220;potentially, the most significant open source project of the next decade&#8221;. <sup>[10]</sup>
</p>

<p style="text-align: justify;">
     All this heralds a bright future for Spark and the related projects. It is hard to imagine how the project will evolve, but the impact it has already done in the big data ecosystem is something to take very seriously.
</p>

<p style="text-align: justify;">
  <strong>References:</strong>
</p>

<p style="text-align: justify;">
  [1] <a href="http://www.slideshare.net/Typesafe_Inc/sneak-preview-apache-spark" target="_blank">http://www.slideshare.net/Typesafe_Inc/sneak-preview-apache-spark</a>
</p>

<p style="text-align: justify;">
  [2] <a href="http://es.slideshare.net/sbaltagi/spark-or-hadoop-is-it-an-eitheror-proposition-by-slim-baltagi" target="_blank">http://es.slideshare.net/sbaltagi/spark-or-hadoop-is-it-an-eitheror-proposition-by-slim-baltagi</a>
</p>

<p style="text-align: justify;">
  [3] <a href="https://spark.apache.org/faq.html" target="_blank">https://spark.apache.org/faq.html</a>
</p>

<p style="text-align: justify;">
  [4] <a href="http://www.spark.tc/projects/" target="_blank">http://www.spark.tc/projects/</a>
</p>

<p style="text-align: justify;">
  [5] <a href="http://blog.ibmjstart.net/2015/07/14/seti-sparks-machine-learning-to-sift-big-data/" target="_blank">http://blog.ibmjstart.net/2015/07/14/seti-sparks-machine-learning-to-sift-big-data/</a>
</p>

<p style="text-align: justify;">
  [6] <a href="http://blog.ibmjstart.net/2015/08/06/types-of-bigdata-from-the-allen-telescope-array/" target="_blank">http://blog.ibmjstart.net/2015/08/06/types-of-bigdata-from-the-allen-telescope-array/</a>
</p>

<p style="text-align: justify;">
  [7] <a href="https://github.com/hackspark/Amber-Alert-Aid" target="_blank">https://github.com/hackspark/Amber-Alert-Aid</a>
</p>

<p style="text-align: justify;">
  [8] <a href="http://blog.ibmjstart.net/2015/06/29/why-is-ibm-involved-with-apache-spark/" target="_blank">http://blog.ibmjstart.net/2015/06/29/why-is-ibm-involved-with-apache-spark/</a>
</p>

<p style="text-align: justify;">
  [9] <a href="http://www.ibm.com/analytics/us/en/technology/spark/" target="_blank">http://www.ibm.com/analytics/us/en/technology/spark/</a>
</p>

<p style="text-align: justify;">
  [10] <a href="https://www-03.ibm.com/press/us/en/pressrelease/47107.wss" target="_blank">https://www-03.ibm.com/press/us/en/pressrelease/47107.wss</a>
</p>