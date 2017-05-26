---
title: Vhosts in Apache
author: markus
type: post
date: 2014-02-22T17:36:54+00:00
url: /?p=282
categories:
  - Allgemein

---
Generell sollte (ich verwende hier einen httpd) eine zusätzliche config-File für einen Vhost unter /etc/httpd/conf.d abgelegt werden, diese kann dann folgende Daten enthalten (Beispiel): 

`NameVirtualHost *:80<br />
<VirtualHost *:80><br />
    ServerAdmin admin@irgendnedomain<br />
    DocumentRoot /var/www/domainpfad<br />
    Servername meinedomain.de<br />
    ErrorLog /var/log/domainpfad/error_log<br />
    LogLevel warn<br />
    CustomLog /var/log/domainpfad/access_log combined<br />
    ServerSignature Off</p>
<p>    <Directory /><br />
        Options FollowSymLinks<br />
        AllowOverride None<br />
    </Directory></p>
<p>    <Directory /var/www/domainpfad><br />
        Options Indexes FollowSymLinks<br />
        AllowOverride None<br />
        Order allow,deny<br />
        allow from all<br />
    </Directory></p>
<p>    ScriptAlias /cgi-bin/ /var/www/cgi-bin/</p>
<p>    <Directory "/var/www/cgi-bin"><br />
        AllowOverride None<br />
        Options +ExecCGI +SymLinksIfOwnerMatch<br />
        Order allow,deny<br />
        Allow from all<br />
    </Directory><br />
</VirtualHost>`

Wobei zu beachten wäre, dass
  
`NameVirtualHost *:80`
  
generell das Virtual Hosting einschaltet und auch in der Hauptconfig-File httpd.conf bzw. apache2.conf gut aufgehoben ist. Grundsätzlich sollten die aufgeführten Ports (:80) auch als Listen-Directive in der Hauptconfig-File angegeben sein.