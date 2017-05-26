---
title: Perl-Module neu bauen und installieren
author: markus
type: post
date: 2014-06-30T14:27:48+00:00
url: /?p=396
categories:
  - Allgemein

---
Perl Module können über die CPAN-Shell neu gebaut und installiert werden.
  
Aufrufen der CPAN-Shell:
  
`sudo perl -MCPAN -eshell<br />
cpan[1]> install ADAMK/List-MoreUtils-0.33.tar.gz<br />
cpan[2]> install RKITOVER/Net-SSH2-0.53.tar.gz`

Die Module werden mit AUTHOR/modulname-Version.tar.gz in der Notation zum CPAN-Baum eingegeben.
  
[Net::SSH2-Modul bei CPAN][1]

Die Version von Modulen kann folgendermaßen angezeigt werden:
  
`cpan[1]> m Net::SSH2<br />
Reading '/home/markusd/.cpan/Metadata'<br />
  Database was generated on Mon, 30 Jun 2014 04:41:01 GMT<br />
Module id = Net::SSH2<br />
    CPAN_USERID  RKITOVER (Rafael Kitover <rkitover@gmail.com>)<br />
    CPAN_VERSION 0.53<br />
    CPAN_FILE    R/RK/RKITOVER/Net-SSH2-0.53.tar.gz<br />
    MANPAGE      Net::SSH2 - Support for the SSH 2 protocol via libssh2.<br />
    INST_FILE    /usr/lib/perl5/site_perl/Net/SSH2.pm<br />
    INST_VERSION 0.53`

 [1]: https://metacpan.org/pod/Net::SSH2 "Net::SSH2-Modul"