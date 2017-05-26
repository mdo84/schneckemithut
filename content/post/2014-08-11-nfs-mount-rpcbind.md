---
title: 'nfs-mount & rpcbind'
author: markus
type: post
date: 2014-08-11T13:11:27+00:00
url: /?p=431
categories:
  - Centos
  - linux

---
Sollte ein nfs-Mount auf einem Centos-minimal mal nicht direkt funktionieren, liegt dies evtl. am rpcbind-Dienst:
  
`[root@fe01 ~]# /etc/init.d/nfs start<br />
NFS-Dienste starten:                                       [  OK  ]<br />
NFS-mountd starten:                                        [FEHLGESCHLAGEN]<br />
NFS-Daemon starten: rpc.nfsd: writing fd to kernel failed: errno 111 (Connection refused)<br />
rpc.nfsd: unable to set any sockets for nfsd<br />
                                                           [FEHLGESCHLAGEN]</p>
<p>[root@fe01 ~]# /etc/init.d/rpcbind start<br />
rpcbind starten:                                           [  OK  ]</p>
<p>[root@fe01 ~]# /etc/init.d/nfs start<br />
NFS-Dienste starten:                                       [  OK  ]<br />
NFS-mountd starten:                                        [  OK  ]<br />
NFS-Daemon starten:                                        [  OK  ]<br />
RPC-idmapd starten:                                        [  OK  ]`

Zusätzlich sollte das freizugebende Verzeichnis natürlich in der /etc/exports eingetragen sein:
  
`[root@fe01 ~]# cat /etc/exports<br />
/exports/data *.localkvm(rw)`

Der Mount kann dann auf der anderen Maschine gewöhnlich gemountet werden:
  
`[root@fe02 ~]# mount fe01.localkvm:/exports/data /mnt<br />
[root@fe02 ~]# cd /mnt/<br />
[root@fe02 mnt]# ll<br />
insgesamt 0<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 10.txt<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 1.txt<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 2.txt<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 3.txt<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 4.txt<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 5.txt<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 6.txt<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 7.txt<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 8.txt<br />
-rw-r--r--. 1 root root 0 11. Aug 14:54 9.txt`