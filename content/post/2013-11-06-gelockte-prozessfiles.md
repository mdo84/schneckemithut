---
title: Gelockte Prozessfiles – die Zombies kommen!
author: markus
type: post
date: 2013-11-06T15:42:34+00:00
url: /?p=153
categories:
  - Bash
  - linux

---
Oladida, gerade mit nem yum-Prozess gekämpft der als Zombie ([hier was zum Lesen][1]) durch die Gegend lief. 

<pre>$ ps aux| grep yum
root     22009 25.5  0.0      0     0 ?        Zs   14:59  22:22 [yum] &lt;defunct>
5295     32747  0.0  0.0 103248   812 pts/1    S+   16:26   0:00 grep yum</pre>

Mein Chef brachte dann die Erlösung: 

<pre>$ pstree
---------8&lt;-----------
     ├─puppetd───yum
---------8&lt;-----------  
$ sudo /etc/init.d/puppet restart
Stopping puppet:                                           [FAILED]
Starting puppet:                                           [  OK  ]
---------8&lt;----------- 
$ pstree
     ├─puppetd
---------8&lt;-----------
$ ps aux | grep yum
5295       778  0.0  0.0 103244   804 pts/1    S+   16:28   0:00 grep yum</pre>

CHEER!

 [1]: http://www.techfak.uni-bielefeld.de/ags/rbg/de/rechner-unix-zombie.html