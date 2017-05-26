---
title: Nagios Plugin check_tcp und haproxy
author: markus
type: post
date: 2015-12-10T21:41:25+00:00
url: /?p=554
categories:
  - Allgemein
  - linux
  - Nagios
tags:
  - check_tcp
  - Nagios
  - tcpdump

---
Ich habe mich gefragt, wie ich eine Datenbankconnection monitoren kann, die sich über einen lokalen haproxy mit einer Remotedatenbank verbindet: 

Es existiert ein Nagios Plugin, welches tcp-checks auf offene Ports von Maschinen verschicken kann.
  
`$ ./check_tcp -H localhost -p 13306 -s send_by_check_tcp`

In dem Beispiel wird von auf Host_A ein Dienst betrieben, welcher eine DB-Connection benötigt. Da mehrere Lese-DB-Hosts zur Verfügung stehen, wurde ein haproxy eingesetzt.
  
`HOST_A -> haproxy (Port 13306) ---------> DBHOST_A (Port 3306) / DBHOST_B (Port 3306)`

Checkt der check_tcp nun den offenen haproxy-Port, oder werden auch die Syn-Packages an den DB-Host weitergeleitet? 

Diesem Gedanken schafft ein tcpdump abhilfe auf einem der DB-Hosts:
  
`$ tcpdump -i eth0 -vvv -w dumpfile host HOST_A and dst port 3306`

Ergebnis:
  
Die Checks werden von haproxy durchgereicht und landen im tcpdump der DBHosts.