---
title: Catch-all des Nginx mit Server_name
author: markus
type: post
date: 2014-02-10T13:24:32+00:00
url: /?p=274
categories:
  - Allgemein

---
Catch-all per Server_name mit Nginx: 

<pre>In catch-all server examples the strange name “_” can be seen:

    server {
        listen       80  default_server;
        server_name  _;
        return       444;
    }

There is nothing special about this name, it is just one of a myriad of invalid domain names which never intersect with any real name. Other invalid names like “--” and “!@#” may equally be used. </pre>

Quelle: <a href="http://nginx.org/en/docs/http/server_names.html" title="http://nginx.org/en/docs/http/server_names.html" target="_blank">http://nginx.org/en/docs/http/server_names.html</a>