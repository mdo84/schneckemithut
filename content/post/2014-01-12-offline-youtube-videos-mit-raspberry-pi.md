---
title: Offline-Youtube-Videos mit Raspberry-Pi
author: markus
type: post
date: 2014-01-12T14:13:46+00:00
url: /?p=211
categories:
  - Raspberry

---
Mit meinem Raspberry lege ich mir mittlerweile Vorträge von youtube auf meine USB-Platte zurecht: 

<pre>pi@raspberrypi ~/usb-platte/Video/Dokus $ youtube-dl -f 18 http://www.youtube.com/watch?v=xwh-G3hO_Cg
[youtube] Setting language
[youtube] xwh-G3hO_Cg: Downloading webpage
[youtube] xwh-G3hO_Cg: Downloading video info webpage
[youtube] xwh-G3hO_Cg: Extracting video information
[download] Destination: Puppet von Tim Schmeling-xwh-G3hO_Cg.mp4
[download] 100% of 143.94MiB in 00:33</pre>

Hierbei verwende ich das Prgramm <a href="http://rg3.github.io/youtube-dl" title="youtube-dl" target="_blank">youtube-dl</a> in Verbindung mit minidlna. Als Speicher kommt eine alte MyBook 1TB USB-2.0-Festplatte mit externer Stromversorgung zum Einsatz. 

Grundsätzlich lassen sich mit youtube-dl Videos von youtube (aber auch von CollegeHumor, Comedy Central, Dailymotion, Facebook, Metacafe, MyVideo, Photobucket, The Escapist, Vimeo, Yahoo!, blip.tv, depositfiles.com, video.google.com, xvideos, Soundcloud, InfoQ, Mixcloud, OpenClassRoom) in verschiedenen Qualitäten herunterladen. Hierbei gelten folgende Download-Parameter: 

<pre>-f FMT, --format=FMT
Specify the video format (quality) in which to download the video.

For youtube.com, in particular, the meaning of the format codes is given as:

WebM video at 480p: 43
WebM video at 720p: 45
H264 video in MP4 container at 480p: 18
H264 video in MP4 container at 720p: 22
H264 video in MP4 container at 1080p: 37
H264 video in FLV container at 360p: 34
H264 video in FLV container at 480p: 35
H263 video at 240p: 5
3GP video: 17</pre>

Sollten im Namen deutsche Sonderzeichen (ö, ä, ü) enthalten sein, empfiehlt es sich den Output mit -o zu ändern. Weitere Dokumentation: <a href="http://rg3.github.io/youtube-dl/documentation.html" title="Dokumentation" target="_blank">youtube-dl Doku</a>

PS: Nach dem ersten Start lässt sich das Binary auch mit 

<pre>youtube-dl -U </pre>

updaten.