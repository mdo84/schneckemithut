---
title: Webcaching mit Varnish
author: markus
type: post
date: 2013-10-14T11:07:08+00:00
url: /?p=27
categories:
  - Varnish

---
Der Einsatz eines Webcaches wie Varnish beschleunigt Websites ungemein.
  
Hierbei werden statische Inhalte einer Website bereits in den Arbeitsspeicher des Webcaches geladen und bei Bedarf (HTTP-Anfragen von Usern) ausgeliefert. Hierbei kann Varnish auch einiges an Last bereits abfangen, ohne dass der dahinter stehende Webserver davon überhaupt Wind bekommt (z.B. Anfragen auf Startseiten oder statischen Inhalt). Guter Artikel über Varnish Webcaching: [http://blog.mgm-tp.com/2012/01/varnish-web-cache/][1]

Varnish lässt sich sowohl direkt auf dem Webserver als auch als zusätzliche Maschine betreiben.
  
Anleitung zur Installation eines Varnish-Webcaches:
  
[https://www.varnish-cache.org/docs/3.0/installation/index.html][2]

Gute Anleitung zum initialisierten Start eines Varnishs mit Memoryallocation (wieviel Arbeitsspeicher soll Varnish verwenden) und Configpfad (welche VCLs soll Varnish laden):
  
[https://www.varnish-cache.org/docs/3.0/tutorial/starting_varnish.html][3]

 [1]: http://blog.mgm-tp.com/2012/01/varnish-web-cache/ "http://blog.mgm-tp.com/2012/01/varnish-web-cache/"
 [2]: https://www.varnish-cache.org/docs/3.0/installation/index.html "https://www.varnish-cache.org/docs/3.0/installation/index.html"
 [3]: https://www.varnish-cache.org/docs/3.0/tutorial/starting_varnish.html "https://www.varnish-cache.org/docs/3.0/tutorial/starting_varnish.html"