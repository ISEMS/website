---
title: FAQ
url: /FAQ/
draft: false
menu: header
layout: single
---

# Kann man mit einem Solarknoten langfristig Geld sparen?

Zunächst muss man feststellen: Ein akkugepuffertes Inselsystem über das ganze Jahr mit Solarenergie zu versorgen ist etwas teurer als Strom aus der Steckdose. Immerhin müssen wir Strom nicht nur produzieren, sondern auch speichern. Der Prozess des Ladens und Entladens muss elektronisch überwacht, geregelt und idealerweise optimiert werden. All das kostet natürlich Aufwand und Geld. 

Wenn aber eine WLAN-Community einen Elektriker und einen Dachdecker dafür bezahlen muss, damit sie Strom auf einem Hochhausdach bekommt, weil der Besitzer des Gebäudes das verlangt, rechnet sich die Investition in ein Solarsystem für einen kleineren Standort sofort.

Ein kleiner, sparsamer WLAN-Router verbraucht im Betrieb am herkömmlichen Stromnetz etwa 8-10 Euro Strom pro Jahr. Dieses Geld spart man ein. Gäbe es keinen Akkuverschleiß, würde sich der Mehraufwand im Lauf der Jahre alleine über die Einsparung bei der Stromrechnung amortisieren. Eine Kilowattstunde Solarstrom zu erzeugen kostet mit großen Solarmodulen nur etwa 0.05 Euro, wenn man ein Solarmodul über 20 Jahre betreibt. Einmal installiert, spielen nachfolgende Strompreiserhöhungen keine Rolle mehr. 

Ein Solarmodul mit 50 Watt Leistung kostet 50-60 Euro und erzeugt in Berlin in 20 Jahren etwa 800 kWh Strom. In einem Inselsystem produziert das Solarmodul weniger, da überschüssige Energie nicht abgerufen wird, d.h. wenn die Verbraucher weniger verbrauchen als das Solarmodul gerade liefern kann und der Akku schon voll ist. Der Freifunk-Open-MPPT Typ B wird einen Überschussenergieausgang haben, um z.B. über USB Smartphones, Tablets, Powerbanks zu laden.

Leider gibt es aber in batteriegepufferten Systemen den Akkuverschleiß, der abhängig vom Akkutyp nach 5 - 10 Jahren Betrieb erneut Kosten verursacht.

Deshalb lohnt es sich sehr, den Akkuverschleiß zu minimieren. In einem falsch dimensionierten und aufgebauten System altern die Akkus sehr viel schneller, was den Spass an einer photovoltaischen Inselanlage reduzieren kann.

Anderseits muss ein AGM-Bleiakku nach etwa 5 Jahren Betriebsdauer ersetzt werden. Sehr gute Gel-Akkus halten bis zu 10 Jahre. Andere Kosten fallen nicht an und die übrige Hardware sollte mindestes 20 Jahre halten, sofern sie nicht durch äußere Einwirkung zerstört wird (Vandalismus, Diebstahl, Blitzschlag).

#### Ein Solarsystem ohne Akku ist nach ein paar Jahren billiger als ein System mit Netzstrom

Es würde aber nur tagsüber funktionieren. Für manche Anwendungen ist das sogar eine Option. 

Das ISEMS-Design kann nicht ganz ohne Akku arbeiten. Im Normalbetrieb sollte sich der Akku über Nacht nur um etwa 10-20% entladen. Ein typischer AGM-Akku verliert durch 1300 Entladezyklen von 30% Tiefe (von 100% voll auf 70% voll) 40% seiner Kapazität. Nur bei längeren Flauten in der dunklen Jahreszeit sollte er sich tiefer entladen. 

Es gilt, die Anzahl der tiefen Entladezyklen möglichst klein zu halten.

Der Freifunk-Open-MPPT kann aber so konfiguriert werden, dass das System abgeschaltet wird, sobald der Akku geringfügig entladen wird und nur dann eingeschaltet wird, wenn der Akku voll ist. Dadurch würde sich die Akkulebensdauer bis zur Haltbarkeit der maximalen Lagerdauer annähern.


