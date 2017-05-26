---
title: Host ins Puppet aufnehmen
author: markus
type: post
date: 2014-01-12T20:20:35+00:00
url: /?p=216
categories:
  - Puppet

---
Um einen neuen Host ins Puppet aufzunehmen durchlaufen wir folgende Schritte:
  
Connection zum Puppet-Master auf dem Master genehmigen:
  
iptables -A INPUT -p tcp -m state &#8211;state NEW -s AGENT-IP &#8211;dport 8140 -j ACCEPT

Puppet auf dem Agent installieren (yum install puppet facter) puppet mit 

<pre>~# puppet agent --server=MASTER-IP --no-daemonize --verbose
info: Creating a new SSL key for AGENT
info: Caching certificate for ca
info: Creating a new SSL certificate request for AGENT
info: Certificate Request fingerprint (md5): CE:87:DA:DA:FF:DB:52:B2:94:DD:DE:E8:5D:E6:78:53
notice: Did not receive certificate
...
</pre>

Nun kann auf dem Master der SSL-Request mit 

<pre>puppet cert --list</pre>

angeguckt und mit 

<pre>puppet cert --sign AGENT</pre>

bestätigt werden. Zuletzt muss noch ein Node unter manifests/\* definiert werden. Je nach Node-Definition eine \*.pp-File, alternativ in der nodes.pp: 

<pre>node 'AGENT' {
}</pre>

Der Agent sollte nun beim Master den aktuellen Katalog abrufen können: 

<pre>~#puppet agent server=PUPPET-MASTER --no-daemonize --onetime --no-usecacheonfailure -v --noop --test
info: Caching catalog for AGENT
info: Applying configuration version '1389551645'
notice: Finished catalog run in 0.02 seconds</pre>