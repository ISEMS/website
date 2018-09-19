---
title: ISEMS Startseite
---

#Was ist das Independent Solar Energy Mesh System (ISEMS)?

Das Independent Solar Energy Mesh System ist eine Softwarelösung zum Betreuen von energieautarken Solarroutern, entwickelt vor dem Hintergrund und zur Erweiterung von Community-(Mesh)-Netzwerken.

![Mobiler Solarknoten auf dem Tempelhofer Feld](/images/freifunk-mast-thf-klein.jpg)

Das Konzept baut auf dem Freifunk-OpenMPPT-Solarcontroller auf und ist dazu vorgesehen, unabhängige Netzknoten an schwer zu erschließenden Standorten mit Solarenergie zu betreiben und zu managen. 

![Hardware](/images/Blockschaltbild-Foto-klein.png)

Das ISEMS-System besteht aus einer Web-App, die eine Übersicht über die Betriebsdaten und Fehlermeldungen aller Solarknoten bereit stellt. Die Web-App lässt sich auf einem Kleincomputer wie dem Raspberry Pi hosten. In den Solarroutern arbeitet eine Datenlogger- und Analysesoftware, die die Daten des lokalen Systems aufbereitet. Die Daten aller beteiligten Solarknoten werden von der Web-App abgerufen und zu einer Übersicht verarbeitet.

![Physikalischer Layer und Softwarelayer](/images/Hardware-Software-Graphs.jpg)


Die Statusinformationen der einzelnen Solarknotens können von den Usern auch lokal und dezentral über einen Web-Browser eingesehen werden, da jeder Solarknoten einen eigenen kleinen Web-Server besitzt. 

![ISEMS HTML-Statusseite eingebettet in Freifunk-Luci](/images/ISEMS-Router-Status-HTML-Embedded-in-LUCI.png)

Auf der untersten Hardware- und Software-Ebene von ISEMS befindet sich die ISEMS-Firmware für den Freifunk-OpenMPPT-Solarcontroller, eine Elektronik auf der Basis von Open-Source und Open-Hardware. Der Freifunk-OpenMPPT-Solarcontroller ist die Ausgangsbasis des Projektes.

![Platine des Freifunk-OpenMPPT-Reglers Typ A](/images/freifunk-mppt-innen.jpg)

Das typische Anwendungsszenario von ISEMS: Solarnodes verbinden sich mit dem bestehenden Meshnetzwerk einer Community oder bilden lokale Netze, die nur aus Solarknoten bestehen.  Jeder Knoten stellt auch einen WLAN-Hotspot bereit, mit dem sich Endgeräte verbinden können, um das Mesh zu nutzen. Solarknoten mit ISEMS können preiswert nahezu überall aufgestellt werden.

##Wo macht der Einsatz eines solarbetriebenen Meshknotens Sinn?

Überall da, wo es kein Stromnetz für Kommunikationstechnik gibt oder spontan ein drahtloses WLAN-Netzwerk gebraucht wird. Solche Anwendungsszenarien gibt es nicht nur in Community-Netzwerken, sondern auch in Krisengebieten, nach Katastrophen, Stromausfällen, in Flüchtingslagern oder Schwellen- und Entwicklungsländern. Auch in reichen Ländern wie Deutschland, wo es ausserhalb der Ballungsgebiete Funklöcher gibt, kann ISEMS sinnvoll eingesetzt werden.

Durch Solarenergie lassen sich z.B. erhöhte Standorte für Community-Netzwerke erschließen, wo es keinen Strom gibt: Auf einem Berg, der zwischen zwei Dörfern die Funkstrecke blockiert. Auf einem Dach ohne Strom, weil der Eigentümer nicht will, dass man Löcher bohrt. Für die Wasserstand-Messstation am Fluss, für geologische Messungen auf einem Gletscher oder Vulkan...

##Warum liegt der Fokus von ISEMS auf Meshnetzwerken?

