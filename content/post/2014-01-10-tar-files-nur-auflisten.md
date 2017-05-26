---
title: tar-files nur auflisten
author: markus
type: post
date: 2014-01-10T09:53:07+00:00
url: /?p=209
categories:
  - Bash

---
Tar-Files einfach nur auflisten, ohne direkt zu entpacken mit 

<pre>tar -tvf horrido_file.tar.gz </pre>

Ausgabe kann dann z.B. direkt auch gegrept werden mit 

<pre>tar -tvf horrido_file.tar.gz | grep -ir "horrido_text_den_ich_suche"</pre>