---
title: Passwort Keystore in Rex
author: markus
type: post
date: 2013-11-13T07:45:40+00:00
url: /?p=169
categories:
  - Bash
  - Rex

---
Hier ein simpler Passwort-Keystore in Bash (hier allerdings in [Rex][1]-Tasks gegossen). 

<pre>desc "entschlüsseln und anzeigen des keystores";
task "decrypt", sub {
   say run "gpg --passphrase $gpg_pw --batch /data/deployment/rex/passwords/passwords.gpg";
   say run "rm -rf /data/deployment/rex/passwords/passwords.gpg";
   say run "echo keystore in /data/deployment/rex/passwords/passwords";
};

desc "verschlüsseln des keystores";
task "encrypt", sub {
   say run "gpg --passphrase $gpg_pw --batch -c /data/deployment/rex/passwords/passwords";
   say run "rm -rf /data/deployment/rex/passwords/passwords";
};
</pre>

Vielleicht kanns jemand gebrauchen.

 [1]: http://rexify.org