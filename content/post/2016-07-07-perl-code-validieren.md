---
title: perl code validieren
author: markus
type: post
date: 2016-07-07T19:36:16+00:00
url: /?p=543
categories:
  - Perl

---
Perlcode lässt sich leicht validieren, gerade bei Rex-Modulen besonders praktisch 😉

`$ cat test.pl<br />
#!/usr/bin/perl</p>
<p>use strict;<br />
use warnings;</p>
<p>print "test";<br />
$ perl -c test.pl<br />
test.pl syntax OK`

`$ cat test.pl<br />
#!/usr/bin/perl<br />
#<br />
use strict;<br />
use warnings</p>
<p>my $pewpew = "test"<br />
print $pewpew;<br />
$ perl -c test.pl<br />
syntax error at test.pl line 9, near "print"<br />
Global symbol "$pewpew" requires explicit package name (did you forget to declare "my $pewpew"?) at test.pl line 9.<br />
test.pl had compilation errors.`