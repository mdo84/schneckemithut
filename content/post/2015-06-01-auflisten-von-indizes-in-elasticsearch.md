---
title: Auflisten von Indizes in ElasticSearch
author: markus
type: post
date: 2015-06-01T09:44:21+00:00
url: /?p=508
categories:
  - Allgemein

---
Um sich alle verfügbaren Indizes in ElasticSearch anzuzeigen, kann die URI &#8222;_aliases&#8220; des Clusters verwendet werden:
  
`curl -s http://localhost:9200/_aliases`

Um das Ganze noch ein wenig hübsch zu machen, genügt &#8222;pretty&#8220;
  
`curl -s http://localhost:9200/_aliases?pretty=true`