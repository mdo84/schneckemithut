---
title: truncaten von files
author: markus
type: post
date: 2014-01-07T07:46:36+00:00
url: /?p=197
categories:
  - Bash
  - linux

---
Um eine Files zu shrinken kann das Programm &#8222;truncate&#8220; verwendet werden: 

<pre># truncate -s 0 /var/log/messages</pre>

Die File wird dann auf 0 Byte gekürzt -> also geleert und kann somit wieder befüllt werden. Dies ist nützlich bei Log-Dateien, die evtl. nicht rotatet werden und somit einiges an Platz verbrauchen.