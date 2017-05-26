---
title: mehrere Unterordner gleichzeit anlegen
author: markus
type: post
date: 2014-01-12T19:33:02+00:00
url: /?p=214
categories:
  - Bash

---
Und so kann man mehrere Unterordner gleichzeitig anlegen: 

<pre>mkdir pfad/{files,manifests,templates}</pre>

In diesem Beispiel für ein neues Puppet-Modul &#8222;pfad&#8220; mit Unterordnern files, manifests und templates. Sollte mkdir nicht quengeln, wenn die Ordner bereits bestehen, kann mkdir auch mit dem Parameter -p aufgerufen werden.