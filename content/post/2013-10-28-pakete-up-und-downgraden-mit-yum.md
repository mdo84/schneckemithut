---
title: 'Pakete up- und downgraden mit yum'
author: markus
type: post
date: 2013-10-28T12:00:02+00:00
url: /?p=130
categories:
  - Allgemein

---
Mit yum lassen sich Pakete einfach up- und auch downgraden (gerade wenn der installierte Build mal doch nicht so stabil ist wie angenommen, oder wenn es der Kunde gerade erfordert). Voraussetzung hierbei ist das vorhanden sein der gewünschten Version im Repository der Software. Hier ein Beispiel anhand des Paketes &#8222;rex&#8220; (was nicht heist, rex ist in der neuesten Version nicht stabil!): 

<pre>Installed:
  rex.i686 0:0.43.5-1 
~# yum downgrade rex-0.36.0-1.i686
&lt;&lt;&lt;&lt;&lt;&lt;
---> Package rex.i686 0:0.36.0-1 will be a downgrade
--> Processing Dependency: perl(JSON::XS) for package: rex-0.36.0-1.i686
---> Package rex.i686 0:0.43.5-1 will be erased
&lt;&lt;&lt;&lt;&lt;&lt;
 Package                              Arch                Version            Repository              Size
=================================================================================================================
Downgrading:
 rex                                  i686                0.36.0-1           rex                     263 k
Installing for dependencies:
 perl-JSON-XS                         i386                2.32-1.el6         rex                     93 k
 perl-common-sense                    i386                3.4-1.el6          rex                     23 k
&lt;&lt;&lt;&lt;&lt;&lt;
Removed:
  rex.i686 0:0.43.5-1                                                                                                                                                                                
Installed:
  rex.i686 0:0.36.0-1 </pre>

und wieder upgraden: 

<pre>~# yum update rex
---> Package rex.i686 0:0.36.0-1 will be updated
---> Package rex.i686 0:0.43.7-1 will be an update
Updated:
  rex.i686 0:0.43.7-1                                                                                                                                                                                
Complete!</pre>

So lässt sich yum auch schön in Rollbackscripten einsetzen, falls eine Version fehler aufweist und dringend auf eine stabile Version zurückgestuft werden muss.