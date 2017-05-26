---
title: Prozesshandling Linux
author: markus
type: post
date: 2013-10-28T09:00:17+00:00
url: /?p=126
categories:
  - Bash
  - linux

---
Laufende Prozesse lassen sich aus der Shell in den Hintergrund versetzen. Zunächst muss der Job mit STRG + Z pausiert werden: 

<pre>markusd@lap-mdollinger01:~$ sleep 500
^Z
[1]+  Stopped                 sleep 500
markusd@lap-mdollinger01:~$ bg
[1]+ sleep 500 &
markusd@lap-mdollinger01:~$ jobs -l
[1]+  1341 Running                 sleep 500 &
markusd@lap-mdollinger01:~$ fg 1
sleep 500
^C
markusd@lap-mdollinger01:~$ 
</pre>

Durch &#8222;bg&#8220; wird der letzte pausierte Job in den Hintergrund geschoben. Mit &#8222;jobs -l&#8220; werden die laufenden Hintergrundprozesse angezeigt, durch -l auch mit Prozess-ID. Das Programm &#8222;fg&#8220; holt mit dem Parameter der Job-Nummer den Prozess wieder in den Vordergrund.