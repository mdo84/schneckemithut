---
title: MySQL-Upgrade
author: markus
type: post
date: 2013-12-10T09:59:36+00:00
url: /?p=182
categories:
  - linux
  - mysql

---
MySQL-Version updaten (in meinem Fall von 5.1.xx auf 5.5.35-1): 

<pre>~# yum list mysql-server
Installed Packages
mysql-server.i686
5.1.69-1.el6_4                                        @updates
Available Packages
mysql-server.i686
5.5.35-1.el6.remi                                     remi </pre>

Upgrade starten mit 

<pre>~# yum upgrade mysql-server</pre>

Dann mal den MySQL-Server starten

<pre>~# /etc/init.d/mysqld start
mysqld starten:                                            [  OK  ]</pre>

Und in den Logs noch nach Fehlern schauen: 

<pre>~# less /var/log/mysqld.log</pre>

Hier wurde bei mir nun folgendes vermerkt: 

<pre>...
131210  9:28:23 [Note] Server socket created on IP: '0.0.0.0'.
131210  9:28:23 [ERROR] Missing system table mysql.proxies_priv; please run mysql_upgrade to create it
131210  9:28:23 [ERROR] Native table 'performance_schema'.'events_waits_current' has the wrong structure
...</pre>

Also tun wir das doch mal: 

<pre>~# mysql_upgrade -uroot -p</pre>

das Passwort für den root-user noch eingeben und den mysqld nochmal neu starten. Folgendes führt mysql_upgrade eigentlich genau durch: 

<pre>mysqlcheck --all-databases --check-upgrade --auto-repair
           mysql &lt; fix_priv_tables
           mysqlcheck --all-databases --check-upgrade --fix-db-names --fix-table-names</pre>