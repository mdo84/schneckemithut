---
title: weiteres in bash
author: markus
type: post
date: 2014-06-16T06:32:05+00:00
url: /?p=376
categories:
  - Bash

---
hier noch ein paar weitere Dinge die evtl. mit der Bash hilfreich sind:
  
brace-extension
  
`test$ touch {1..10}.txt<br />
test$ ll<br />
drwxr-xr-x 2 markusd users 4096 16. Jun 10:27 ./<br />
drwxr-xr-x 8 markusd users 4096 16. Jun 10:27 ../<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 1.txt<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 10.txt<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 2.txt<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 3.txt<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 4.txt<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 5.txt<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 6.txt<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 7.txt<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 8.txt<br />
-rw-r--r-- 1 markusd users    0 16. Jun 10:27 9.txt`

Debuggen von shell-scripten mit &#8220; sh -x #scriptname# &#8220;
  
`$ ./test.sh<br />
5<br />
hurra wir sind da!`
  
Ausgabe mit debugging-infos:
  
`$ sh -x test.sh<br />
+ echo 5<br />
5<br />
+ hurra='hurra wir sind da!'<br />
+ [[ ! -z hurra wir sind da! ]]<br />
+ echo hurra wir sind 'da!'<br />
hurra wir sind da!`