---
title: MongoDB im Master-/Slave-Setup
author: markus
type: post
date: 2014-04-14T15:16:37+00:00
url: /?p=326
categories:
  - MongoDB

---
Im Zuge eines Projektes habe ich mich ein wenig mit der MongoDB beschäftigt. Die <a href="http://docs.mongodb.org/manual/tutorial/install-mongodb-on-red-hat-centos-or-fedora-linux/" title="MongoDB Installationsanleitung" target="_blank">MongoDB</a> lässt sich neben Singlemode auch in einem Master-/Slave-Setup betreiben.
  
MongoDB unterscheidet hierbei allerdings zwischen Primary und Secondary. In unserem Testsetup betreiben wir auf drei Systemen einen MongoDB-Prozess (mongod) auf Standardport 27017. Diese werden wie folgt gestartet:
  
`mongod --shardsvr --replSet shard1 --port 27017 --rest --dbpath /data/mongo/shard1 --oplogSize 800 > /dev/null &`
  
Der Parameter &#8211;replSet beschreibt hier den Namen des ReplicaSets, &#8211;rest steht für das REST-Interface, den dbpath legen wir zusätzlich noch fest, zusätzlich erhöhen wir das OpLog (Operationslog) auf 800MB. Dies hat folgenden Hintergrund:
  
Die Daten zur Replikation landen standardmäßig in einer &#8222;capped Collection&#8220;. Diese Collection (Collection entspricht einer Tabelle eines RDBMS in MongoDB) hat eine bestimmte Größe. Hat die Collection die gegebene Größe erreicht, fallen die ältesten Einträge dieser Collection heraus und werden durch neuere ersetzt. Gerade dieses Verhalten ist bei Importen oder größeren Inserts in Verbindung mit Replikation gefährlich, da die Collection schneller erneuert wird, als der Secondary replizieren kann. 

Im Grunde haben wir jetzt auf unseren drei Hosts einen mongod-Prozess laufen, über die Eingabe &#8222;mongo&#8220; in der Bash gelangen wir in die mongo-shell. Für die Replikation nehmen wir folgende Eingaben vor:
  
``Im Zuge eines Projektes habe ich mich ein wenig mit der MongoDB beschäftigt. Die <a href="http://docs.mongodb.org/manual/tutorial/install-mongodb-on-red-hat-centos-or-fedora-linux/" title="MongoDB Installationsanleitung" target="_blank">MongoDB</a> lässt sich neben Singlemode auch in einem Master-/Slave-Setup betreiben.
  
MongoDB unterscheidet hierbei allerdings zwischen Primary und Secondary. In unserem Testsetup betreiben wir auf drei Systemen einen MongoDB-Prozess (mongod) auf Standardport 27017. Diese werden wie folgt gestartet:
  
`mongod --shardsvr --replSet shard1 --port 27017 --rest --dbpath /data/mongo/shard1 --oplogSize 800 > /dev/null &`
  
Der Parameter &#8211;replSet beschreibt hier den Namen des ReplicaSets, &#8211;rest steht für das REST-Interface, den dbpath legen wir zusätzlich noch fest, zusätzlich erhöhen wir das OpLog (Operationslog) auf 800MB. Dies hat folgenden Hintergrund:
  
Die Daten zur Replikation landen standardmäßig in einer &#8222;capped Collection&#8220;. Diese Collection (Collection entspricht einer Tabelle eines RDBMS in MongoDB) hat eine bestimmte Größe. Hat die Collection die gegebene Größe erreicht, fallen die ältesten Einträge dieser Collection heraus und werden durch neuere ersetzt. Gerade dieses Verhalten ist bei Importen oder größeren Inserts in Verbindung mit Replikation gefährlich, da die Collection schneller erneuert wird, als der Secondary replizieren kann. 

Im Grunde haben wir jetzt auf unseren drei Hosts einen mongod-Prozess laufen, über die Eingabe &#8222;mongo&#8220; in der Bash gelangen wir in die mongo-shell. Für die Replikation nehmen wir folgende Eingaben vor:
  
`` 
  
Nach einer Minute sollte sich der Eingabeprompt verändern:
  
`shard1:PRIMARY>`
  
[Primary|Secondary] signalisiert nun direkt die jeweilige Rolle des Prozesses, nur der Master nimmt im ReplicaSet nun writes entgegen. Wird der Master nun beendet findet in Election-Prozess statt, während diesem handeln die Slaves untereinander aus, wer die Master-Rolle übernimmt.