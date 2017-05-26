---
title: Grafikfehler – Archlinux / Manjaro
author: markus
type: post
date: 2014-06-24T07:06:05+00:00
url: /?p=386
categories:
  - linux
  - Manjaro

---
Hatte gestern mit Grafikproblemen zu kämpfen.
  
Hier eine Lösung um einen Grafiktreiber downzugraden:
  
https://de.manjaro.org/index.php?topic=1428.0

Ausschnitt:
  
`Falls du in /var/cache/pacman/pkg/ noch die Vorgängerversion liegen hast<br />
einfach mal ausprobieren. Das Paket xf86-video-intel downgraden.<br />
"pacman -U /var/cache/pacman/pkg/xf86-video-intel*** .<br />
Wenns daran nicht lag wieder auf die neue Version updaten.</p>
<p>Außerdem habe ich das Packet erstmal vom Upgrade ausgeschlossen:</p>
<p>/etc/pacman.conf<br />
# Pacman won't upgrade packages listed in IgnorePkg and members of IgnoreGroup<br />
IgnorePkg   = xf86-video-intel`