# Sind Single-Board-Computer wie Raspberry Pi und dergleichen für ISEMS geeignet?

Wenn man die ISEMS-Web-App in einem Raspberry Pi ausführen möchte, lautet die Antwort "Ja, natürlich. Eine gute Wahl." Selbst ein preisgünstiger Einplatinencomputer verfügt über mehr CPU, RAM und Speicher als ein kleiner WLAN-Router, verbraucht relativ wenig Strom und arbeitet geräuschlos. Daher eignet er sich ideal zum Hosten der ISEMS-Web-App. Es kann über WLAN oder Ethernet mit dem ISEMS-Netz verbunden werden.

Falls man den Single Board-Computer auch mit Solarstrom betreiben möchte, ist der RaspberryPi Zero W sehr stromsparend und kann über WLAN mit dem ISEMS-Netz verbunden werden. Er ist klein, kostengünstig, ausreichend, wenn auch etwas langsam.

Falls man einen Raspberry Pi als eigentlichen Solar-Mesh-Router verwenden möchten, lautet die Antwort "Ja, aber ..."

* Zumindest Multi-Core-SBCs (Single Board Computer) sind relativ leistungshungrig. Raspberry Pi 3B und 3B + sind daher nicht die erste Wahl für den kostengünstigen Betrieb mit Solarbetrieb. Auf der anderen Seite verbraucht der Zero W bei niedriger CPU-Last nur einen geringen Stromverbrauch von 0,5 Watt bei 5 Volt, auch wenn WLAN und Bluetooth aktiv sind. Durch die Deaktivierung von WLAN sinkt der Stromverbrauch im Leerlauf auf 0,35 Watt.

* Fortgeschrittene WLAN-Betriebsarten und -Funktionen sind nicht die Stärke der integrierten WLAN-Lösungen auf SBCs. Die WLAN-Leistung ihrer integrierten Funkschnittstellen und Antennen ist hinsichtlich Reichweite, Vielseitigkeit und Datendurchsatz begrenzt. Ihnen fehlen auch Funktionen, die man leicht vermissen kann.

* Gute WLAN-Chipsätze und -Treiber können zwei oder mehr virtuelle drahtlose Schnittstellen auf einer physischen drahtlosen Schnittstelle emulieren. (Verwirrenderweise werden virtuelle drahtlose Schnittstellen von der Industrie als VAPs = virtueller Accesspoint bezeichnet, obwohl sie je nach den Fähigkeiten der Chipsätze und Treiber APs, Clients, Ad-hoc oder 802.11s-Knoten sein können).

* Für ein "echtes" Multipoint-Multipoint-Mesh-Netzwerk muss mindestens der 802.11s- oder der Ad-hoc-Modus mit der WLAN-Schnittstelle verfügbar sein. Der Zero W kann den Ad-hoc-Modus, aber nicht 802.11s. Er kann also meshen.

* Man kann einen Pseudo-Mesh-Modus implementieren, wenn man mindestens ein AP-VAP und ein Client-VAP pro physischer WLAN-Schnittstelle konfiguieren kann, um Multi-Hop-Ketten aus miteinander verbundenen AP + Client-Knoten zu erstellen. Eine solche Kaskaden-Lösung kann jedoch nicht als vollwertiges Meshnetz arbeiten. In vielen Fällen kann das jedoch ausreichend sein. Eine solche Pseudo-Mesh-Netzwerkstruktur gleicht einer Baumstruktur mit Verzweigungen. Für die IoT-Marketing-Community ist ein solches Fake-Mesh in der Regel ausreichend, um zu behaupten, dass sie ein echtes Maschennetz haben ;)

* Die meisten WLAN-Communities sind es gewohnt, mindestens zwei virtuelle WLAN-Schnittstellen pro physischer WLAN-Schnittstelle auf ihren Mesh-Knoten einzurichten: Eine Accesspoint-VAP wird kombiniert mit einer Ad-hoc-VAP oder einer 802.11s-VAP. 802.11s wird von den in Zero W, Raspberry 3B und 3B + verwendeten WLAN + Bluetooth-Chips nicht unterstützt, und es kann nur entweder der AP oder Ad-hoc-Modus ausgeführt werden, jedoch nicht beides gleichzeitig.

