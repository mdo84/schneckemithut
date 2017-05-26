---
title: Erste Erfahrungen mit Stash (Installation)
author: markus
type: post
date: 2015-06-07T20:18:00+00:00
url: /?p=524
categories:
  - Git

---
<a href="https://de.atlassian.com/software/stash" target="_blank">Stash</a> ist ein grafischer Git-Server (like Github) von Atlassian, basiert also auf Java-Technologie und bringt seinen eigenen Tomcat mit.
  
Requirements sind unter anderem ein neues Git Package (wer hätte das gedacht). Da unter CentOS Packages für SVN und Git nicht gerade mit Aktualität glänzen, fügen wir uns ein Repo für aktuelle Git-Versionen hinzu. Ich teste mal das Wandisco Repo:
  
`#http://blog.hgomez.net/2015/02/26/CentOSRHEL-and-up-to-date-Subversion-and-Git.html<br />
#Wandisco-Git.repo<br />
[wandisco-Git]<br />
name=CentOS-6 - Wandisco Git<br />
baseurl=http://opensource.wandisco.com/centos/6/git/$basearch/<br />
enabled=1<br />
gpgcheck=1<br />
gpgkey=http://opensource.wandisco.com/RPM-GPG-KEY-WANdisco`

**Installation von Hand**
  
Dann kann man sich das <a href="https://www.atlassian.com/software/stash/downloads/binary/atlassian-stash-3.9.2-x64.bin" target="_blank">Install-Binary</a> von Atlassian herunterladen. Wie in alten Windowstagen wird man durch die Installation geführt:
  
`This will install Stash 3.9.2 on your computer.<br />
OK [o, Enter], Cancel [c]<br />
o<br />
Please choose one of the following:<br />
Install a new Stash instance [1, Enter], Upgrade an existing Stash instance [2]</p>
<p>Where should Stash be installed?</p>
<p>[/opt/atlassian/stash/3.9.2]</p>
<p>Default location for Stash home directory</p>
<p>The location for Stash data.<br />
This will be the default location for repositories, plugins, and other data.</p>
<p>Ensure that this location is not used by another Stash installation.<br />
[/var/atlassian/application-data/stash]</p>
<p>Configure which ports Stash will use.</p>
<p>Stash requires two TCP ports that are not being used by any other<br />
applications.</p>
<p>The HTTP port is where users will access Stash through their browsers. The<br />
control port is used to start and stop Stash.<br />
HTTP Port Number<br />
[7990]</p>
<p>Control Port Number<br />
[8006]</p>
<p>For a production server we recommend that you run Stash as a Windows/Linux<br />
service because Stash will restart automatically when the computer restarts.<br />
Install Stash as Service?<br />
Yes [y, Enter], No [n]<br />
y<br />
Please review your Stash installation settings</p>
<p>Installation Directory: /opt/atlassian/stash/3.9.2<br />
Home Directory: /var/atlassian/application-data/stash<br />
HTTP Port: 7990<br />
Control Port: 8006<br />
Install as service: Yes </p>
<p>Install [i, Enter], Exit [e]<br />
i`

Der Prozess findet sich unter dem User atlstash
  
``<a href="https://de.atlassian.com/software/stash" target="_blank">Stash</a> ist ein grafischer Git-Server (like Github) von Atlassian, basiert also auf Java-Technologie und bringt seinen eigenen Tomcat mit.
  
Requirements sind unter anderem ein neues Git Package (wer hätte das gedacht). Da unter CentOS Packages für SVN und Git nicht gerade mit Aktualität glänzen, fügen wir uns ein Repo für aktuelle Git-Versionen hinzu. Ich teste mal das Wandisco Repo:
  
`#http://blog.hgomez.net/2015/02/26/CentOSRHEL-and-up-to-date-Subversion-and-Git.html<br />
#Wandisco-Git.repo<br />
[wandisco-Git]<br />
name=CentOS-6 - Wandisco Git<br />
baseurl=http://opensource.wandisco.com/centos/6/git/$basearch/<br />
enabled=1<br />
gpgcheck=1<br />
gpgkey=http://opensource.wandisco.com/RPM-GPG-KEY-WANdisco`

**Installation von Hand**
  
Dann kann man sich das <a href="https://www.atlassian.com/software/stash/downloads/binary/atlassian-stash-3.9.2-x64.bin" target="_blank">Install-Binary</a> von Atlassian herunterladen. Wie in alten Windowstagen wird man durch die Installation geführt:
  
`This will install Stash 3.9.2 on your computer.<br />
OK [o, Enter], Cancel [c]<br />
o<br />
Please choose one of the following:<br />
Install a new Stash instance [1, Enter], Upgrade an existing Stash instance [2]</p>
<p>Where should Stash be installed?</p>
<p>[/opt/atlassian/stash/3.9.2]</p>
<p>Default location for Stash home directory</p>
<p>The location for Stash data.<br />
This will be the default location for repositories, plugins, and other data.</p>
<p>Ensure that this location is not used by another Stash installation.<br />
[/var/atlassian/application-data/stash]</p>
<p>Configure which ports Stash will use.</p>
<p>Stash requires two TCP ports that are not being used by any other<br />
applications.</p>
<p>The HTTP port is where users will access Stash through their browsers. The<br />
control port is used to start and stop Stash.<br />
HTTP Port Number<br />
[7990]</p>
<p>Control Port Number<br />
[8006]</p>
<p>For a production server we recommend that you run Stash as a Windows/Linux<br />
service because Stash will restart automatically when the computer restarts.<br />
Install Stash as Service?<br />
Yes [y, Enter], No [n]<br />
y<br />
Please review your Stash installation settings</p>
<p>Installation Directory: /opt/atlassian/stash/3.9.2<br />
Home Directory: /var/atlassian/application-data/stash<br />
HTTP Port: 7990<br />
Control Port: 8006<br />
Install as service: Yes </p>
<p>Install [i, Enter], Exit [e]<br />
i`

Der Prozess findet sich unter dem User atlstash
  
`` 

Das Setup kann dann per HTTP weitergeführt werden:
  
`http://servername:7990/setup`

**Automatisierte Installation**
  
Automatisches installieren, mitgeben der Parameter in einem <a href="https://confluence.atlassian.com/display/STASH/Running+the+Stash+installer#RunningtheStashinstaller-modes" target="_blank">varfile</a>

Dies würde dann folgendes enthalten:
  
 `// Should Stash be installed as a Service? Must be ADMIN (default: true if the process is running with administrator rights, false otherwise). If false, the home and installation directories must be specified to point to directories owned by the user<br />
app.install.service$Boolean=true</p>
<p>// The ports Stash should bind to (defaults: portChoice=default, httpPort=7990, serverPort=8006)<br />
portChoice=custom<br />
httpPort=7990<br />
serverPort=8006</p>
<p>// Path to the Stash HOME directory (default: /var/atlassian/application-data/stash if the process is running with administrator rights, ~/atlassian/application-data/stash otherwise)<br />
app.stashHome=/var/atlassian/application-data/stash</p>
<p>// The target installation directory (default: /opt/atlassian/stash/<VERSION> if the process is running with administrator rights, ~/atlassian/stash/<VERSION> otherwise)<br />
app.defaultInstallDir=/opt/atlassian/stash/<VERSION>`

Zusätzlich sollte man vor dem ersten Start eine Configfile (stash-config.properties) anlegen und mit Inhalten befüllen, wie [hier][1] beschrieben.

 [1]: https://confluence.atlassian.com/display/STASH/Automated+setup+for+Stash