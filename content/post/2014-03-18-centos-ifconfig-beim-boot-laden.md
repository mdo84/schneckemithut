---
title: CentOS – ifconfig beim Boot laden
author: markus
type: post
date: 2014-03-18T13:55:33+00:00
url: /?p=308
categories:
  - Allgemein

---
Möchte man auch nach dem Booten noch eine funktionierende Netzwerkverbindung haben, lohnt es sich mal in die ifcfg-ethX (in meinem Fall eth0) zu gucken: 

`$ vi /etc/sysconfig/network-scripts/ifcfg-eth0<br />
DEVICE=eth0<br />
BOOTPROTO=static<br />
HWADDR=50:E5:49:C4:5E:75<br />
TYPE=Ethernet<br />
UUID=d34265ca-b12e-42d7-ba8f-56cb727a3900<br />
ONBOOT=yes<br />
NM_CONTROLLED=yes<br />
BROADCAST=192.168.178.255<br />
IPADDR=192.168.78.23<br />
NETWORK=192.168.178.0`