---
title: 'Git merge ging schief?! -> git reset –hard…'
author: markus
type: post
date: 2013-11-04T12:44:13+00:00
url: /?p=145
categories:
  - Git

---
Versionsverwaltung mit Git kann ganz schön lustig werden:
  
Heute vormittag musste ich eine Änderung in einem Branch rückgängig machen und kam leider um folgendes nicht mehr herum: 

<pre>$ git reflog
f9255a2 HEAD@{0}: pull origin integration: Fast-forward
da7176c HEAD@{1}: checkout: moving from production to integration
6e32111 HEAD@{2}: merge stage: Merge made by the 'recursive' strategy.
0cdbede HEAD@{3}: pull origin production: Fast-forward
...
$ git reset --hard da7176c
HEAD is now at da7176c blablupp</pre>

Mit &#8222;git reflog&#8220; lassen sich merges nachvollziehen und durch git reset &#8211;hard xxxxxxx rückgängig machen. Wenn man zum Beispiel die Merges eines Kollegen gar nicht in seinem Branch haben möchte, dies aber trotzdem schon gepullt hat, sieht man in &#8222;git log&#8220; nämlich nur dessen Commits ;). So hat man nun eine Möglichkeit den eigentlichen pull der Änderungen rückgängig zu machen.