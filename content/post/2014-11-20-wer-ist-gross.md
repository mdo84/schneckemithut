---
title: wer ist groß?
author: markus
type: post
date: 2014-11-20T18:27:08+00:00
url: /?p=483
categories:
  - Allgemein

---
Welche Verzeichnisse verbrauchen am meisten Speicherplatz?
  
`# df -hx / | sort -h<br />
130M	/lib<br />
197M	/usr/share<br />
230M	/usr/lib<br />
557M	/usr<br />
820M	/`

Alternativ dazu können auch folgende Varianten verwendet werden:
  
`# du -sch * | sort -h<br />
# du -H --max-depth=1 | sort -nr`