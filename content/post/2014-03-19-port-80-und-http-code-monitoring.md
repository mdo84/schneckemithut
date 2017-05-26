---
title: Port 80 und HTTP-Code Monitoring
author: markus
type: post
date: 2014-03-19T14:47:39+00:00
url: /?p=310
categories:
  - Allgemein

---
Hier ein Script um Port 80 und HTTP-Code 200 zu monitoren (Emailadressen sind noch anzupassen).
  
Abhängigkeit: sendmail
  
`#!/bin/bash<br />
#<br />
RECIPIENT="hüh@hott.de"<br />
FROM="blub@bla.de"<br />
HOSTNAME=$(hostname)<br />
VHOST="schneckemithut.de"</p>
<p>ERRORPORTMESSAGE="subject:ERROR on $HOSTNAME\nfrom:$FROM\nERROR on $HOSTNAME, Port 80 is not running"<br />
ERRORHTTPMESSAGE="subject:ERROR on $HOSTNAME\nfrom:$FROM\nERROR on $HOSTNAME, there is no good HTTP-Code"</p>
<p># Check netstat, grep httpd, grep there Port 80, list double entries unique<br />
HTTPCHECK=$(netstat -tulpen | grep httpd | grep -o 80 | uniq)<br />
if [[ $HTTPCHECK != "80" ]]; then<br />
  echo -e $ERRORPORTMESSAGE | /usr/sbin/sendmail $RECIPIENT<br />
fi</p>
<p># Check vhost<br />
VHOSTCHECK=$(curl --write-out "%{http_code}" --silent --header "Host: $VHOST" --output /dev/null http://localhost:80)<br />
if [[ $VHOSTCHECK != "200" ]]; then<br />
  echo -e $ERRORHTTPMESSAGE | /usr/sbin/sendmail $RECIPIENT<br />
fi`