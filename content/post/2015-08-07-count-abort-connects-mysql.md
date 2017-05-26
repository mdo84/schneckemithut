---
title: count abort connects mysql
author: markus
type: post
date: 2015-08-07T13:22:25+00:00
url: /?p=556
categories:
  - Allgemein

---
Um sich die abgebrochenen Mysql-Connections von Clients an den Server anzuschauen reicht ein
  
`mysql -e "show global status like '%abort%';"<br />
+------------------+-------+<br />
| Variable_name    | Value |<br />
+------------------+-------+<br />
| Aborted_clients  | 0     |<br />
| Aborted_connects | 1     |<br />
+------------------+-------+`