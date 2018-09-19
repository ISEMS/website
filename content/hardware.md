---
title: Hardware
url: /hardware/
draft: false
menu: header
---
# Hardware

# Zum Aufbau eines ISEMS-Solarknotens werden folgende Hardwarekomponenten benötigt:

1. Ein WLAN-Router. Es sollte ein energiesparendes Modell sein, das von OpenWRT unterstützt wird und eine serielle Schnittstelle eingebaut hat (das haben praktisch alle, aber meistens muss man Pins bestücken).

2. Ein Freifunk-OpenMPPT-Solarladeregler mit Temperatursensor. Zur Zeit gibt es eine Version für Solarmodule bis zu 50 Watt (Typ A) und Prototypen bis zu 100 Watt (Typ B) Eine Version bis 300 Watt ist in Planung. Typ A kostet ohne Gehäuse 40 Euro, Typ B voraussichtlich 60 Euro.

3. Ein Bleiakku vom Typ Blei-Gel oder Blei-AGM mit 12 Volt Nennspannung.

4. Solarmodul mit typisch 50 Watt für 12 Volt Systeme und einer Spannung im maximalen Leistungspunkt um 18 Volt für Freifunk-OpenMPPT-Regler Typ A oder Typ B. Ausreichend für ein System mit einem Radio-Interface oder einem sehr sparsamen System mit zwei Radios. Solarmodule gleichen Typs können parallel geschaltet werden.

5. Kleinteile wie Befestigungsmaterial, Kabel, eine Sicherung, ein wasserdichtes Gehäuse.

## Diagramm

Hier die verdrahteten Elemente eines laufenden Knotens in einer Übersicht.

![Hardware](/images/Blockschaltbild-Foto-mittel.png)



# 1. Geeignete WLAN-Router

Für ISEMS verwenden wir keine teuren Meshrouter von kommerziellen Herstellern, die proprietäre und inkompatible Produkte anbieten, sondern freie Software und das freie Embedded-Linux OpenWRT, mit dem wir geeignete, preiswerte Router zum Meshbetrieb umflashen. Auch ISEMS ist freie Software und der verwendete Freifunk-Solarcontroller ist Open-Hardware und Open-Software. Dabei sind wir bestrebt, die Kosten pro Solarknoten möglichst gering zu halten. Wichtig ist dazu die Wahl eines energiesparenden Routers. Greift man hier zu einem falschen Modell, entstehen hohe Folgekosten, weil sich der Aufwand für die Energieversorgung erheblich verteuert. Noch ein Kriterium ist wichtig, falls man meshen möchte: Der WLAN-Chipsatz des Routers muss stabil Multipunkt-zu-Multipunkt-Verbindungen aufbauen können.

#### Welcher WLAN-Modus und welcher WLAN-Chipsatz?
Für ein »echtes« Meshnetzwerk braucht man pro Knotenpunkt mindestens ein WLAN-Interface, dass stabil im Ad-Hoc-Modus oder nach 802.11s funkt. Der Grund: Wir brauchen zum »echten« Meshen die Multipunkt-zu-Multipunkt-Betriebsart von WLAN. Heute gibt es in WLAN nach IEEE 802.11 zwei Multipunkt-zu-Multipunkt-Betriebsarten zur Auswahl: 

* Ad-Hoc (Alte Schule ;)

* 802.11s (Die Neue)

Die Organisation IEEE – Institute of Electrical and Electronics Engineers – hat sich vor ein paar Jahren dazu entschlossen, einen verbesserten Multipunkt-zu-Multipunkt-Betriebsmodus zur IEEE 802.11-Protokollfamilie hinzu zu fügen. Dabei dachte man auch gleich daran, zwei Mesh-Routing-Protokoll in den Standard 802.11s einzuführen. Aus meiner Sicht (Elektra) ohne eine solide Basis von Erfahrungen in der praktischen Nutzung der gewählten Protokolle zu haben. Schaltet man das in 802.11s definierte Routing ab, hat man einen leicht verbesserten Multipunkt-zu-Multipunkt-Modus zur Verfügung, der aber mit dem alten Ad-Hoc-Modus inkompatibel ist, aber eine ordentliche Basis für bewährte Meshroutingprotokolle bietet. Langfristig wird 802.11s den alten Ad-Hoc-Modus ablösen. Die Umstellung von Ad-Hoc auf 802.11s ist natürlich für bereits bestehenden Communities ein logistischer Aufwand.

