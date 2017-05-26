---
title: MySQL im Master-/Master-Setup
author: markus
type: post
date: 2014-04-03T08:37:57+00:00
url: /?p=317
categories:
  - mysql

---
Für eine Master-/Master-Replikation sollte ein Loadbalancer eingesetzt werden, der den write-Port (3306) auf EINE Maschine balanced. Bei Bedarf kann dann dieser geschwenkt werden und man kann weiterhin schreibend auf die Datenbank zugreifen.
  
Alternativ sollten Autoinkrement-Inhalte auf die Master aufgeteilt werden, bsp. ungerade auf einen Knoten, gerade auf einen anderen Knoten.

Für die Replikation an sich lassen sich Datenbanken masterseitig ausschließen:

Dies wurde durch die my.cnf-Parameter
  
`binlog_ignore_db = dbname0<br />
binlog_ignore_db = dbname1<br />
binlog_ignore_db = dbname2`
  
realisiert.

Durch den Parameter binlog\_ignore\_db werden erst gar keine Daten in das binlog geschrieben. Sollte nur ein Slave (von mehreren) keine Daten bestimmter Datenbanken bekommen, ist auf
  
dem Slave der Parameter replication\_ignore\_db die richtige Wahl.

Es wurde ein Dump auf dem aktiven Master erstellt:
  
`mysqldump -udumpuser -p --add-drop-database --databases database1 database2 --master-data=1 | /usr/bin/gzip dumpfile.sql.tar.gz`
  
Master-data erfasst die Log-File und Log-Pos.

Der Dump muss dann in den Slave eingespielt werden:
  
`mysql -udbadmin -p < zcat dumpfile.sql.tar.gz`
  
oder
  
`zcat dumpfile.sql.tar.gz | mysql -udbadmin -p`

Bei der Ersteinrichtung der Replikation muss nur noch ein
  
`CHANGE MASTER TO MASTER_HOST='master.domain.de' MASTER_USER='replicationuser' MASTER_PASSWORD='replicationpassword' MASTER_LOG_FILE='mysql-binlog.XXXXXX' MASTER_LOG_POS=XXXXXX;`
  
angegeben werden. Diese Log-File-Daten lassen sich aus der Sicherung auslesen:
  
`zcat dumpfile.sql.tar.gz | head -n 30`

Zuletzt muss auf dem Slave noch die Replikation gestartet werden:
  
`mysql> START SLAVE;`