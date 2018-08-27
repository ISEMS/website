---
title: Hardware
url: /hardware/
menu: header
---
# Hardware

## Der Freifunk-OpenMPPT

Der Freifunk-OpenMPPT ist ein programmierbarer Open-Source und Open-Hardware Solarladeregler mit sogenanntem Maximum-Power-Point-Tracking.  MPP-Tracking bedeutet, dass der Solarregler die Spannung des Solarmoduls im Punkt größter Ausgangsleistung berechnet und elektronisch nachführt, so dass der größtmögliche Energieertrag entsteht. Dadurch läßt sich der Ladestrom – je nach Batterieladestand und Temperatur – gegenüber einem einfachen PWM-Laderegler um bis zu 40% steigern. Der Freifunk-OpenMPPT besitzt eine serielle Schnittstelle, über die er seine  Betriebsdaten ausgibt und über die er auch gesteuert und seine Firmware neu geflasht werden kann. 

 Es gibt unterschiedliche Leistungsstufen des Freifunk-OpenMPPT.  Modell A ist für kleinere Anlagen bis 50 Watt Solarmodulleistung ausgelegt, Modell B für 100 Watt und Modell C (in Planung) für 300 Watt. Die Geräte sind primär gedacht für die Versorgung und Überwachung der Stromversorgung von energieautonomen Freifunk-Routern oder überall da, wo man eine kleine und effiziente unabhängige Stromversorgung braucht, insbesondere dann, wenn man ihre Betriebsdaten auch aus der Ferne überwachen möchte.

## Funktionen des  Freifunk-OpenMPPT-Solarcontrollers

* Serielle Schnittstelle mit 3.3 Volt TTL Pegel.

* Solarladeregler mit Nachführung der Solargeneratorspannung im maximalen Leistungspunkt (sogenanntes Maximum-Power-Point-Tracking)

* Erhöhung des Energieertrags durch effizienten DC/DC-Abwärtswandler mit >95% Wirkungsgrad

* Tiefentladeschutz mit programmierbarem Ein- und Ausschaltpunkt

* Überwachung von Leerlaufspannung des Solarmoduls, Eingangsspannung im Leistungspunkt, Batteriespannung und Batterietemperatur.

* Temperaturgesteuerte Ladekennlinie nach **IU**-Verfahren

* Programmierbarer Router-Reset Timer (Watchdog)

* Powerdown-Timer um Energie zu sparen

* Konfigurierbarer Tiefentladeschutz

* Funktioniert auch ohne Router als universell einsetzbarer Solarladeregler mit MPPT-Funktion.

* Firmware kann über den Bootloader neu geflasht werden.



## Diagramm


## Installation


## Video
<figure>
<div class="iframe-wrapper">
<iframe src="https://www.youtube-nocookie.com/embed/BxFpY2tsPtU?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
</div>
<figcaption>
In diesem Video wird die Installation eines Freifunk-OpenMPPT-Mastes gezezeigt.
</figcaption>
</figure>
