---
title: Redirects mit Varnish
author: markus
type: post
date: 2014-07-24T08:32:57+00:00
url: /?p=424
categories:
  - Varnish

---
Um Redirects mit Varnish zu lösen, muss man mit Error-Codes arbeiten. Folgendes Szenario: 

Man möchte mit einem 301er auf eine andere Domain umleiten, sichtbar für den User im Browserfenster:
  
Requests an hurra.example.com sollen an pimp.my.domain weitergeleitet werden.
  
`backend hurra {<br />
    .host = "hurra.example.com";<br />
    .port = "80";<br />
}</p>
<p>sub vcl_recv {<br />
   if (req.http.host ~ "^hurra\.example\.com$") {<br />
      error 750 "Moved Permanently";<br />
   }<br />
}</p>
<p>sub vcl_error {<br />
    if (obj.status == 750) {<br />
        set obj.http.Location = "http://pimp.my.domain/";<br />
        set obj.status = 301;<br />
        return(deliver);<br />
    }<br />
}`

Alternativ wäre dies auch versteckt möglich. Der user würde dann nichts davon mitbekommen&#8230;
  
`backend hurra {<br />
    .host = "hurra.example.com";<br />
    .port = "80";<br />
}<br />
backend pimp {<br />
     .host = "pimp.my.domain";<br />
     .port = "80";<br />
}</p>
<p>sub vcl_recv {<br />
   if (req.http.host ~ "^hurra\.example\.com$") {<br />
       set req.http.host = "pimp.my.domain";<br />
       set req.url = regsub(req.url, "^hurra\.example\.com$", "pimp.my.domain");<br />
       set req.backend = pimp;<br />
       return (lookup);<br />
   }<br />
}`