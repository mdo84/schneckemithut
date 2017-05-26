---
title: SSL-Zertifikat beantragen und erste Schritte
author: markus
type: post
date: 2014-04-03T13:27:17+00:00
url: /?p=321
categories:
  - Allgemein

---
Für meine Owncloud habe ich mir ein SSL-Zertifikat bei https://www.cacert.org besorgt.
  
Einfach der Registrierung folgen und eine Domain hinterlegen (welche noch per Email überprüft wird, man sollte also eine existierende Emailadresse dafür anlegen oder verwenden). Ein kostenloses Zertifikat ist hier dann 6 Monate gültig, kann aber danach auch noch verlängert werden. 

Dann sollte man sich mit openssl eine Zertifikatsanfrage generieren:
  
`openssl req -nodes -new -newkey rsa:2048 -out csr.pem`
  
Quelle: https://ssl-trust.com/csr-erstellen/openssl

Diese muss dann bei cacert unter Serverzertifikate -> neu reingepastet werden und man erhält kurz darauf ein Serverzertifikat angezeigt, welches man sich dann kopiert und auf dem Server hinterlegt. Für die ersten Schritte mit SSL empfiehlt sich evtl. die Standardkonfiguration der Apache / HTTPD config ( bei Centos /etc/httpd/conf.d/ssl.conf ) zu verwenden.
  
Hier die benötigten Daten wie Zertifikatspfad, Keypfad, Docroot etc. ergänzen 🙂