---
title: Nachtrag zu htaccess
author: markus
type: post
date: 2014-07-14T11:41:14+00:00
url: /?p=418
categories:
  - Allgemein

---
Hat man bei einem Apache Zugriff auf die Vhost-Conf, bietet sich die Authentifikationsdefinition direkt in der Vhost-Conf an: 

    `<Directory /var/www/www-vhostf00bar><br />
        Options +FollowSymLinks +Multiviews +Indexes<br />
        AllowOverride None<br />
        AuthType basic<br />
        AuthName "private"<br />
        AuthUserFile /etc/httpd/.htpasswd<br />
        Require valid-user<br />
    </Directory>`

Die Passwort-File kann dann mit
  
``Hat man bei einem Apache Zugriff auf die Vhost-Conf, bietet sich die Authentifikationsdefinition direkt in der Vhost-Conf an: 

    `<Directory /var/www/www-vhostf00bar><br />
        Options +FollowSymLinks +Multiviews +Indexes<br />
        AllowOverride None<br />
        AuthType basic<br />
        AuthName "private"<br />
        AuthUserFile /etc/httpd/.htpasswd<br />
        Require valid-user<br />
    </Directory>`

Die Passwort-File kann dann mit
  
`` 
  
erstellt werden. Vorsicht: Das Passwort ist dann immernoch auf der Konsole im Klartext sichtbar (History etc. ).