---
title: Manjaro Pacman GPG-Error
author: markus
type: post
date: 2015-01-16T14:00:03+00:00
url: /?p=490
categories:
  - linux
  - Manjaro
tags:
  - GPG Error

---
Manchmal lassen sich unter Manjaro Paketquellen nicht mehr herunterladen und man wird mit einem GPG-Error abserviert.
  
`Fehler: GPGME error: Keine Daten<br />
Fehler: GPGME error: Keine Daten<br />
Fehler: GPGME error: Keine Daten<br />
Fehler: GPGME error: Keine Daten`

Hierbei hilft es die GPG-Keys zu erneuern:
  
`sudo pacman-key --refresh-keys<br />
sudo pacman-key --populate<br />
sudo pacman -Scc<br />
sudo pacman -Syy`

Quelle: https://forum.manjaro.org/index.php?PHPSESSID=rled3jkmv1rbl83la38u4ujj41&topic=1157.msg9049#msg9049

UPDATE:
  
Mittlerweile wurde für die neueren Manjaro-Releases ein alias für die .bashrc eingeführt:
  
`sudo rm -f /var/lib/pacman/db.lck && sudo pacman-mirrors -g && sudo pacman -Syyuu  && sudo pacman -Suu`

Dieser behebt auch die Probleme wie oben beschrieben. 

UPDATE die zweite:
  
Es hat sich noch ein weiterer Fehler dazugesellt:
  
`error: key "CAA6A59611C7F07E" could not be looked up remotely`

Dieser Error lässt sich hiermit lösen:
  
`pacman -Sy archlinux-keyring manjaro-keyring<br />
pacman-key --init<br />
pacman-key --populate archlinux manjaro`
  
Quelle: https://forum.manjaro.org/index.php?topic=63.0