---
title: sound-device finden
author: markus
type: post
date: 2014-05-19T15:08:59+00:00
url: /?p=361
categories:
  - Allgemein
  - Bash
  - linux

---
Herausfinden des Sounddevices, bzw. anzeigen dieser:
  
`$ aplay -L<br />
null<br />
    Discard all samples (playback) or generate zero samples (capture)<br />
pulse<br />
    PulseAudio Sound Server<br />
default<br />
    Default ALSA Output (currently PulseAudio Sound Server)<br />
sysdefault:CARD=PCH<br />
    HDA Intel PCH, ALC3202 Analog<br />
    Default Audio Device<br />
front:CARD=PCH,DEV=0<br />
    HDA Intel PCH, ALC3202 Analog<br />
    Front speakers<br />
surround40:CARD=PCH,DEV=0<br />
    HDA Intel PCH, ALC3202 Analog<br />
    4.0 Surround output to Front and Rear speakers<br />
surround41:CARD=PCH,DEV=0<br />
    HDA Intel PCH, ALC3202 Analog<br />
    4.1 Surround output to Front, Rear and Subwoofer speakers<br />
surround50:CARD=PCH,DEV=0<br />
    HDA Intel PCH, ALC3202 Analog<br />
    5.0 Surround output to Front, Center and Rear speakers<br />
surround51:CARD=PCH,DEV=0<br />
    HDA Intel PCH, ALC3202 Analog<br />
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers<br />
surround71:CARD=PCH,DEV=0<br />
    HDA Intel PCH, ALC3202 Analog<br />
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers`

Wird beispielsweise bei recordmydesktop benötigt, kann dann mit &#8211;device z.B. front als Soundquelle ausgewählt werden.