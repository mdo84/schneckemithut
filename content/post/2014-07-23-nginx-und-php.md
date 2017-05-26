---
title: nginx und php
author: markus
type: post
date: 2014-07-23T14:19:03+00:00
url: /?p=421
categories:
  - Nginx

---
Grundsätzlich arbeitet Nginx gut in der Auslieferung mit statischem Content. Allerdings lässt sich auch eine PHP-Schnittstelle über fastcgi hinzufügen: 

`/etc/nginx/conf.d/# vi default.conf<br />
    location ~ \.php$ {<br />
        fastcgi_pass   127.0.0.1:9000;<br />
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;<br />
        include        fastcgi_params;<br />
    }`

Zusäztlich sollte php-fpm mit php-common als Abhängigkeit installiert sein. Um künftig weitere Fallstricke zu vermeiden, empfiehlt sich auch <a href="http://wiki.nginx.org/Pitfalls" title="Nginx Pitfalls" target="_blank">dies</a>.
  
Ausgeliefert wird nginx mit einer anderen Config:
  
    `#location ~ \.php$ {<br />
    #    root           html;<br />
    #    fastcgi_pass   127.0.0.1:9000;<br />
    #    fastcgi_index  index.php;<br />
    #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;<br />
    #    include        fastcgi_params;<br />
    #}`

Wobei hier der fastcgi\_param SCRIPT\_FILENAME auf $docroot/scripts zeigt. Wenn dieser nicht vorhanden ist, wird dieser Error in der nginx.conf ausgeworfen:
  
`2014/07/23 15:07:49 [error] 1688#0: *13 FastCGI sent in stderr: "Primary script unknown" while reading response header from upstream, client: 192.168.122.1, server: _, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "192.168.122.82"`
  
Daher sollte dieser Pfad unbedingt angepasst werden (siehe erster Codeschnippsel und Dokument &#8222;Nginx Pitfalls&#8220;).