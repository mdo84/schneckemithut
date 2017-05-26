---
title: htpasswd – htaccess bei nginx erstellen
author: markus
type: post
date: 2013-10-31T08:25:57+00:00
url: /?p=143
categories:
  - Allgemein

---
Der htaccess bei nginx läuft ein wenig anders als bei Apache. Eine kleine Einführung der Unterschiede findet man <a href="http://www.kuketz-blog.de/htaccess-schutz-wordpress-absichern-teil4/" title="htaccess" target="_blank">hier</a>. Möchte man nun das Password nicht in Plain text irgendwo hinterlegen, oder beispielsweise den htaccess auch über varnish machen, kann man sich mit den htpasswd-tools ein verschlüsseltes Kennwort erstellen: 

<pre>$ htpasswd -c neues_file user
New password: 
Re-type new password: 
Adding password for user user
&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;
$ cat neues_file 
user:cvUZLg4DYNh3M</pre>