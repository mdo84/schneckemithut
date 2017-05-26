---
title: mknod pipe
author: markus
type: post
date: 2014-11-19T19:18:04+00:00
url: /?p=472
categories:
  - linux

---
Um eine Pipe unter Linux zu erstellen, genügt ein
  
`~/test$ mknod testpipe p<br />
~/test$ echo "hallo pipe" > testpipe<br />
~/test$ echo $$<br />
24040<br />
----------------- andere konsole<br />
~/test$ cat < testpipe<br />
hallo pipe<br />
~/test$ echo $$<br />
24134`

Der Filetype Pipe stellt eine Pipe &#8222;|&#8220; auf Dateiebene dar, die mit einem Filenamen angesprochen werden kann.
  
Mehr dazu unter
  
`~/test$ apropos fifo<br />
fifo (7)             - »first-in-first-out«-Spezialdatei (named pipe)`