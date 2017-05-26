---
title: default ACLs entfernen
author: markus
type: post
date: 2013-12-09T12:01:10+00:00
url: /?p=172
categories:
  - Bash
  - linux

---
Nunja, wir haben gerade versucht default-ACLs von Verzeichnissen zu entfernen. Die nötige Magic war dann anders als gedacht

<pre>folgende Versuche ergaben KEINE Lösung: 
/usr/bin/setfacl -R -dm g:die-gruppe:rwX /weg/zum/verzeichnis
/usr/bin/setfacl -R -x g:die-gruppe:rwX /weg/zum/verzeichnis
/usr/bin/setfacl -Rx default:group:die-gruppe:rwX /weg/zum/verzeichnis
/usr/bin/setfacl -x default:group:die-gruppe:rwX /weg/zum/verzeichnis</pre>

Tja, RTFM bringt die Lösung: 

<pre>/usr/bin/setfacl -Rk /weg/zum/verzeichnis</pre>

Wobei hier -R für rekursiv steht, -k für das Entfernen der Default-ACLs.