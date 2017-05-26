---
title: MySQL-Backup
author: markus
type: post
date: 2013-11-11T15:22:37+00:00
url: /?p=158
categories:
  - mysql

---
MySQL-Backup per mysqldump: 

<pre>mysqldump -uuser -ppassword --all-databases --events | /bin/gzip > /data/backup/all.sql.gz</pre>

Es sollten bei einem Backup gleich alle Datenbanken gesichert werden, da auch die mysql-eigene User-DB mysql damit mitgesichert wird.
  
Ein Restore erfolgt dann mit: 

<pre>zcat /data/backup/all.sql.gz | mysql -uuser -ppassword --database wordpress</pre>