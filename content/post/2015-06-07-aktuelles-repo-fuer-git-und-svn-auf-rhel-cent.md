---
title: aktuelles Repo für git und svn auf RHEL / CENT
author: markus
type: post
date: 2015-06-07T19:47:19+00:00
url: /?p=531
categories:
  - Allgemein

---
Da unter CentOS Packages für SVN und Git nicht gerade mit Aktualität glänzen, teste ich gerade das Wandisco Repo:
  
`#http://blog.hgomez.net/2015/02/26/CentOSRHEL-and-up-to-date-Subversion-and-Git.html<br />
#Wandisco-Git.repo<br />
[wandisco-Git]<br />
name=CentOS-6 - Wandisco Git<br />
baseurl=http://opensource.wandisco.com/centos/6/git/$basearch/<br />
enabled=1<br />
gpgcheck=1<br />
gpgkey=http://opensource.wandisco.com/RPM-GPG-KEY-WANdisco`