---
title: Umask, Berechtigungen, Links…
author: markus
type: post
date: 2013-11-12T09:39:34+00:00
url: /?p=160
categories:
  - linux

---
Hier noch fix ein Nachtrag &#8211; gerade habe ich mich ein wenig mit Themen beschäftigt, weil ein paar Verzeichniseinstellungen auf einer Büchse nicht getan haben.
  
Links gibt es in zwei Varianten: Hardlinks (linked direkt auf den Inode einer Datei, sozusagen sind alle Dateien Hardlinks) und Softlinks (auch Symlink genannt; das OS erkennt einen Softlink und leitet den User zur Datei weiter). 

<pre>Hardlink: 
$: ln datei link</pre>

<pre>Softlink: 
$: ln -s datei symlink</pre>

Hier eine Übersicht zu den allgemeinen Berechtigungen unter Linux:
  
http://openbook.galileocomputing.de/linux/linux\_kap14\_001.html#dodtp5deaea2c-6f73-4e59-81b0-a58d65db00b9

Die Umask beschreibt die Standardrechte für eine neu erstelle Datei, die eine Datei allerdings nicht erhält. Dies in Octalwerten: 

<pre>$: umask
0022
$: umask 0002
$: umask
0002</pre>

Hier erhält die Gruppe also nicht schreiben und Others nicht schreiben (also 0755).