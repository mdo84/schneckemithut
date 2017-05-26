---
title: rpm-Package-Building
author: markus
type: post
date: 2014-01-29T10:13:54+00:00
url: /?p=261
categories:
  - Allgemein

---
Um Pakete im rpm-Format zu bauen, benötigt man ein spec-file und das Package rpm-build.
  
Links hierzu:
  
https://www.redhat.com/archives/rpm-list/2001-December/msg00200.html
  
http://www.tldp.org/HOWTO/RPM-HOWTO/build-it.html

Hier ein Specfile welches ein vorhandes tar.gz-Paket in die vorhergesehenen Verzeichnisse verteilt. 

<pre>Name:  solr-ezfind
Version:    4.6.0
Release:    1
BuildArch:  noarch
Summary:    Apache Solr for with ezfind-extensions

Group:      System Environment/Daemons
License:    Apache License
URL:        http://lucene.apache.org/solr/
BuildRoot:  %(mktemp -ud %{_tmppath}/%{name}-%{version}-%{release}-XXXXXX)
Packager:   Markus Dollinger &lt;markus@schneckemithut.de>

BuildRequires:  pkgconfig
Requires:   sed

%description
Solr is the popular, blazing fast open source enterprise search platform from
the Apache Lucene project. This package contains the adapted version of Solr, 
additionally the ezfind-extensions from ezfind-solr27.noarch (2.7.0-9).


%build
tar xfz %{_sourcedir}/solr-ezfind-4.6.tar.gz

%install
rm -rf %{buildroot}
%{__mkdir} -p %{buildroot}/opt/solr46
cp -rp contrib %{buildroot}/opt/solr46/contrib
cp -rp dist %{buildroot}/opt/solr46/dist
cp -rp example %{buildroot}/opt/solr46/example
cp -rp docs %{buildroot}/opt/solr46/docs
cp -rp licenses %{buildroot}/opt/solr46/licenses

%post
chown -R solr4:solr4 /opt/solr46


%clean
rm -rf %{buildroot}


%files
%defattr(-,root,root,-)
/opt/solr46/*
%doc

%changelog
* Wed Jan 29 2014 Markus Dollinger &lt;markus@schneckemithut.de> - 4.6.0-1
- Initial build.</pre>

Das bauen des Paketes wird dann in der Verzeichnisstruktur von rpmbuild durchgeführt: 

<pre>rpmbuild -ba solr.spec</pre>

Wobei sich das tar.gz im SOURCES-Verzeichnis befinden sollte: 

<pre>~/rpmbuild# tree
.
|-- BUILD
|-- BUILDROOT
|-- RPMS
|   |-- i386
|   |   `-- solr-ezfind-4.6.0-1.i386.rpm
|   `-- noarch
|       `-- solr-ezfind-4.6.0-1.noarch.rpm
|-- SOURCES
|   `-- solr-ezfind-4.6.tar.gz
|-- SPECS
|   `-- solr.spec
`-- SRPMS
    `-- solr-ezfind-4.6.0-1.src.rpm</pre>