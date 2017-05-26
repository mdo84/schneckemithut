---
title: darfs ein bischen Tee sein?
author: markus
type: post
date: 2014-06-20T08:08:47+00:00
url: /?p=383
categories:
  - Bash

---
Die Ausgabe von Prozessen oder Crons der Bash auf mehrere Logfiles verteilen mit dem Programm &#8222;tee&#8220;:
  
`test$ cat test.sh<br />
#!/bin/bash<br />
echo "wir sind das volk" | tee logfile1.log logfile2.log<br />
test$ ./test.sh<br />
wir sind das volk<br />
test$ ll<br />
insgesamt 20<br />
drwxr-xr-x 2 markusd users 4096 20. Jun 12:06 ./<br />
drwxr-xr-x 8 markusd users 4096 16. Jun 10:27 ../<br />
-rw-r--r-- 1 markusd users   18 20. Jun 12:06 logfile1.log<br />
-rw-r--r-- 1 markusd users   18 20. Jun 12:06 logfile2.log<br />
-rwxr--r-- 1 markusd users   72 20. Jun 12:06 test.sh*<br />
test$ cat logfile1.log logfile2.log<br />
wir sind das volk<br />
wir sind das volk`