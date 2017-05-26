---
title: erste Schritte mit btsync
author: markus
type: post
date: 2014-05-07T16:36:42+00:00
url: /?p=349
categories:
  - Allgemein

---
Um directories auf mehreren Maschinen zu syncen lohnt sich ein Blick auf btsync:
  
http://www.bittorrent.com/intl/de/sync/downloads/

Die Einrichtung eines freigegebenen Verzeichnisses ist dabei denkbar einfach (aus Linux-Sicht):
  
Package downloaden, entpacken, btsync-script starten. In den iptables Port 8888 für das Webinterface http://localhost:8888 freigeben, ein Verzeichnis anlegen (z.b. /data/btsync ), im Webinterface einen Ordner hinzufügen, Geheimschlüssel generieren und Pfad auswählen. Auf der Gegenseite muss dann nur noch der Geheimschlüssel der anderen Maschine angegeben werden, zusätzlich noch ein Verzeichnis in der die Daten gesynct werden sollen. Zusätzlich kann auch unter Schreib- und Lesemodus unterschieden werden.
  
Später kann der Port 8888 für das Webinterface auch wieder disabled werden.