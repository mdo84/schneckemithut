---
title: Rex-Tasks ausblenden
author: markus
type: post
date: 2014-01-13T08:17:12+00:00
url: /?p=223
categories:
  - Allgemein

---
<a href="http://rexify.org" title="Rexify" target="_blank">Rex</a>-Tasks können mit folgendem Code aus der Ansicht -T (verfügbare Tasks) ausgeblendet werden: 

<pre>$Rex::Commands::Dont_register_tasks = TRUE;
task "auszublendendertask", group => "myservergroup", sub {
   # irgend ein foo
};
$Rex::Commands::Dont_register_tasks = FALSE;</pre>

Dieser Task taucht dann nicht mehr in der Übersicht 

<pre>rex -T</pre>

auf, kann aber trotzdem noch in Transactions verwendet werden.