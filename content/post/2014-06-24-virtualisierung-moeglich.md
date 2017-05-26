---
title: Virtualisierung möglich?
author: markus
type: post
date: 2014-06-24T09:19:20+00:00
url: /?p=388
categories:
  - Virtualisierung

---
Um für bsp. KVM die Virtualisierung der verwendeten CPU zu checken, sollte
  
`grep -E 'vmx|svm' /proc/cpuinfo`
  
einen Output liefern. Dann kann auf der laufenden Maschine Virtualisiert werden.
  
Wird kein Output geliefert, sollte im Bios erst die Virtualisierung aktiviert werden.