Am besten gelingt das Meshing mit 802.11n WLAN-Chips von Atheros/Qualcom mit dem Linux-Treiber ath9k. ath9k kann jede Betriebsart gut. Chipsätze von Mediatek für 802.11ac gehen auch, aber die Treiber-Unterstützung für 802.11n im 2.4 GHz-Band bei Dual-Band-Geräten macht noch Probleme. Das 802.11ac WLAN von Qualcomm im 5 GHz-Band arbeitet mit binärer, geschlossener Firmware. Immerhin kann es 802.11s.

Verwendet man 802.11s im Mesh, sollte man auch alle anderen Geräte, die bisher im Ad-Hoc-Modus liefen auf 802.11s umstellen, damit die weiter miteinander funken können. 802.11s mit abgeschaltetem internen Routing ist gegenüber Ad-Hoc eher von Vorteil, da der Multipunkt-zu-Multipunkt-Modus von 802.11s gegenüber dem alten Ad-Hoc-Modus leichte Vorteile bietet. Dazu muss man aber das von 802.11s definierte interne Mesh-Routing abschalten und wie gehabt eines der »richtigen« Meshprotokolle wie OLSR, B.A.T.M.A.N., batman-adv, BMX, Babel etc. benutzen.
 
Leider ändert sich das Angebot geeigneter Router laufend und große Hersteller wie TP-Link wechseln von Hardware-Revision zu Hardware-Revision den Chipsatz. Bei kleinere Herstellern wie Dragino und GL.iNet ist das übersichtlicher. Bei GL.iNet geht der Hersteller des Chipsatzes aus der Bezeichnung des Geräts hervor. AR steht bei GL.iNet für Atheros/Qualcomm, MT für Mediatek.  

Die unter Freifunkern beliebten Outdoor-Router Nanostation M2, M5, Bullet und andere Geräte des Herstellers Ubiquity sind wegen ihrer hohen Stromaufnahme von etwa 4-6 Watt ungeeignet. Es gibt von Ubiquity vermutlich auch sparsame Modelle. Falls Ihr welche kennt, lasst es uns wissen. Nachfolgend ein paar empfehlenswerte Beispiele.

## Dragino

Ein kleiner chinesischer Hersteller aus Shenzhen, der Open-Hardware-Produkte mit OpenWRT für Maker, Hacker und WLAN-Community-Netzwerke herstellt. 

Disclaimer: Ich (Elektra) kenne den Inhaber Edwin Chen persönlich und habe mit ihm beim Design von zwei Open-Hardware- und Open-Software-Projekten (LibreMesh und Villatelco) zusammen gearbeitet.

#### Dragino MS14N-S

Dies ist die Indoor-Variante der Mesh-Potato 2.0, die Edwin zusammen mit Villagetelco entwickelt hat. Eines der Designziele war geringer Energieverbrauch und beste Unterstützung für WLAN-Meshnetzwerke. Alle freien Input-Output-Pins und die serielle Schnittstelle sind über einen Stecksockel exponiert, für den Dragino diverse Erweiterungsplatinen (Shields) anbietet. Es gibt reichlich Flash und RAM. Externe Antenne.

Nachteile:

* Diese Indoorversion braucht zusätzlich ein wasserdichtes Gehäuse.

* Nur Single-Stream-WLAN, aber mit einem für das Meshen bestens geeigneten Chipsatz.

* Setzt man ein Shield ein, sind die Pins für die serielle Schnittstelle verdeckt, da sie im gleichen Sockel sitzen.

