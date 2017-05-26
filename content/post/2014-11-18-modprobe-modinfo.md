---
title: modprobe, modinfo
author: markus
type: post
date: 2014-11-18T19:12:15+00:00
url: /?p=467
categories:
  - linux

---
Um Informationen über ein Modul zu erhalten genügt ein:
  
`modinfo <modulname><br />
z.b.<br />
# modinfo dummy<br />
filename:       /lib/modules/3.10.56-1-MANJARO/kernel/drivers/net/dummy.ko.gz<br />
alias:          rtnl-link-dummy<br />
license:        GPL<br />
depends:<br />
intree:         Y<br />
vermagic:       3.10.56-1-MANJARO SMP mod_unload modversions<br />
parm:           numdummies:Number of dummy pseudo devices (int)`

Um ein Modul zu laden, kann modprobe verwendet werden:
  
`# modprobe dummy numdummies=2<br />
# ip a<br />
..<br />
35: dummy0: <BROADCAST,NOARP> mtu 1500 qdisc noop state DOWN group default<br />
    link/ether fe:ec:ff:db:4d:ae brd ff:ff:ff:ff:ff:ff<br />
36: dummy1: <BROADCAST,NOARP> mtu 1500 qdisc noop state DOWN group default<br />
    link/ether ee:ee:54:9f:18:dd brd ff:ff:ff:ff:ff:ff<br />
..`

Modprobe beachtet hierbei sogar die Abhängigkeiten von Modulen. Es lassen sich auch aliase definieren (/etc/modprobe.conf &#8211; falls die Paramterliste mal zu lang werden sollte). Kernelmodule befinden sich generell unter
  
`/lib/modules/<Kernelversion>`

Das entladen von Modulen geht mit dem Parameter -r von statten:
  
`modprobe -r dummy`

siehe hierzu auch
  
man modprobe
  
man modinfo
  
man modprobe.conf