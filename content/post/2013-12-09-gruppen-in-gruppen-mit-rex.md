---
title: Gruppen in Gruppen mit Rex
author: markus
type: post
date: 2013-12-09T13:39:42+00:00
url: /?p=179
categories:
  - Rex

---
Arbeiten mit mehreren genesteten Gruppen in Rex über Arrays: 

<pre>@frontends = qw/server1 server2 server3 server4/;
@backends = qw/server5 server6 server7/;
@all = (@frontends, @backends);

group frontends => @frontends;
group backends => @backends;
group all => @all;</pre>

Mehr zu Rex gibt es hier: [www.rexify.org][1]

 [1]: http://www.rexify.org "Rexify"