* Ein USB 2.0 Port, z.B. für ein zweites WLAN-Interface per USB.

Preis: Etwa 44 Euro

#### Dragino Pan Model D - WIFi Outdoor IoT Appliance

Dies ist die Outdoor-Variante der Mesh-Potato 2.0 AWD mit Stromversorgung über passives Power-over-Ethernet, die Edwin Chen zusammen mit Villagetelco entwickelt hat. Alle freien Input-Output-Pins und die serielle Schnittstelle sind über einen Stecksockel exponiert, für den Dragino diverse Erweiterungsplatinen (Shields) anbietet. Es gibt reichlich Flash und RAM und sogar einen internen SD-Kartenslot, um den Massenspeicher zu erweitern. Es gibt intern eine USB-2.0-Anschlussmöglichkeit über vier Pins für ein zusätzliches USB-WLAN-Interface, denn die Mesh-Potato 2.0 AWD war als Dual-Band-Gerät konzipiert. Leider bietet Dragino die Dual-Band-Version in seinem Shop nicht an und Villagetelco vertreibt die Mesh-Potato 2.0 AWD nicht mehr. 

Nachteile:

* Nur Single-Stream-WLAN, aber mit einem für das Meshen bestens geeigneten Chipsatz.

* Setzt man ein Shield ein, sind die Pins für die serielle Schnittstelle verdeckt, da sie im gleichen Sockel sitzen.

Preis: Etwa 57 Euro

## GL.iNet

#### GL.iNet GL-AR300M16 mit Dual-Stream-MIMO (2T2R)

Ein kleiner Pocket-Router mit geringem Stromverbrauch, ausreichend Flash und RAM und einem für das Mesh passenden WLAN Chipsatz. Wird bereits mit OpenWRT geliefert. Benötigt ein wasserdichtes Gehäuse. Ist mit integrierten oder abnehmbaren Antennen erhältlich. Die Version mit abnehmbaren Antennen ist besser geeignet. Besitzt einen USB 2.0-Port. Daran könnte man ein zusätzliches USB-WLAN-Interface anschließen.

Preis etwa 31 Euro. 

**Nachteile: **

* Stromversorgung per USB mit 5 Volt. Für kleines Geld gibt es aber Spannungswandler, die die 12 Volt Spannung aus dem Bleiakku in 5 Volt verwandeln. Solche Geräte sind als preiswerte Autoadapter für Smartphones und Tablets.

* 4 Pins zur Nutzung der seriellen Schnittstelle müssen eingelötet werden.

Fazit: Klein, günstig, energiesparend und nahezu problemlos einzusetzen.

#### GL.iNet GL-AR150

Der kleine Bruder des GL.iNet GL-AR300M16. Einziger wesentlicher Unterschied: Dieses Modell ist nur Single-Stream und kostet drei Euro weniger.

## TP-Link

Das D am Ende der Modellbezeichnungen der chinesischen Marke TP-Link steht für Detachable (Abnehmbare Antenne). Von vielen Geräten gibt es zwei Versionen, die sich nur darin unterscheiden. Der Aufpreis für die Abnehmbarkeit der Antennen ist relativ teuer.

#### TP-Link WR940N mit Triple-Stream-MIMO (3T3R)


Der sehr günstige Router (ohne D am Ende) braucht nur rund 1,2 bis 1,5 Watt und kostet etwa 25 Euro. Das ist wunderbar energiesparend und mit Triple-Stream-MIMO und guten Rundstrahlantennen eine Menge Radio für kleines Geld. Er ist mein (Elektra) aktueller Favorit für ein Brot- und Butter-Gerät, da Löten für mich kein Problem darstellt und ich die Firmware so weit abspecken kann, bis es passt in den knappen Flash-Speicher passt. Seine Nachteile: 

