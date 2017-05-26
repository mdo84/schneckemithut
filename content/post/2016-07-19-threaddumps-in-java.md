---
title: Threaddumps in Java
author: markus
type: post
date: 2016-07-19T06:47:36+00:00
url: /?p=604
categories:
  - Allgemein

---
Threaddumps können mit einem kill -3 erstellt werden, dabei werden diese in das Log der Applikation geschrieben &#8211; bei einem Tomcat mit Tanuki-wrapper beispielsweise in das wrapper.log
  
`kill -3 PID`

Zusätzlich lässt sich mit JDK-Boardmitteln ein Threaddump in ein File schreiben:
  
`jstack -l PID > AUSGABEFILE.out`

jstack ist Teil des Java JDKs und befindet sich im Binary-Ordner des JDKs.