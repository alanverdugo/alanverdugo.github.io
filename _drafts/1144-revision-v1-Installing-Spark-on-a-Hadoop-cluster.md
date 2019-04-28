---
id: 1150
title: Installing Spark on a Hadoop cluster
date: 2016-02-15T14:08:05-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=1150
permalink: /?p=1150
---
First, we will <a href="https://spark.apache.org/downloads.html" target="_blank">download</a> the newest version of Spark. In this case, we will download version 1.6.0 pre-built for Hadoop 2.6 or later.

&nbsp;

mkdir /tmp/spark/; cd /tmp/spark  
wget http://mirror.metrocast.net/apache/spark/spark-1.6.0/spark-1.6.0-bin-hadoop2.6.tgz

&nbsp;

We create a home directory for Spark and uncompress our tarball in it.

mkdir /opt/spark

tar -zvxf /tmp/spark/spark-1.6.0-bin-hadoop2.6.tgz

mv /tmp/spark/spark-1.6.0-bin-hadoop2.6/* /opt/spark

&nbsp;

Add the SPARK_HOME variable to .bashrc:

export SPARK_HOME=/opt/spark

&nbsp;

There are 3 ways to deploy Spark with Hadoop: Standalone, Spark on YARN and Spark on MapReduce.