* Nur 4 Megabyte Flash. Das ist sehr knapp bemessen und reicht gerade so, wenn man auf Features in der Firmware verzichtet. Manche Freifunk-Communities unterstützen Geräte mit 4 MB Flash nicht mehr. Der Trend geht in der Software leider stets dazu, mehr Platz und Ressourcen zu verbrauchen.

* Muss in ein wasserfestes und UV-stabiles Gehäuse eingebaut werden. Das ist kein großer Nachteil, denn im gleichen Gehäuse kann auch der Freifunk-OpenMPPT-Solarcontroller untergebracht werden. 

* Die drei gut funktionierenden rundstrahlenden Antennen sind nicht abschraubbar. Hier muss man eigentlich nichts ändern, ausser man möchte unbedingt andere Antennen (z.B. Richtantennen) anschließen. Dafür sind die Antennenkabel übersichtlich auf die Platine gelötet. Das Problem lässt sich also mit einem Lötkolben leicht beheben.

* Die Pins der seriellen Schnittstelle sind nicht bestückt. Das ist bei dieser Art von Geräten üblich, um Kosten zu sparen. Vier Pins müssen eingelötet werden. Eine billige und leichte Übung.

* Zwei sehr kleine Widerstände an der seriellen Schnittstelle sind nicht bestückt und diese jeweils zwei Pads müssen überbrückt werden. Das wäre kinderleicht, wenn sie nicht so klein wären. An dieser Stelle sollte man sich von einer Person helfen lassen, die einen feinen Lötkolben, eine feine Pinzette, eine ruhige Hand und gute Augen hat.

Fazit: Wenig Flash, aber wer löten kann, kann für kleines Geld eine Menge damit anstellen. 

#### TP-Link WR1043ND mit Triple-Stream-MIMO (3T3R)

Haben wir selbst nicht getestet, die aktuelle Hardware-Revision sollte aber ähnlich sparsam sein. Mit 35 Euro etwas teurer. Dafür ausreichend Flash und mit abnehmbaren Antennen. Der Gigabit-Port ist für einen Solarrouter eigentlich überflüssig.

Nachteile: 

* Braucht ein wasserdichtes Gehäuse, in dem auch gleich der Solarcontroller eingebaut werden kann.

* Auch hier muss man die serielle Schnittstelle mit Pins bestücken, wie eigentlich immer.

* Bei neueren Hardware-Revisionen muss auch hier eine Brücke an der seriellen Schnittstelle eingelötet werden.

Fazit: Gutes Gerät.

#### TP-Link Archer C7 AC1750 mit Triple-Stream-MIMO (3T3R)

Dual-Band und in beiden Bändern mit Triple-Stream-MIMO (3T3R) und zwei USB 2.0-Ports

Für etwa 3 Watt Energieverbrauch und etwa 80 Euro bekommt man insgesamt sechs MIMO-Streams in zwei Frequenzbändern und ein leistungsstarkes Gerät. Leider sind die 2,4 GHz Antennen nur intern. Da man aber den Lötkolben sowieso benutzen muss, um wie üblich die Pins der seriellen Schnittstelle zu bestücken, kann man das gleich ändern. Oder man verwendet Richtantennen nur im 5 GHz-Band. Auch hier könnte man wieder zusätzlich die Anzahl der Interfaces per USB erweitern.

Nachteil:

* Kostet deutlich mehr, aber leistet auch viel mehr.

* 3 Watt Stromverbrauch sind gut, aber im Winter wird es mit 50 Watt Solarmodulkapazität sicher prekär. Besser 100 Watt nehmen.

* Das 802.11ac WLAN von Qualcomm im 5 GHz-Band arbeitet mit binärer, geschlossener Firmware. Es kann 802.11s, aber kein Ad-Hoc.

Fazit: Leistungsstarkes Gerät für den kleinen Solar-Backbone. Man kann die MIMO-Streams aufteilen und in mehrere Richtungen mit Richtantennen funken. Bessere Antennen bringen Reichweite und Geschwindigkeit, sie verbrauchen aber trotzdem keinen Strom, weil sie passiv sind. 


