---
title: yumdownloader – pakete aus repos downloaden
author: markus
type: post
date: 2014-04-29T19:20:12+00:00
url: /?p=335
categories:
  - Bash
  - linux
tags:
  - yum
  - yumdownloader

---
Um Pakete direkt von Repositorys herunterzuladen, kann yumdownloader verwendet werden. Dies sollte allerdings mit Root-Rechten ausgeführt werden, damit auch alle Repositories berücksichtig werden:
  
`sudo yumdownloader php-5.4.24-1.el6.remi.x86_64`