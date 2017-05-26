---
title: Centos ipv6’en
author: markus
type: post
date: 2014-05-23T07:06:17+00:00
url: /?p=368
categories:
  - Centos
  - linux

---
Um Centos eine globale ipv6-Adresse in die Hand zu drücken, bedarf es folgender Schritte: 

`$ cat > /etc/sysconfig/network << EOF<br />
NETWORKING_IPV6=yes<br />
EOF<br />
$ vi /etc/sysconfig/network-scripts/ifcfg-eth0<br />
IPV6INIT=yes<br />
IPV6ADDR=<IPv6-Adresse><br />
IPV6_DEFAULTGW=<IPv6-Gateway-Adresse>`

Die Adresse kann frei gewählt werden, z.B. bei einem /64 Präfix:
  
0000:0000:0000:0000 / 64
  
-> xxx:xxxx:xxxx:xxxx:0000:0000:0000:0001
  
Gateway sollte auch nur eingetragen werden, falls man eines vom Provider zugewiesen bekommt. 

Danach noch Service restarten
  
`$ service network restart`

Danach sollte ein Ping per ipv6 möglich sein:
  
`# ping6 ipv6.google.com<br />
PING ipv6.google.com(muc03s08-in-x02.1e100.net) 56 data bytes<br />
64 bytes from muc03s08-in-x02.1e100.net: icmp_seq=1 ttl=58 time=10.1 ms<br />
64 bytes from muc03s08-in-x02.1e100.net: icmp_seq=2 ttl=58 time=10.2 ms<br />
64 bytes from muc03s08-in-x02.1e100.net: icmp_seq=3 ttl=58 time=10.2 ms<br />
64 bytes from muc03s08-in-x02.1e100.net: icmp_seq=4 ttl=58 time=10.2 ms<br />
...`

Alternativ-Lesestoff:
  
http://www.cyberciti.biz/faq/rhel-redhat-fedora-centos-ipv6-network-configuration/
  
http://www.cyberciti.biz/faq/ipv6-apache-configuration-tutorial/

PS: Sollte sich ein Ergebnis nach den vhost-Einstellungen nicht direkt einstellen, kann dies auch an Browser-Einstellungen liegen. Beispielsweise verwendet Firefox einen Fallback auf ipv4:
  
Browser-Adresszeile: about:config

network.http.fast-fallback-to-IPv4;true
  
-> abändern auf false
  
Browser neu starten

Testing mit ipv6 und Browser-Plugins:
  
https://addons.mozilla.org/en-US/firefox/addon/ipvfox/
  
https://chrome.google.com/webstore/detail/ipvfoo/ecanpcehffngcegjmadlcijfolapggal