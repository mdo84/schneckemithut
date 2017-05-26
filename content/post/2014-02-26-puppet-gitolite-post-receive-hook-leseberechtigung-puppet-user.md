---
title: Puppet Gitolite post-receive -hook, Leseberechtigung Puppet User
author: markus
type: post
date: 2014-02-26T10:55:24+00:00
url: /?p=281
categories:
  - Allgemein

---
Die standardmäßige Umask in Gitolite-Repos (die beispielsweise mit post-receive-Hooks in Verzeichnisse gelegt werden) ist in der .gitolite.rc im Homeverzeichnis des Users Gitolite nachzuvollziehen und zu ändern: 

<pre>$REPO_UMASK = 0077;</pre>

Dies bewirkt, dass nur der User Gitolite mit rwx-Rechten auf neue Files zugreifen kann. Um quick & dirty (z.B. Puppet oder dem Rest der Welt) einen Lesezugriff zu gewähren, kann die Umask auf 

<pre>$REPO_UMASK = 0006;</pre>

geändert werden. ganz Dirty wäre eine Änderung des Checkout-Hooks in Ruby-Code um nachträglich einen chmod über den branch laufen zu lassen: 

<pre>%x{chmod -R 775 #{ENVIRONMENT_BASEDIR}/#{branchname}}</pre>

Zuletzt die einzig richtige Lösung: ACLs-Richtlinien für das Filesystem erstellen und auf die Branches für neu erstelle Files als default festlegen.