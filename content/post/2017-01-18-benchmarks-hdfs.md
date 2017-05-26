---
title: Benchmarks HDFS
author: markus
type: post
date: 2017-01-18T20:20:56+00:00
url: /?p=635
categories:
  - Hadoop
tags:
  - benchmark
  - hdfs

---
Benchmarks eines HDFS lassen meist einfach durch beigelieferte Jars durchführen. Beispielsweise bei Hortonworks: 

`Benchmarks eines HDFS lassen meist einfach durch beigelieferte Jars durchführen. Beispielsweise bei Hortonworks: 

` 

Hierbei werden mit dem Test &#8222;TestDFSIO&#8220; jeweils 100 Files mit 100MB Größe ins HDFS geschrieben, anschließend kann auch die Leseperformance getestet werden. 

``Benchmarks eines HDFS lassen meist einfach durch beigelieferte Jars durchführen. Beispielsweise bei Hortonworks: 

`Benchmarks eines HDFS lassen meist einfach durch beigelieferte Jars durchführen. Beispielsweise bei Hortonworks: 

` 

Hierbei werden mit dem Test &#8222;TestDFSIO&#8220; jeweils 100 Files mit 100MB Größe ins HDFS geschrieben, anschließend kann auch die Leseperformance getestet werden. 

`` 

Die Testdaten bleiben im HDFS erhalten unter /benchmarks/TestDFSIO, sie können allerdings folgend auch gelöscht werden: 

`hadoop jar /usr/hdp/2.3.4.0-3485/hadoop-mapreduce/hadoop-mapreduce-client-jobclient-*-tests.jar TestDFSIO -clean`