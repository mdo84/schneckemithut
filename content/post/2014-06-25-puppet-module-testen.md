---
title: Puppet-Module testen
author: markus
type: post
date: 2014-06-25T12:26:57+00:00
url: /?p=390
categories:
  - Allgemein

---
Um ein einzelnes Puppet-Modul zu testen genügt ein
  
`puppet apply --modulepath=. --noop site.pp`
  
mit folgendem Puppet-Beispiel-Code:
  
`# ls<br />
site.pp ssh<br />
# cat site.pp<br />
node default {<br />
class { 'ssh': }<br />
}<br />
# cat ssh/manifests/init.pp<br />
class ssh {<br />
package { 'ssh':<br />
ensure => present,<br />
}<br />
}`