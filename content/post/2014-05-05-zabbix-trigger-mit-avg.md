---
title: Zabbix-Trigger mit avg
author: markus
type: post
date: 2014-05-05T16:51:25+00:00
url: /?p=339
categories:
  - Allgemein
  - Zabbix

---
Hier ein Trigger für ein Zabbix-Template, welcher alarmiert, wenn das Item die letzten 10 Minuten (600 Sekunden) nicht einen Wert zurücklieferte.
  
`{Template_Solr_Corecheck:solr.solrnumdocs[{$SOLRHOST},{$SOLRPORT},{$SOLRCORE1}].avg(600)}<1`

In dem Fall prüft der Trigger ein Script auf der Maschine ab, welches die Dokumentenanzahl eines Solr-Cores zurückgibt. Der Trigger prüft dann die letzten 10 Minuten, ob der Durchschnitt der Werte kleiner 1 ist, dann wird alarmiert. Dies umgeht einzelne Fehlalarme, falls die Responsezeit des Solrs mal etwas &#8222;größer&#8220; ausfällt. Ist somit die letzten 10 Minuten kein Wert zustandegekommen (default im Script = 0), wird alarmiert. Ist auch nur eine Response dazwischen (Doc-Anzahl meist >10000), fällt der avg größer 1 aus -> wird nicht alarmiert.