Der Vorteil von Meshnetzwerken ist, dass sich jeder Knotenpunkt im Mesh mit beliebig vielen anderen Knoten verbinden kann ohne eine Master-Client-Hierarchie koordinieren zu müssen. Meshknoten arbeiten funktechnisch im Multipunkt-zu-Multipunkt-Modus – jeder Knoten kann mit jedem Knoten direkt kommunizieren, sofern sie sich in Funkreichweite befinden. Ein Meshroutingprotokoll sorgt darüber hinaus automatisch dafür, dass auch Knoten ausserhalb der direkten Reichweite erreichbar sind, indem alle Knoten als Vermittler (Relaisstationen) arbeiten und die Kommunikation weiterleiten. Fällt ein Knoten aus, sucht das Meshroutingprotokoll automatisch nach alternativen Routen. Kommen Knoten hinzu, werden sie automatisch in das Netz eingebunden. Für ISEMS ist das ein großer Vorteil. Man kann in einem Gebiet ISEMS-Solarknoten verteilen und hat eine laufende Kommunikationsinfrastuktur. 

In der am meisten stromsparenden Low-Cost-Variante braucht man nur ein WLAN-Radio pro ISEMS-Station. Mit ein wenig mehr Aufwand und zwei WLAN-Radios pro Gerät bekommt man bedeutend mehr Performance und niedrigere Latenzen.

**Meshing ist für ISEMS von großem Vorteil, aber für den Einsatz der Softwarelösung nicht zwingend.** Auf Grund der Vorteile bevorzugen wir die Vernetzung der Knotenpunkte per Funkmesh, aber es ist für den Einsatz der ISEMS-Software nicht grundsätzlich erforderlich, dass die Solarknoten meshen. Meshen vereinfacht die Anwendung und erhöht die Ausfallsicherheit. 

##Was kostet ein ISEMS-Solarknoten?

Für ein einfaches, preiswertes und effizient konzipiertes System, das im Dauerbetrieb z.B. in Norddeutschland das ganze Jahr funktioniert, muss man im Selbstbau etwa 200-250 Euro für Material ausgeben.

Hier ein Beispiel:

        Router WR940N 25 Euro 
        Wasserdichtes, UV-beständiges Gehäuse 20 Euro 
        Akku Kung-Long 12 V 18 Ah 40 Euro 
        Solarmodul 50 Watt 60 Euro 
        Freifunk-Open-MPPT Solarcontroller 40 Euro 
        Kleinteile (Befestigungsmaterial, Schrauben, Kabel) 20 Euro


In dieser Beispielrechnung sind keine externen Antennen aufgeführt. Der Solarnode mit rundstrahlenden Antennen kann z.B. auf einem Bergrücken stehen und von mehreren Dörfern aus einigen Kilometern Entfernung mit guten Richtantennen angefunkt werden. Es erzeugt kaum Windlast und kann an einem leichten Mast montiert werden.

#Zum Aufbau eines ISEMS-Solarknotens werden folgende Komponenten benötigt:

1. WLAN-Router. Es sollte ein energiesparendes Modell sein, das von OpenWRT unterstützt wird und eine serielle Schnittstelle eingebaut hat (das haben praktisch alle, aber meistens muss man Pins bestücken). 

2. Freifunk-OpenMPPT-Solarladeregler mit Temperatursensor. Zur Zeit gibt es eine Version für Solarmodule bis zu 50 Watt (Typ A) und Prototypen bis zu 100 Watt (Typ B) Eine Version bis 300 Watt ist in Planung. Typ A kostet ohne Gehäuse 40 Euro, Typ B voraussichtlich 60 Euro.

