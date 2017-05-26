---
title: find mit exec
author: markus
type: post
date: 2014-01-10T08:35:04+00:00
url: /?p=201
categories:
  - Bash
  - linux

---
Löschen von alten Files, z.B. Puppet-Reports mit find und exec-Funktion: 

<pre>$ sudo find . -ctime +20 -type f -exec rm {} \;</pre>

-ctime findet alle Files die n*24 Stunden nicht mehr gechanged wurden, type File und executed den remove-Befehl.
  
Praktisch, da Puppet Reportverzeichnisse für jede Maschine anlegt, darin dann für jeden durchlaufenen Run eine yaml-File ablegt.