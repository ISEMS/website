---
title: FAQ
url: /FAQ/
draft: false
menu: header
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


# Eignen sich auch Raspberry Pi und Co?

Zunächst: Ein sparsamer Einplatinen-Computer mit mehr CPU, RAM und Massenspeicher ist ideal um die ISEMS Web-App zu hosten. Man kann ihn per Funk oder per Ethernet mit einem Solarknoten verbinden, wobei Ethernet sich i.d.R. besser eignet, weil es stabiler und zuverlässiger ist. Auch kann man Raspberry Pi und Co problemlos an den Freifunk-OpenMPPT-Solarconroller anschließen und die ISEMS Datenlogger- und Datenanalysesoftware darin laufen lassen. Dazu braucht man nur die Softwarekomponenten **stty**, Lua, UCI und eine serielle Verbindung zum Freifunk-OpenMPPT-Solarcontroller mit drei Jumper-Kabeln.

Als WLAN-Router eignet sich ein RaspPi aber weniger. Funken und insbesondere Meshen ist nicht die Stärke von Einplatinen-Computern. Die WLAN-Performance ihrer integrierten Schnittstellen ist beschränkt, was Reichweite, Vielseitigkeit, Datendurchsatz und Treiberstabilität angeht. Wenn aber ein RaspPi nur Daten sammeln und verschicken soll und sich nur als WLAN-Client mit dem Mesh verbindet, geht es. Für einen Umweltsensor o.ä. bieten Raspberry Pi und Co viele interessante Funktionen.


# Funktioniert die ISEMS-Software auch ohne Mesh?

Ja, sie ist universell. 

# Warum fokussiert Ihr Euch auf Meshnetzwerke?

Man kann natürlich auch Geräte ohne Mesh untereinander vernetzen, wenn deren Radios nicht im Multipunkt-zu-Multipunkt-Modus, sondern im Punkt-zu-Punkt oder Punkt-zu-Multipunkt-Modus laufen. Ein Meshroutingprotokoll ist trotzdem immer von Vorteil, sonst muss man Routen von Hand eintragen, oder ein anderes Routingprotokoll für klassische Internet-Infrastruktur nutzen, die aber eigentlich nicht für Funkanwendungen taugen. 

In Community-Netzwerken wie z.B. Freifunk oder von kommerziellen WLAN-Serviceprovidern wird der Punkt-zu-Punkt oder Punkt-zu-Multipunkt-Modus überwiegend für schnelle Backbone-Verbindungen angewendet. Dafür kommen dann mehre schnelle und energiehungrige Router pro Standort zum Einsatz, die über einen Switch verbunden sind. Für Solarbetrieb ist das ungeeignet, weil die Solaranlage ziemlich teuer wäre. Für einen solarbetriebenen Backbone-Standort muss man etwas tiefer in die Trickkiste greifen.

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

