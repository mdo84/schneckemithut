---
title: FTP-Configuration
author: markus
type: post
date: 2014-03-14T11:18:56+00:00
url: /?p=302
categories:
  - Proftp

---
Hier einige Links zur Konfiguration eines FTP-Servers:
  
`http://ubuntuforums.org/showthread.php?t=79588<br />
http://www.proftpd.org/docs/howto/ConfigFile.html`

Hier wird der Daemon Proftpd verwendet und Verwendung der Unix-Authentifizierung. Gerade dieser Teil hat es mir angetan, da ich keine Lust hatte einen Anonymous-FTP zu betreiben: 

`FTP-Verzeichnisse:<br />
~/download<br />
~/upload</p>
<p><Directory /home/FTP-shared><br />
Umask 022 022<br />
AllowOverwrite off<br />
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD><br />
	DenyAll<br />
	</Limit><br />
</Directory></p>
<p><Directory /home/FTP-shared/download/*><br />
Umask 022 022<br />
AllowOverwrite off<br />
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD><br />
	DenyAll<br />
	</Limit><br />
</Directory></p>
<p><Directory /home/FTP-shared/upload/><br />
Umask 022 022<br />
AllowOverwrite on<br />
	<Limit READ RMD DELE><br />
      	DenyAll<br />
    	</Limit></p>
<p>    	<Limit STOR CWD MKD><br />
      	AllowAll<br />
    	</Limit><br />
</Directory>`