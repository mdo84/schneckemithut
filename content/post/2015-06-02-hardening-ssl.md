---
title: hardening SSL
author: markus
type: post
date: 2015-06-02T19:18:35+00:00
url: /?p=514
categories:
  - Allgemein

---
Um SSL unanfälliger zu gestalten, lohnt es sich einen Qualys-Check zu machen:
  
https://www.ssllabs.com/ssltest/

Bei der Initialen SSL-Einrichtung wird meist RC4 und SSLv3 von Qualys angemeckert, dies lässt sich mit folgenden Einstellungen richten:
  
`SSLCipherSuite EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH<br />
SSLProtocol All -SSLv2 -SSLv3<br />
SSLHonorCipherOrder On<br />
// HSTS<br />
Header always set Strict-Transport-Security "max-age=63072000; includeSubdomains; preload"<br />
Header always set X-Frame-Options DENY<br />
Header always set X-Content-Type-Options nosniff<br />
// HPKP<br />
Header always set Public-Key-Pins "pin-sha256=\"base64+primary==\"; pin-sha256=\"base64+backup==\"; max-age=5184000; includeSubDomains"`
  
Quelle: https://cipherli.st/

Nach dem Qualys-Test wird man auch gerne zur Dokumentation weitergeleitet:
  
https://raymii.org/s/tutorials/Strong\_SSL\_Security\_On\_Apache2.html

Zusätzlich habe ich mir einen Rewrite von http auf https eingerichtet, welcher im Vhost von Port 80 platziert wird:
  
   `</Directory><br />
   RewriteEngine on<br />
   ReWriteCond %{SERVER_PORT} !^443$<br />
   RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [NC,R,L]<br />
</VirtualHost>`