3. EBleiakku vom Typ Blei-Gel oder Blei-AGM mit 12 Volt Nennspannung. Das System lässt sich prinzipiell auch für Akkus mit anderer Chemie anpassen, wie Lithium-Ionen oder Lithium-Eisen-Phosphat. Bleiakkus sind preiswert, robust und können auch bei Minusgraden geladen werden. Li-Ionen-Akkus müssten dagegen zum Laden geheizt werden. Das höhere Gewicht von Bleiakkus sollte im stationären Betrieb keinen großen Nachteil darstellen. Je nach Typ des Bleiakkus beträgt die Lebensdauer 5 Jahre (AGM) bis 10 Jahre (Gel), vorausgesetzt das System wurde richtig dimensioniert und installiert. **Hinweis: Starterbatterien sind für Solarbetrieb ungeeignet.** Wer ganz arm ist, kann sein Glück auch mit abgehalfterten PKW- oder LKW-Akkus versuchen. Besser sind aber gebrauchte Traktions-, Alarmanlagen- oder USV-Akkus. Führt man solche Akkus einer Zweitverwertung zu, können tatsächlich Kosten gespart werden.

4. Solarmodul mit typisch 50 Watt für 12 Volt Systeme und einer Spannung im maximalen Leistungspunkt um 18 Volt für Freifunk-OpenMPPT-Regler Typ A oder Typ B. Ausreichend für ein System mit einem Radio-Interface oder einem sehr sparsamen System mit zwei Radios.

5. Kleinteile wie Befestigungsmaterial, Kabel, eine Sicherung, ein wasserdichtes Gehäuse.

#Geeignete WLAN-Router

Wir sind bestrebt, die Kosten pro Knoten möglichst gering zu halten. Wichtig ist dazu die Wahl eines energiesparenden Routers. Greift man hier zu einem falschen Modell, entstehen hohe Folgekosten, weil sich der Aufwand für die Energieversorgung erheblich verteuert.

Für ISEMS verwenden wir keine teuren Meshrouter von kommerziellen Herstellern, die proprietäre und inkompatible Produkte anbieten, sondern freie Software und das freie Embedded-Linux OpenWRT, mit dem wir preiswerte Router zum Meshbetrieb umflashen. Auch ISEMS ist freie Software und der verwendete Freifunk-Solarcontroller ist Open-Hardware und Open-Software.
 
Leider ändert sich das Angebot geeigneter Router lausfend. Die unter Freifunkern beliebten Router Nanostation M2, M5, Bullet und andere Geräte des Herstellers Ubiquity sind mit einer Stromaufnahme von etwa 4-6 Watt völlig ungeeignet. Nachfolgend ein paar empfehlenswerte Beispiele.

##Dragino

Ein kleiner chinesischer Hersteller aus Shenzhen, der Open-Hardware-Produkte mit OpenWRT für Maker, Hacker und WLAN-Community-Netzwerke herstellt. 

Disclaimer: Ich (Elektra) kenne den Inhaber Edwin Chen persönlich und habe mit ihm beim Design von zwei Open-Hardware- und Open-Software-Projekten (LibreMesh und Villatelco) zusammen gearbeitet.

####Dragino MS14N-S

Dies ist die energiesparende Indoor-Variante der Mesh-Potato 2.0, die Edwin zusammen mit Villagetelco entwickelt hat. Eines der Designziele war geringer Energieverbrauch und beste Unterstützung für WLAN-Meshnetzwerke. Alle freien Input-Output-Pins und die serielle Schnittstelle sind über einen Stecksockel exponiert, für den Dragino diverse Erweiterungsplatinen (Shields) anbietet. Es gibt reichlich Flash und RAM. Externe Antenne.

Nachteile:

* Diese Indoorversion braucht zusätzlich ein wasserdichtes Gehäuse.

* Nur Single-Stream-WLAN, aber mit einem für das Meshen bestens geeigneten Chipsatz.

* Setzt man ein Shield ein, sind die Pins für die serielle Schnittstelle verdeckt, da sie im gleichen Sockel sitzen.

