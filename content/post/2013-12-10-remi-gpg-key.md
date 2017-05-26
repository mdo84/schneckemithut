---
title: Remi GPG-Key
author: markus
type: post
date: 2013-12-10T09:23:52+00:00
url: /?p=185
categories:
  - Allgemein

---
Weil ich jetzt schon mehrmals nach dem GPG-Key von Remi gesucht habe: 

<pre>http://rpms.famillecollet.com/RPM-GPG-KEY-remi</pre>

Als Ergänzung: Dieser wird für das abgleichen der signierten Pakete aus dem Remi Repository verwendet. Lokal kann dieser dann eingebunden werden: 

<pre># cat /etc/yum.repos.d/remi.repo 
[remi]
name=Les RPM de remi pour Enterprise Linux 6 - $basearch
mirrorlist=http://rpms.famillecollet.com/enterprise/6/remi/mirror
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-remi</pre>