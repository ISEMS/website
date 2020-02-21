
---
title: FF-ESP32
url: /FF-ESP32
draft: false
menu: header
---


# Neue Freifunk OpenMPPT-Hardware basierend auf ESP32 mit ISEMS-Firmware und WiFi
Freifunk hat einen neuen Solar-MPP-Tracking-Solarladeregler mit integriertem WLAN
entworfen. Wir haben eine ISEMS-Firmwarelösung entwickelt, die auf FreeRTOS und Nodemcu für den ESP32-Chip
basiert.

Der Stromverbrauch unter Volllast beträgt im Vollbetrieb nur 0,6 W im
Accesspoint-Modus und 0,3 W bei Betrieb als WiFi-Client.

Hardware-Prototyp und Software funktionieren bereits einwandfrei, die endgültige Hardware
wird jedoch einen zusätzlichen UEXT-Header haben, weil die Community uns
nach der Möglichkeit gefragt hat, weiter externe Sensoren hinzuzufügen.

Eine einführende Anleitung auf Englisch für die Benutzung gibt es
[hier](https://github.com/ISEMS/ISEMS-ESP32/blob/master/BEGINNER-HOWTO.md).

![FF-ESP32-OpenMPPT-v1.0](/images/ff-esp32-openmppt.jpg)
