---
title: Redirects (Weiterleitungen) mit Varnish Webcache
author: markus
type: post
date: 2013-10-24T13:13:30+00:00
url: /?p=123
categories:
  - Varnish

---
Möchte man eine Weiterleitung auf eine URL in den Varnish eintragen reicht bereits folgender Eintrag in der vcl_recv: 

<pre>if (req.http.host == "meinedomain.com") {
    if (req.url == "^/HURRA") {
	set req.url = regsub(req.url, "^/HURRA", "/weg/zu/HURRA");
}
</pre>

Danach die vcl mit varnish\_reload\_vcl neu laden, alternativ 

<pre>pkill varnishd
varnishd -f /etc/varnish/default.vcl -s malloc,1G -T 127.0.0.1:2000 -a 0.0.0.0:80
</pre>

Weitere Informationen auch [hier][1].

 [1]: https://www.varnish-cache.org/trac/wiki/RedirectsAndRewrites "https://www.varnish-cache.org/trac/wiki/RedirectsAndRewrites"