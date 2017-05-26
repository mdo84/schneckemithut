---
title: 'WordPress als Keksfabrik  & einfache Lasttests auf Webseiten'
author: markus
type: post
date: 2013-10-21T12:09:12+00:00
url: /?p=43
categories:
  - Varnish

---
Durch mein Testing mit Varnish und WordPress möchte ich hier den Unterschied zwischen einem kleinen Webauftritt ohne und mit Varnish Webcache zeigen. Grundsätzlich verwendet WordPress eine Menge [Cookies][1]. Diese sind für das Webcaching tödlich, da jede Request eines Clients dann an den Webserver weitergereicht und nicht aus dem Cache gezogen wird. Hierbei kann schonmal eine Trefferquote (Hitrate auf den Cache) von 0 zusammen kommen. Ich möchte das mit einem Lasttest mal ausprobieren: 

Einfache (und schnelle) Lasttests lassen sich mit Blazemeter (http://www.blazemeter.com) durchführen. Blazemeter nutzt [JMeter von Apache][2]. Einfach testen und ausprobieren lassen sich diese mit einem Testaccount und einem Lasttest von 50 Usern. Durch eine kurze Anleitung wird der User durch die Funktionen geführt und erhält am Ende einen Status-Bericht. Laut Angaben des Anbieters lassen sich so Lasttests bis 100.000 User durchführen. Gemäß den JMeter-Standards lassen sich auch eigene Scripte integrieren.
  
Während des Tests lässt sich das Log und auch ein aktueller Status des Lasttests (Loadresults wie active user, max users, response time) sowie ein Ergebnis des Lasttests ausgeben. Den Log kann man anschließend auch herunterladen.
  
Gerade für größere Auftritte lohnt sich so ein Test um einen Ansturm von Usern zu testen oder die theoretische Auslastung eines Auftritts zu kennen. Entspricht das Ergebnis dann nicht den Erwartungen, kann die Infrastruktur noch hochskaliert werden.
  
Hier der Lasttest mit 50 Usern ohne den Einsatz eines Webcaches bzw. mit Standardeinstellungen im Varnish und aktivierten Cookies: 

[<img src="http://schneckemithut.de/wp-content/uploads/2013/10/beitrag4.png" alt="ohne Varnish" width="990" height="494" class="alignnone size-full wp-image-53" />][3] 

Dies ist das Ergebnis eines Lasttests mit Varnish Webcache (mit deaktivierten Cookies = Cookies werden vom Varnish entfernt, Auslieferung direkt aus dem Cache). Tipps hierzu [hier][4] und [da][5].

[<img src="http://schneckemithut.de/wp-content/uploads/2013/10/beitrag1.png" alt="beitrag1" width="987" height="491" class="alignnone size-full wp-image-50" />][6]

Interessant ist die response Time (grün) der Website bei steigender Nutzerzahl (blau) welche sich mit richtiger Varnishkonfiguration kaum zu ändern scheint, mit steigender Nutzerzahl sogar konstanter wird).

 [1]: http://de.wikipedia.org/wiki/Cookie "Cookies"
 [2]: http://de.wikipedia.org/wiki/Apache_JMeter "JMeter von Apache"
 [3]: http://schneckemithut.de/wp-content/uploads/2013/10/beitrag4.png
 [4]: https://www.varnish-cache.org/trac/wiki/VarnishAndWordpress "hier"
 [5]: https://www.varnish-cache.org/trac/wiki/VCLExampleCacheCookies "da"
 [6]: http://schneckemithut.de/wp-content/uploads/2013/10/beitrag1.png