---
title: lokales yumrepo
author: markus
type: post
date: 2014-06-17T09:45:32+00:00
url: /?p=378
categories:
  - Centos
  - linux

---
Um ein lokales yum-repo zu erstellen, benötigt man &#8222;createrepo&#8220;.
  
`/data/yumrepo# createrepo --database /data/yumrepo</p>
<p>Saving Primary metadata<br />
Saving file lists metadata<br />
Saving other metadata<br />
Generating sqlite DBs<br />
Sqlite DBs complete`

`# cat /etc/yum.repos.d/localrepo.repo<br />
[localrepo]<br />
name=localrepo for php-testing<br />
baseurl=file:/data/yumrepo/<br />
enabled=1<br />
gpgcheck=0`

Danach noch Pakete ins Repo schieben und &#8222;yum makecache&#8220; ausführen. Nun könnte man zusätzlich noch die Priorität des Repos anpassen, falls man die selben Pakete anbieten möchte (nur eben lokal).
  
`# cat /etc/yum.repos.d/localrepo.repo<br />
[localrepo]<br />
name=localrepo for php-testing<br />
baseurl=file:/data/yumrepo/<br />
enabled=1<br />
priority=1<br />
gpgcheck=0`
  
Alternativ bieten wir nun das Remi-Repo mit anderer Priorität an:
  
`# cat /etc/yum.repos.d/remi.repo<br />
[remi]<br />
name=Les RPM de remi pour Enterprise Linux 6 - $basearch<br />
mirrorlist=http://rpms.famillecollet.com/enterprise/6/remi/mirror<br />
enabled=1<br />
gpgcheck=1<br />
priority=2<br />
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-remi`

Per yumdownloader könnte man nun ein Paket aus dem remi-Repo downloaden, im localrepo speichern, createrepo nochmals ausführen und den Cache von yum per makecache auffrischen. Installiert man nun dieses Paket per yum, wird dies anstelle des Remi-Repos gewählt, die Dependencies allerdings aus dem Remi, wenn sie nicht im localrepo liegen:
  
`Installing:<br />
 php-fpm                   x86_64            5.4.29-3.el6.remi            localrepo          1.3 M<br />
Updating for dependencies:<br />
 php                       x86_64            5.4.29-3.el6.remi            remi               2.7 M<br />
 php-cli                   x86_64            5.4.29-3.el6.remi            remi               2.6 M`