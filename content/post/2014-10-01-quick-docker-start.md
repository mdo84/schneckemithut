---
title: quick docker start
author: markus
type: post
date: 2014-10-01T20:20:13+00:00
url: /?p=442
categories:
  - Docker

---
Docker installieren mit
  
`$ yum install docker-io`

Docker starten mit
  
`$ /etc/init.d/docker start || service docker start`

Docker testen
  
`$ docker info`

Docker Container erstellen
  
`$ docker run --name web01 -i -t ubuntu /bin/bash`

Stati der Container feststellen
  
`$ docker ps -a`

den Docker Command wieder aufnehmen
  
``Docker installieren mit
  
`$ yum install docker-io`

Docker starten mit
  
`$ /etc/init.d/docker start || service docker start`

Docker testen
  
`$ docker info`

Docker Container erstellen
  
`$ docker run --name web01 -i -t ubuntu /bin/bash`

Stati der Container feststellen
  
`$ docker ps -a`

den Docker Command wieder aufnehmen
  
`` 

Daemonized Docker Container starten
  
`[root@kvmhost ~]# docker run --name daemon_dave -d ubuntu /bin/sh -c "while true; do echo hello world; sleep 1; done"<br />
b2218fee08dc060f0b1e3d19f95b4adc41011c31cb9e6350729f9397b8fa5cb9<br />
[root@kvmhost ~]# docker ps<br />
CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS              PORTS               NAMES<br />
b2218fee08dc        ubuntu:latest       /bin/sh -c 'while tr   8 seconds ago       Up 7 seconds                            daemon_dave`

Container Logs ansehen (-f für tail -f)
  
`[root@kvmhost ~]# docker logs daemon_dave || docker logs -f daemon_dave<br />
hello world<br />
hello world<br />
hello world<br />
hello world`

Logs mit Timestamp
  
`[root@kvmhost ~]# docker logs --tail 3 -t daemon_dave<br />
[Oct  1 20:17:39.171] hello world<br />
[Oct  1 20:17:40.173] hello world<br />
[Oct  1 20:17:41.174] hello world`

Inspecten des Docker-Prozesses
  
`$ docker top daemon_dave`