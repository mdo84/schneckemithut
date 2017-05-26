---
title: OpenVPN unter Manjaro
author: markus
type: post
date: 2014-01-21T11:13:11+00:00
url: /?p=252
categories:
  - Allgemein

---
Da ich neulich auf Manjaro gewechselt bin, hier noch ein Hinweis:
  
Für OpenVPN sollte (je nach Verbindungskonfiguration) per

<pre>modprobe tun</pre>

der tun/tap-device-driver nachgeladen werden.
  
Lektüre <a href="https://wiki.archlinux.de/title/OpenVPN" title="https://wiki.archlinux.de/title/OpenVPN" target="_blank">hier</a> und <a href="https://www.kernel.org/doc/Documentation/networking/tuntap.txt" title="https://www.kernel.org/doc/Documentation/networking/tuntap.txt" target="_blank">da</a>.