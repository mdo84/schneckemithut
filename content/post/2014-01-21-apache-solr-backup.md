---
title: Apache Solr Backup
author: markus
type: post
date: 2014-01-21T09:31:41+00:00
url: /?p=248
categories:
  - Allgemein

---
Ein Backup eines Solr-Indexes lässt sich leicht mit Curl durchführen: 

<pre>curl 'http://localhost:8980/solr/$core/replication?command=backup&numberToKeep=1&location=/data/backup/$core'</pre>

Wobei hier der Replication-Handler in der Solrconfig.xml eingetragen sein muss. In diesem Falle kann auch auf einem Slave (im Master/Slave-Setup) ein Backup durchgeführt werden. Das Backup wird lokal auf der Maschine durchgeführt, Pfade und Port sollten natürlich stimmen.
  
Hierzu noch etwas <a href="https://cwiki.apache.org/confluence/display/solr/Backing+Up" title="https://cwiki.apache.org/confluence/display/solr/Backing+Up" target="_blank">Lektüre.</a>