* USB 2.0 Port, z.B. für ein zweites WLAN-Interface per USB.

Preis: Etwa 44 Euro

####Dragino Pan Model D - WIFi Outdoor IoT Appliance

Dies ist die energiesparende Outdoor-Variante der Mesh-Potato 2.0 AWD mit Stromversorgung über passives Power-over-Ethernet, die Edwin Chen zusammen mit Villagetelco entwickelt hat. Alle freien Input-Output-Pins und die serielle Schnittstelle sind über einen Stecksockel exponiert, für den Dragino diverse Erweiterungsplatinen (Shields) anbietet. Es gibt reichlich Flash und RAM und sogar einen internen SD-Kartenslot, um den Massenspeicher zu erweitern. Es gibt intern eine USB-2.0-Anschlussmöglichkeit über vier Pins für ein zusätzliches USB-WLAN-Interface, denn die Mesh-Potato 2.0 AWD war als Dual-Band-Gerät konzipiert. Leider bietet Dragino die Dual-Band-Version in seinem Shop nicht an und Villagetelco vertreibt die Mesh-Potato 2.0 AWD nicht mehr. 

Nachteile:

* Nur Single-Stream-WLAN, aber mit einem für das Meshen bestens geeigneten Chipsatz.

* Setzt man ein Shield ein, sind die Pins für die serielle Schnittstelle verdeckt, da sie im gleichen Sockel sitzen.

Preis: Etwa 57 Euro

##GL.iNet

####GL.iNet GL-AR300M16 mit Dual-Stream-MIMO (2T2R)

Ein kleiner Pocket-Router mit geringem Stromverbrauch, ausreichend Flash und RAM und einem für das Mesh passenden WLAN Chipsatz. Wird bereits mit OpenWRT geliefert. Benötigt ein wasserdichtes Gehäuse. Ist mit integrierten oder abnehmbaren Antennen erhältlich. Die Version mit abnehmbaren Antennen ist besser geeignet. Besitzt einen USB 2.0-Port. Daran könnte man ein zusätzliches USB-WLAN-Interface anschließen.

Preis etwa 31 Euro. 

**Nachteile: **

* Stromversorgung per USB mit 5 Volt. Für kleines Geld gibt es aber Spannungswandler, die die 12 Volt Spannung aus dem Bleiakku in 5 Volt verwandeln. Solche Geräte sind als preiswerte Autoadapter für Smartphones und Tablets.

* 4 Pins zur Nutzung der seriellen Schnittstelle müssen eingelötet werden.

Fazit: Klein, günstig, energiesparend und nahezu problemlos einzusetzen.

####GL.iNet GL-AR150

Der kleine Bruder des GL.iNet GL-AR300M16. Einziger wesentlicher Unterschied: Dieses Modell ist nur Single-Stream und kostet drei Euro weniger.

##TP-Link

Das D am Ende der Modellbezeichnungen der chinesischen Marke TP-Link steht für Detachable (Abnehmbare Antenne). Von vielen Geräten gibt es zwei Versionen, die sich nur darin unterscheiden. Der Aufpreis für die Abnehmbarkeit der Antennen ist relativ teuer.

####TP-Link WR940N mit Triple-Stream-MIMO (3T3R)


Der sehr günstige Router ohne D am Ende braucht nur rund 1,2 bis 1,5 Watt und kostet etwa 25 Euro. Das ist wunderbar energiesparend und eine Menge Radio für kleines Geld. Er ist mein (Elektra) aktueller Favorit für ein Brot- und Butter-Gerät, da Löten für mich kein Problem darstellt. Seine Nachteile: 

* Nur 4 Megabyte Flash. Das ist knapp bemessen und reicht gerade so. Manche Freifunk-Communities unterstützen Geräte mit 4 MB Flash nicht mehr.

