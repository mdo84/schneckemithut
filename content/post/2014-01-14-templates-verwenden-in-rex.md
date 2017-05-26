---
title: Templates verwenden in Rex
author: markus
type: post
date: 2014-01-14T11:30:07+00:00
url: /?p=225
categories:
  - Rex

---
Um Templates in Rex-Tasks verwenden zu können ist nur ein Aufruf von 

<pre>file "/tmp/${solr_core}/conf/solrconfig.xml",
         content => template($config_path . "/solrconfig-solrslaves.xml", masterurl => $MASTER_URL, solrcore => $solr_core);</pre>

notwendig. Wobei hier ${solr\_core} eine Variable eines Arrays darstellt. $config\_path enspricht dem Config-Pfad des Tempates. &#8222;masterurl&#8220; und &#8222;solrcore&#8220; sind Variablen, die im Template mit
  
`<%= $::masterurl %>` hinterlegt sind. Die Übergabe der im Task verwendeten Variablen an das Template $MASTER\_URL und $solr\_core erfolgt am Ende der template()-Anweisung.