* Hard-MAC-Chipsätze, wie in den Raspberry Pi's sind oft durch die Anzahl der Peers begrenzt, die sie im AP- oder Ad-hoc-Modus verarbeiten können. Normalerweise funktioniert es mit bis zu 7 Peers, die lokal per WiFi angebunden sind, aber nicht mehr.

* Das WiFi-ACK-Timing lässt sich nicht einstellen. Dies ist erforderlich, damit WLAN-Richtfunkstrecken funktionieren, die länger als 1-2 Kilometer sind.

Man kann SBCs wie die unterschiedlichen Raspberry Pi-Modelle (und ähnliche) einfach an den Freifunk-Open-MPPT-Solarregler anschließen und die ISEMS-Datenlogger- und Datenanalysesoftware sowie gleichzeitig alle Arten von Sensoren und ein HAT und die ISEMS-Webanwendung usw. anwenden. Zum Lesen von Daten aus dem Freifunk-Open-MPPT benötigt man lediglich die Softwarekomponenten **stty**, Lua, UCI. Für den Anschluss der seriellen Ports des Pi und des Freifunk-Open-MPPT-Solarreglers sind nur drei Jumper-Kabel erforderlich, da der serielle Port mit passendem Logikpegel bereits auf dem Pin-Header der Pi's verfügbar ist.

Nebenbei:

Wir haben mit der Anbindung an das Freifunk-Mesh-Netzwerk im Ad-hoc-Modus experimentiert, während der Zero W gleichzeitig als Bluetooth-Netzwerkzugriffspunkt dient. Auf diese Weise können wir über Bluetooth im Mesh und im Internet surfen. Die Datenrate der Bluetooth-Clients beim Surfen über den Bluetooth-AP des Zero W ist zwar langsamer (etwa 100-130 KByte/s), dafür geht der Stromverbrauch auf der Seite der Endgeräte (Smartphone, Laptop, Tablet) sehr stark zurück. Ihre Batterien halten also sehr viel länger, wenn Sie ständig mit dem lokalen drahtlosen Netzwerk verbunden sind.

# Funktioniert die ISEMS-Software auch ohne Mesh?

Ja, sie ist universell. 

# Warum fokussiert Ihr Euch auf Meshnetzwerke?

Funk ist ein Broadcastmedium auf der physikalischen Ebene, d.h. jedes Gerät in Reichweite empfängt sowieso die Daten, die auf demselben Kanal übertragen werden. Der Grund dafür, dass WLAN-Clients auf dem MAC-Layer im traditionellen Accesspoint-Client-Modell nicht direkt miteinander kommunizieren können, ist eigentlich artifiziell und entseht durch das Protokolldesign auf dem MAC-Layer. Der Grund, warum sich die Entwicklung von WiFi historisch von den ersten Punkt-zu-Punkt-Verbindungen zu einem Nabe-und-Speiche-Modell entwickelt hat, ist wahrscheinlich auf das etablierte hierarchische Denken, die Vereinfachung der MAC-Implementierung und Management-Überlegungen zurückzuführen.

Wenn zwei Clients in einem AP-Netzwerk Daten austauschen, wird ihre Kommunikation im besten Fall auf die Hälfte der Netzwerkbandbreite reduziert. Nehmen wir an, dass Client-Station A Daten an Station B sendet. Station A sendet die Daten an AP X, AP X sendet sie an Station B weiter. Anstelle einer direkten Übertragung von A nach B gibt es zwei. Das ist sogar oft noch wesentlich ineffizienter, als es zunächst erscheint: In einer Bürosituation befinden sich Station A und Station B möglicherweise auf einem Tisch, 30 cm voneinander entfernt und 50 Meter vom AP X entfernt, mit dem sie assoziiert sind. Eine direkte Übertragung von A nach B würde im Ad-Hoc-Modus in einem Sendevorgang bei maximaler Geschwindigkeit erfolgen, stattdessen braucht es zwei Übertragungen über AP X dazwischen, die wegen der Entfernung mit einer viel niedrigeren Geschwindigkeit abläuft und sich deshalb auch noch halbiert. Da greift man dann doch lieber zum Netzwerkkabel oder kopiert die Daten auf ein Trägermedium.

