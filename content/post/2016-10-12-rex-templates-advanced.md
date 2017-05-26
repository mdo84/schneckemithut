---
title: Rex Templates advanced
author: markus
type: post
date: 2016-10-12T09:52:33+00:00
url: /?p=620
categories:
  - Perl
  - Rex

---
Um kompliziertere Config-Files auf Maschinen auszubringen kann man sich ebenfalls einer File-Resource bedienen und Parameter mitgeben. 

`my $test_vhosts = get cmdb "vhosts";<br />
task "config", group => "servers", sub {</p>
<p>  file "/this/is/my/config",<br />
      owner   => "root",<br />
      group   => "root",<br />
      mode    => "644",<br />
      content => template("config/config_file.tpl",<br />
          vhosts                => \@vhosts<br />
      );`

Zu beachten ist hier: Das Array muss als content-Parameter derefenziert werden ( daher der \ vor @).
  
Im Template lässt sich dann über das Array iterieren: 

`$ cat config/config_file.tpl<br />
  # list of vhosts<br />
  <% for my $vhost (@{ $vhosts }) { %><br />
  here comes the vhost: <%= $vhost %><br />
  <% } %>`

Inline-Perl wird hierbei mit <% und %> begrenzt. Variablen können mit <%= $var %> verwendet werden.
  
Zusätzlich lassen sich inline auch weitere Perlmodule und Funktionen ausführen &#8211; z.b: 

`$ cat config/config_file.tpl<br />
  <% use Digest::MD5 qw(md5_hex); %><br />
  # list of vhosts<br />
  <% for my $vhost (@{ $vhosts }) { %><br />
  <% my $md5_vhost = md5_hex($vhost); %><br />
  here comes the vhost: <%= $vhost %><br />
  here comes the md5_vhost: <%= $md5_vhost %><br />
  <% } %>`