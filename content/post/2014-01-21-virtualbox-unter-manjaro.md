---
title: VirtualBox unter Manjaro
author: markus
type: post
date: 2014-01-21T12:51:03+00:00
url: /?p=255
categories:
  - Manjaro

---
Für VirtualBox wird zusätzlich noch der vboxdrv benötigt: 

<pre>$ sudo modprobe vboxdrv 
--------8&lt;---------
$ lsmod | grep vbox
vboxpci                14581  0 
vboxnetflt             17676  0 
vboxnetadp             18323  0 
vboxdrv               265850  3 vboxnetadp,vboxnetflt,vboxpci</pre>

Dies wird allerdings auch bei der Installation von VirtualBox angezeigt.