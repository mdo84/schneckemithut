---
title: PHP Newrelic-Daemon
author: markus
type: post
date: 2014-01-21T09:07:30+00:00
url: /?p=243
categories:
  - Allgemein

---
Der Newrelic-Daemon kann automatisch durch PHP gestartet werden. Diese Option findet sich in der Newrelic.ini für PHP: 

<pre>; Setting: newrelic.daemon.dont_launch
; Type   : integer (0, 1, 2 or 3)
; Scope  : system
; Default: 0
; Info   : If you prefer to have the daemon launched externally before the
;          agent starts up, set this variable to non-zero. The value you
;          choose determines exactly when the agent is allowed to start the
;          daemon:
;          0 - agent can start the daemon any time it needs to
;          1 - non-CLI (i.e Apache / php-fpm) agents can start the daemon
;          2 - only CLI agents can start the daemon
;          3 - the agent will never start the daemon
;
newrelic.daemon.dont_launch = 3</pre>

Je nach Wunsch (in diesem Fall &#8222;bitte bloß nicht starten&#8220;) kann die Option dann gesetzt werden.