Es ist möglich, größere drahtlose Netzwerklösungen auch ohne Maschennetzwerke zu bauen. Unser Hauptgrund wäre jedoch, wenn die WLAN-Funkgeräte nicht für den zuverlässigen Betrieb im Multipoint-zu-Multipoint-Modus eingerichtet werden können, wie dies bei den meisten Endgeräten der Fall ist. Trotzdem ist der Einsatz eines Mesh-Routing-Protokoll auch in diesem Fall von Vorteil, ansonsten müssen Routen manuell eingeben oder korrigiert werden. Alternativ kann man auch ein anderes Routing-Protokoll für die klassische Internetinfrastruktur verwenden. Diese sind jedoch nicht, oder nur sehr bedingt, für Funkanwendungen geeignet.

Für Richtfunkverbidungen spielen diese Betrachtungen natürlich keine Rolle.

In Community-Netzwerken wie z.B. Freifunk oder von kommerziellen WLAN-Serviceprovidern wird der Punkt-zu-Punkt oder Punkt-zu-Multipunkt-Modus überwiegend für schnelle Backbone-Verbindungen angewendet. Dafür kommen dann mehre schnelle und energiehungrige Router pro Standort zum Einsatz, die über einen Switch verbunden sind. Für Solarbetrieb ist das ungeeignet, weil die Solaranlage ziemlich teuer wäre. Für einen solarbetriebenen Backbone-Standort muss man etwas tiefer in die Trickkiste greifen. Aber auch hier kommen natürlich Routingprotokolle zum Einsatz.

# Welche Vor-und Nachteile haben Multi-Radio-Setups?

Hat man mehrere Interfaces pro Knoten, steigert das den Datendurchsatz wesentlich und verringert die Latenz. Damit steigt auch der Stromverbrauch. Pro WLAN-Interface muss man bei einem sparsamen Gerät mit einem Verbrauch von etwa 0,5-1 Watt rechnen. Das klingt nach wenig, läppert sich aber auf Dauer. Für einen möglichst preiswerten, sparsamen Meshknoten für den Einstieg solltet Ihr ein WLAN-Gerät mit nur einem WLAN-Interface oder ein sparsames Dual-Band-Gerät verwenden, dass mit OpenWRT stabil im Multipunkt-zu-Multipunkt-Modus funktioniert.

## Gibt es eine fertige ISEMS-Freifunk-Firmware für meinen Router?

Jein. Für die Mesh-Potato AWD aka Dragino MS14 und den TP-Link WR940N haben wir eine generische Freifunk-Firmware mit OLSR gemacht, aber unterschiedliche Freifunk Communities haben unterschiedliche Firmwares mit unterschiedlichen Routingprotokollen. Hier kann man ISEMS als OpenWRT-Paket oder als generische Installation nachinstallieren.

## Wie funktioniert die generische Installation per Tarball?

TBD

## Was sind die Systemvoraussetzungen auf den ISEMS-Knoten?

Linux, Lua, stty, die sowieso schon vorhandene Shell (ash oder besser), UCI.

## Wieviel taugt USB-WLAN?

Bei der Vorstellung der geeigneten Router haben wir erwähnt, dass per USB die Anzahl der WLAN-Schnittstellen erweitert werden kann. Ausserdem kann man sie abschalten, um Strom zu sparen. Das Problem ist: So richtig toll sind sie alle nicht. Als WLAN-Client funktionieren sie alle mehr oder weniger. Leider kennen wir nur einen USB-WLAN-Chipsatz, der leidlich zum Meshen funktioniert: 

Ralink/Mediatek RT5572

