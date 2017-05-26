---
title: grep vorne und hinten
author: markus
type: post
date: 2014-01-10T09:19:34+00:00
url: /?p=205
categories:
  - Bash

---
Möchte man als Ergebnis nicht nur eine einzelne Zeile des Greps als Ergebnis, sondern die folgenden oder davor stehenden Zeilen ebenfalls ausgeben lässt sich -A oder -B dafür verwenden:
  
-A NUM, &#8211;after-context=NUM
  
Print NUM lines of trailing context after matching lines. Places a line containing a group separator (&#8211;) between contiguous groups of matches. With the -o or &#8211;only-matching option, this has no effect and a warning is given.

-B NUM, &#8211;before-context=NUM
  
Print NUM lines of leading context before matching lines. Places a line containing a group separator (&#8211;) between contiguous groups of matches. With the -o or &#8211;only-matching option, this has no effect and a warning is given.
  
Usage:

<pre>grep -ir -A5 -B5 "horrido" . </pre>