* Muss in ein wasserfestes und UV-stabiles Gehäuse eingebaut werden. Das ist kein großer Nachteil, denn im gleichen Gehäuse kann auch der Freifunk-OpenMPPT-Solarcontroller untergebracht werden. 

* Die drei gut funktionierenden rundstrahlenden Antennen sind nicht abschraubbar. Hier muss man eigentlich nichts ändern, ausser man möchte unbedingt Richtantennen anschließen. Dafür sind die Antennenkabel übersichtlich auf die Platine gelötet. Das Problem lässt sich also mit einem Lötkolben leicht beheben.

* Die Pins der seriellen Schnittstelle sind nicht bestückt. Das ist bei dieser Art von Geräten üblich, um Kosten zu sparen. Vier Pins müssen eingelötet werden. Eine billige und leichte Übung.

* Zwei sehr kleine Widerstände an der seriellen Schnittstelle sind nicht bestückt und diese zwei Pads müssen jeweils überbrückt werden. Das wäre kinderleicht, wenn sie nicht so klein wären. An dieser Stelle sollte man sich von einer Person helfen lassen, die einen feinen Lötkolben, eine feine Pinzette, eine ruhige Hand und gute Augen hat.

Fazit: Wenig Flash, aber wer löten kann, kann für kleines Geld eine Menge damit anstellen. 

####TP-Link WR1043ND mit Triple-Stream-MIMO (3T3R)

Haben wir selbst nicht getestet, die aktuelle Hardware-Revision sollte aber ähnlich sparsam sein. Mit 35 Euro etwas teurer. Dafür ausreichend Flash und mit abnehmbaren Antennen. Der Gigabit-Port ist für einen Solarrouter eigentlich überflüssig.

Nachteile: 

* Braucht ein wasserdichtes Gehäuse, in dem auch gleich der Solarcontroller eingebaut werden kann.

* Auch hier muss man die serielle Schnittstelle mit Pins bestücken, wie eigentlich immer.

* Bei neueren Hardware-Revisionen muss auch hier eine Brücke an der seriellen Schnittstelle eingelötet werden.

Fazit: Gutes Gerät.

####TP-Link Archer C7 AC1750 mit Triple-Stream-MIMO (3T3R)

Dual-Band und in beiden Bändern mit Triple-Stream-MIMO (3T3R) und zwei USB 2.0-Ports

Für etwa 3 Watt Energieverbrauch und etwa 80 Euro bekommt man insgesamt sechs MIMO-Streams in zwei Frequenzbändern und ein leistungsstarkes Gerät. Leider sind die 2,4 GHz Antennen nur intern. Da man aber den Lötkolben sowieso benutzen muss, um wie üblich die Pins der seriellen Schnittstelle zu bestücken, kann man das gleich ändern. Oder man verwendet Richtantennen nur im 5 GHz-Band. Auch hier könnte man wieder zusätzlich die Anzahl der Interfaces per USB erweitern.

Nachteil:

* Kostet deutlich mehr, aber leistet auch viel mehr.

* 3 Watt Stromverbrauch sind gut, aber im Winter wird es mit 50 Watt Solarmodulkapazität sicher prekär. Besser 100 Watt nehmen.

* Das 802.11ac WLAN von Qualcomm im 5 GHz-Band arbeitet mit binärer, geschlossener Firmware. Es kann 802.11s, aber kein Ad-Hoc.

Fazit: Leistungsstarkes Gerät für den kleinen Solar-Backbone. Man kann die MIMO-Streams aufteilen und in mehrere Richtungen mit Richtantennen funken. Antennen bringen Reichweite und Geschwindigkeit, brauchen trotzdem keinen Strom, weil sie passiv sind. 


##Kann man mit einem Solarknoten langfristig Geld sparen?

Zunächst muss man feststellen: Ein akkugepuffertes Inselsystem über das ganze Jahr mit Solarenergie zu versorgen ist etwas teurer als Strom aus der Steckdose. Immerhin müssen wir Strom nicht nur produzieren, sondern auch speichern. Der Prozess des Ladens und Entladens muss elektronisch überwacht, geregelt und idealerweise optimiert werden. All das kostet natürlich Aufwand und Geld. 