## 2. Der Freifunk-OpenMPPT

Der Freifunk-OpenMPPT ist ein programmierbarer Open-Source und Open-Hardware Solarladeregler mit sogenanntem Maximum-Power-Point-Tracking.  MPP-Tracking bedeutet, dass der Solarregler die Spannung des Solarmoduls im Punkt größter Ausgangsleistung berechnet und elektronisch nachführt, so dass der größtmögliche Energieertrag entsteht. Dadurch läßt sich der Ladestrom – je nach Batterieladestand und Temperatur – gegenüber einem einfachen PWM-Laderegler um bis zu 40% steigern. Der Freifunk-OpenMPPT besitzt eine serielle Schnittstelle, über die er seine  Betriebsdaten ausgibt und über die er auch gesteuert und seine Firmware neu geflasht werden kann.

Links ein Fertiggerät im Modulgehäuse, rechts ein Bausatz.

![Freifunk-OpenMPPT als Fertiggerät und Bausatz](/images/openmppt-fertiggeraet-bausatz.jpg)

Es gibt unterschiedliche Leistungsstufen des Freifunk-OpenMPPT. Modell A ist für kleinere Anlagen bis 50 Watt Solarmodulleistung ausgelegt, Modell B für 100 Watt und Modell C (in Planung) für 300 Watt. 

![Prototyp von Freifunk-OpenMPPT Typ B](/images/Prototyp_Typ_B.jpg)

Der Freifunk-OpenMPPT sind primär gedacht für die Versorgung und Überwachung von energieautonomen Freifunk-Routern oder überall da, wo man eine kleine und effiziente unabhängige Stromversorgung braucht, insbesondere dann, wenn man ihre Betriebsdaten auch aus der Ferne überwachen möchte.

## Funktionen des Freifunk-OpenMPPT-Solarcontrollers

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


Eine detaillierte Beschreibung des Freifunk-OpenMPPT findet Ihr [hier](http://elektrad.info/download/Freifunk-OpenMPPT-Handbuch-26-August-2017.pdf) in der Bau- und Betriebsanleitung. 

## 3. Bleiakkus

Es wird ein Bleiakku des Typs AGM oder Gel mit 12 Volt Nennspannung verwendet. Solarmodulgröße und Akkugröße sollten in einem sinnvollen Verhältnis stehen. Für ein Solarsystem mit einem 50 Watt Solarmodul ist ein Akku mit 17 Ah oder mehr empfehlenswert. Der Grund: Ist der Akku zu klein, wird er zu schnell geladen und altert deshalb schneller. Auch beim Entladen macht ein kleiner Akku schnell schlapp und altert wegen der tieferen Entladungen schneller.

Um die Speicherkapazität zu erhöhen, können auch mehrere Bleiakkus mit gleicher Spannung parallel geschaltet werden. Das ISEMS-System und der Freifunk-OpenMPPT lassen sich prinzipiell auch für Akkus mit anderer Chemie anpassen, wie Lithium-Ionen oder Lithium-Eisen-Phosphat. Bleiakkus sind preiswert, robust und können auch bei Minusgraden geladen werden. Li-Ionen-Akkus müssten dagegen zum Laden geheizt werden. Das höhere Gewicht von Bleiakkus sollte im stationären Betrieb keinen großen Nachteil darstellen. Je nach Typ des Bleiakkus beträgt die Lebensdauer 5 Jahre (AGM) bis 10 Jahre (Gel), vorausgesetzt das System wurde richtig dimensioniert und installiert. **Hinweis: Starterbatterien sind für Solarbetrieb ungeeignet.** Wer ganz arm ist, kann sein Glück auch mit abgehalfterten PKW- oder LKW-Akkus versuchen. Besser sind aber gebrauchte Traktions-, Alarmanlagen- oder USV-Akkus. Führt man solche Akkus einer Zweitverwertung zu, können tatsächlich Kosten gespart werden.


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
