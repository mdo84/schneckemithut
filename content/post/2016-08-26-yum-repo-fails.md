---
title: Yum Repo Fails…
author: markus
type: post
date: 2016-08-26T11:21:24+00:00
url: /?p=615
categories:
  - Centos
  - linux
tags:
  - proxy
  - yum

---
Ich bin heute auf folgenden Yum-Repo-Fehler gestoßen: 

 `One of the configured repositories failed (hdp-repo),<br />
 and yum doesn't have enough cached data to continue. At this point the only<br />
 safe thing yum can do is fail. There are a few ways to work "fix" this:</p>
<p>     1. Contact the upstream for the repository and get them to fix the problem.</p>
<p>     2. Reconfigure the baseurl/etc. for the repository, to point to a working<br />
        upstream. This is most often useful if you are using a newer<br />
        distribution release than is supported by the repository (and the<br />
[main]<br />
        packages for the previous distribution release still work).</p>
<p>     3. Disable the repository, so yum won't use it by default. Yum will then<br />
        just ignore the repository until you permanently enable it again or use<br />
        --enablerepo for temporary usage:</p>
<p>            yum-config-manager --disable hdp-repo</p>
<p>     4. Configure the failing repository to be skipped, if it is unavailable.<br />
        Note that yum will try to contact the repo. when it runs most commands,<br />
        so will have to try and fail each time (and thus. yum will be be much<br />
        slower). If it is a very temporary problem though, this is often a nice<br />
        compromise:</p>
<p>            yum-config-manager --save --setopt=hdp-repo.skip_if_unavailable=true`

Hier lohnt sich ebenfalls ein Blick in die /etc/yum.conf, um zu schauen ob ein Proxy konfiguriert wurde der evtl. nicht mehr tooled wie er soll. Dies war bei mir der Fall. Die Proxy-Einstellung auskommentiert -> geht. 

https://www.centos.org/forums/viewtopic.php?t=50536