Wenn aber eine WLAN-Community einen Elektriker und einen Dachdecker dafür bezahlen muss, damit sie Strom auf einem Hochhausdach bekommt, weil der Besitzer des Gebäudes das verlangt, rechnet sich die Investition in ein Solarsystem für einen kleineren Standort sofort.

Ein kleiner, sparsamer WLAN-Router verbraucht im Betrieb am herkömmlichen Stromnetz etwa 8-10 Euro Strom pro Jahr. Dieses Geld spart man ein. Gäbe es keinen Akkuverschleiß, würde sich der Mehraufwand im Lauf der Jahre alleine über die Einsparung bei der Stromrechnung amortisieren. Eine Kilowattstunde Solarstrom zu erzeugen kostet mit großen Solarmodulen nur etwa 0.05 Euro, wenn man ein Solarmodul über 20 Jahre betreibt. Einmal installiert, spielen nachfolgende Strompreiserhöhungen keine Rolle mehr. 

Ein Solarmodul mit 50 Watt Leistung kostet 50-60 Euro und erzeugt in Berlin in 20 Jahren etwa 800 kWh Strom. 

Leider gibt es aber in batteriegepufferten Systemen den Akkuverschleiß, der abhängig vom Akkutyp nach 5 - 10 Jahren Betrieb erneut Kosten verursacht.

Deshalb lohnt es sich sehr, den Akkuverschleiß zu minimieren. In einem falsch dimensionierten und aufgebauten System altern die Akkus sehr viel schneller, was den Spass an einer photovoltaischen Inselanlage reduzieren kann.

Anderseits muss ein AGM-Bleiakku nach etwa 5 Jahren Betriebsdauer ersetzt werden. Andere Kosten fallen nicht an und die übrige Hardware sollte mindestes 20 Jahre halten, sofern sie nicht durch äußere Einwirkung zerstört wird (Vandalismus, Diebstahl, Blitzschlag).

####Ein Solarsystem ohne Akku wäre billiger als ein System mit Strom aus der Steckdose

Es würde aber nur tagsüber funktionieren. Für manche Anwendungen ist das sogar eine Option. 

Das ISEMS-Design kann nicht ganz ohne Akku arbeiten. Im Normalbetrieb sollte sich der Akku über Nacht nur um etwa 10-20% entladen. Nur bei längeren Flauten in der dunklen Jahreszeit sollte er sich tiefer entladen. 

Es gilt, die Anzahl der tiefen Entladezyklen möglichst klein zu halten.

Der Freifunk-Open-MPPT kann aber so konfiguriert werden, dass das System abgeschaltet wird, sobald der Akku geringfügig entladen wird und nur dann eingeschaltet wird, wenn der Akku voll ist. Dadurch würde sich die Akkulebensdauer bis zur Haltbarkeit der maximalen Lagerdauer annähern.




#Gehen auch Raspberry Pi und Co?

Zunächst: Ein Einplatinen-Computer ist ideal um die ISEMS Web-App zu hosten. Im Prinzip eignet sich ein solches Gerät auch an Stelle eines Routers mit OpenWRT. Auch jedes andere Embedded-Linux-System, in dem eine Shell (Ash oder besser), **stty**, Lua und UCI installiert sind, und das energiesparend ist, eignet sich im Prinzip. Man sollte sich aber darüber klar sein: Funken und insbesondere Meshen ist nicht die Stärke solcher Geräte, falls sie das überhaupt können. Die Performance ist beschränkt, was Reichweite, Vielseitigkeit, Datendurchsatz und Treiberstabilität angeht. Wenn aber ein ISEMS-Knoten z.B. nur überwiegend Messdaten sammelt und verschickt, oder nur das Solarsystem fernüberwacht werden soll, kann ein Einplatinencomputer passend sein, der sich nur als WLAN-Client mit dem Mesh verbindet.

