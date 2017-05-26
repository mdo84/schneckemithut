---
title: mysqldump mit single transaction
author: markus
type: post
date: 2014-08-13T11:29:49+00:00
url: /?p=436
categories:
  - mysql

---
Um während des Betriebes einen Dump ohne längeren Table-Lock zu ziehen, kann der Modus Single-Transaction verwendet werden.
  
<a href="http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html#option_mysqldump_single-transaction" title="http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html#option_mysqldump_single-transaction" target="_blank">http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html#option_mysqldump_single-transaction</a>

Hier sollte allerdings das Schema der Tabellen beachtet werden, da dies laut Doku nur mit InnoDB-Engine funktioniert:
  
`Um während des Betriebes einen Dump ohne längeren Table-Lock zu ziehen, kann der Modus Single-Transaction verwendet werden.
  
<a href="http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html#option_mysqldump_single-transaction" title="http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html#option_mysqldump_single-transaction" target="_blank">http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html#option_mysqldump_single-transaction</a>

Hier sollte allerdings das Schema der Tabellen beachtet werden, da dies laut Doku nur mit InnoDB-Engine funktioniert:
  
` 

Mit Single-Transaction wird der Table-Lock während eines mysqldump mit &#8211;master-data auf einen kleinen Zeitraum reduziert.