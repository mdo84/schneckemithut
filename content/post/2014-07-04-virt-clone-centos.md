---
title: virt-clone Centos
author: markus
type: post
date: 2014-07-04T08:23:57+00:00
url: /?p=401
categories:
  - Centos
  - KVM

---
Beim kvm-clonen kann per Befehl eine neue MAC-Adresse mitgegeben werden:
  
`virt-clone --original cent0 --name cent1 --file /var/lib/libvirt/images/cent1.img --mac 52:54:00:57:DB:2B`

&#8222;cent0&#8220; stellt hierbei die zu kopierende VM dar, &#8222;cent1&#8220; ist die neue VM. &#8211;file gibt dabei das neue Festplattenimage an. Die neue MAC-Adresse geben wir mit &#8211;mac mit. 

Allerdings werden die Linux-Configs dadurch ja nicht geändert. Hier muss bei Redhat-Derivaten folgende File gelöscht werden
  
`# rm -f /etc/udev/rules.d/70-persistent-net.rules<br />
# reboot`

Evtl. muss dann noch die MAC-Adresse in der ifcfg-eth0 angepasst werden:
  
`# vim /etc/sysconfig/network-scripts/ifcfg-eth0`