##Wieviel taugt USB-WLAN?

Bei der Vorstellung der geeigneten Router haben wir erwähnt, dass per USB die Anzahl der WLAN-Schnittstellen erweitert werden kann. Ausserdem kann man sie abschalten, um Strom zu sparen. Das Problem ist: So richtig toll sind sie alle nicht. Als WLAN-Client funktionieren sie alle mehr oder weniger. Leider kennen wir nur einen USB-WLAN-Chipsatz, der leidlich zum Meshen funktioniert: 

Ralink/Mediatek RT5572

#Welcher WLAN-Modus und welcher WLAN-Chipsatz?
Für ein »echtes« Meshnetzwerk braucht man pro Knotenpunkt mindestens ein WLAN-Interface, dass stabil im Ad-Hoc-Modus oder nach 802.11s funkt. Der Grund: Wir brauchen zum »echten« Meshen die Multipunkt-zu-Multipunkt-Betriebsart von WLAN. 

Heute gibt es zwei Multipunkt-zu-Multipunkt-Betriebsarten zur Auswahl: 

* Ad-Hoc (Alte Schule ;)

* 802.11s (Die Neue)

Die Organisation IEEE – Institute of Electrical and Electronics Engineers – hat sich vor ein paar Jahren dazu entschlossen, Meshing zur IEEE 802.11-Protokollfamilie hinzu zu fügen. Dabei dachte man auch gleich daran, ein Mesh-Routing-Protokoll einzuführen. Aus meiner Sicht (Elektra) ohne eine solide Basis von Erfahrungen in der praktischen Nutzung der gewählten Protokolle zu haben. Schaltet man das in 802.11s definierte Routing ab, hat man einen leicht verbesserten Multipunkt-zu-Multipunkt-Modus zur Verfügung, der aber mit dem alten Ad-Hoc-Modus inkompatibel ist, aber eine ordentliche Basis für bewährte Meshroutingprotokolle bietet. Langfristig wird diese Betriebsart den alten Ad-Hoc-Modus ablösen. Die Umstellung von Ad-Hoc auf 802.11s ist natürlich für bereits bestehenden Communities ein abschreckender Aufwand.

Am besten gelingt das Meshing mit 802.11n WLAN-Chips von Atheros/Qualcom mit dem Linux-Treiber ath9k. ath9k kann jede Betriebsart gut. Chipsätze von Mediatek für 802.11ac gehen auch, aber die Treiber-Unterstützung für 802.11n im 2.4 GHz-Band bei Dual-Band-Geräten macht noch Probleme. Das 802.11ac WLAN von Qualcomm im 5 GHz-Band arbeitet mit binärer, geschlossener Firmware. Immerhin kann es 802.11s.

Verwendet man 802.11s im Mesh, muss man auch alle anderen Ad-Hoc- Geräte auf 802.11s umstellen. Das ist eher von Vorteil, da 802.11s gegenüber dem alten Ad-Hoc-Modus Vorteile bietet. Dazu muss man aber das von 802.11s definierte Mesh-Routing abschalten und wie gehabt OLSR, B.A.T.M.A.N., BMX, Babel etc. benutzen.



Das Independent Solar Energy Mesh System macht es auch für Nichtexpert\*innen einfacher,
eigene und vom Stromnetz unabhängige Kommunikationsinfrastruktur aufzubauen.


Damit du dir dein eigenes Solarnetz oder einen Solarknoten bauen kannst brauchst du nur folgende Schritte zu befolgen:

- Router kaufen
- Batterie anschließen
- OpenMPPT installieren
- Firmware flashen

Das ISEMS Paket besteht dabei aus mehreren Teilen. Mehr dazu findest du in den Abschnitten
Hardware und Software.
