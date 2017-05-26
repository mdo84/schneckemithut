---
title: URLs aus HTML grep’en
author: markus
type: post
date: 2016-10-05T08:38:16+00:00
url: /?p=618
categories:
  - Bash
tags:
  - bash
  - grep
  - urls

---
Hier ein Snippet, mit welchem sich URLs aus HTML grep&#8217;en lassen:
  
`$ curl <url> 2>&1 | egrep -o  "(http|https):.*\">" | awk  'BEGIN {FS="\""};{print $1}'`

Hiermit lassen sich auch prima direkt files herunterladen, z.b. PDFs:
  
`$ curl http://events.linuxfoundation.org/events/linuxcon-europe/program/slides 2>&1 | egrep -o  "(http|https):.*\">" | grep "sites/events/files/slides" | awk  'BEGIN {FS="\""};{print $1}' > urls.txt; for i in $(cat urls.txt); do wget $i; done`