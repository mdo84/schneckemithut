---
title: SSL mit letsencrypt
author: markus
type: post
date: 2016-06-02T19:35:11+00:00
url: /?p=582
categories:
  - Allgemein

---
Ich bin mittlerweile auf letsencrypt umgestiegen und lasse mir hier meine Zertifikate generieren.
  
`https://letsencrypt.org/getting-started/`

Gerade wenn man so richtig faul ist (wie ich), packt man das ganze dann noch in einen cronjob und ist glücklich 🙂
  
`1 1 1 * * root <pfad zu certbot>/certbot-auto renew`