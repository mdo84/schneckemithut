---
title: find empty-dirs
author: markus
type: post
date: 2014-02-10T10:30:16+00:00
url: /?p=265
categories:
  - Allgemein

---
So findet man im aktuellen Verzeichnis alle leeren enthaltenen Verzeichnisse. 

<pre>find . -type d -empty</pre>

Um diese leeren Verzeichnisse lassen sich auch gleich mit dem -exec Parameter wegwerfen: 

<pre>find . -type d -empty -exec rmdir {} \;</pre>