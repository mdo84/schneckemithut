---
title: Jenkins safeRestart
author: markus
type: post
date: 2013-11-12T15:21:48+00:00
url: /?p=166
categories:
  - Jenkins

---
Jenkins (die in einem Java Servelettcontainer lauffähigen Application) kann auch per Weboberfläche restartet werden (per Configurationsmenu ist nur &#8222;prepare for Shutdown&#8220; ansurfbar): 

<pre>http://&lt;jenkins-kiste>:8080/jenkins/safeRestart = warten auf beenden der jobs, sicherer neustart folgt
http://&lt;jenkins-kiste>:8080/jenkins/restart = force restart, ohne auf builds zu warten</pre>