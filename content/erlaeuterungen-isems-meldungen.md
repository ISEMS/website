---
title: ISEMS Systemmeldungen
url: /documentation/system-messages
draft:false
---

# Erläuterung der ISEMS Systemmeldungen

## Normale Statusmeldungen

**»Healthy«**

Das ISEMS-System funktioniert einwandfrei. So sollte es immer sein :) 

**»Charging«**

Der Akku wird geladen. Das System läuft mit Solarenergie und speichert die Solarenergie im Akku, die gerade nicht verbraucht wird.

**»Discharging«**

Der Akku wird nachts oder bei sehr geringer Sonneneinstrahlung entladen. Das System verbraucht jetzt im Akku gespeicherte Solarenergie. Diese Meldung sollte bei Tag nicht erscheinen, ausgenommen in der Dämmerung oder bei sehr trüben Lichtverhältnissen. Findet während des Tages keine Ladung statt, deutet das auf ein sich ankündigendes Problem hin.

**»Fully charged«**

Der Akku ist vollständig aufgeladen. Das System läuft mit Solarenergie. Es ist Energieüberschuss vorhanden, der nicht gespeichert oder verbraucht wird. 

## Warnungen

#### »Warning: Battery level low. Increased battery wear«

**Bedeutung: Der Ladestand des Akkus hat 50% Ladestand unterschritten. Bei tiefem Ladestand sinkt die Lebensdauer des Akkus, die von Betriebsdauer und Entladetiefe abhängt.**

Diese Meldung sollte nur im Winter an manchen Tagen erscheinen. Tritt sie häufig oder gar im Sommer auf, kann das mehrere Ursachen haben:

* Der Akku ist zu klein dimensioniert oder seine Speicherkapazität hat durch Verschleiß abgenommen. **Abhilfe:** Die Akkukapazität durch Parallelschaltung von Akkus vergrößern oder größeren Akku installieren, bzw. verschlissenen Akku ersetzen.

* Das Solarmodul ist zu klein dimensoniert, es wird grundsätzlich mehr Energie verbraucht als produziert. **Abhilfe:** Ein zusätzliches Solarmodul oder ein größeres Solarmodul installieren. Dabei die maximale Belastbarkeit des Open-MPPT-Reglers beachten und eventuell durch leistungsstärkere Version ersetzen. Stromsparmechanismen aktivieren oder sparsameren Router verwenden.

* Das Solarmodul wird im Laufe des Tages abgeschattet (z.B. durch Äste von Bäumen.)  Das Solarmodul sollte sich von Sonnenaufgang bis Sonnenuntergang nicht im Schatten befinden. **Abhilfe:** Einen besseren Montageort suchen oder die Objekte entfernen, die zur Verschattung des Solarmoduls führen.

* Das Solarmodul ist falsch ausgerichtet. **Abhilfe:** Es sollte um die Mittagszeit frontal zur Sonne zeigen.

* Das Solarmodul ist verschmutzt (z.B. durch Laub, Vogelkot), vereist oder mit Schnee bedeckt. **Abhilfe: Das Solarmodul sollte relativ steil (45-55 Grad) montiert werden, so dass Verschmutzungen leicht vom Regen abgewaschen werden oder Schnee leicht herunter rutscht.** Die daraus resultierende Leistungseinbuße im Sommer ist leicht zu verschmerzen und im Winter passt der Winkel ausgezeichnet. So reinigt sich das Solarmodul in der Regel von selbst, ohne manuell einzugreifen. Die Unterkante des Solarmoduls sollte ausreichend Abstand zum Dach oder Boden haben, so dass sich anfallender Schnee in den Wintermonaten nicht vor dem Solarmodul auftürmt.

* **Wird tagsüber nicht geladen?** Dann ist kein Solarmodul angeschlossen oder der Anschluss ist unterbrochen. **Abhilfe: Solarmodul anschließen, Verbindungen prüfen.**

#### »Warning: Temperature sensor not connected«

**Bedeutung: Es ist kein Temperatursensor angeschlossen, oder die Verbindung zum Temperatursensor ist unterbrochen.**

Der Temperatursensor ist erforderlich, damit der Open-MPPT die Temperatur des Akkus messen und die maximale Ladespannung berechnen kann. Ohne Temperatursensor geht der Open-MPPT permanent von 20 Grad Akkutemperatur aus. Ist der Akku Temperaturen über 30 Grad und unter 10 Grad ausgesetzt, beschleunigt ein fehlender Temperatursensor den Akku-Verschleiß.

**Abhilfe: Temperatursensor anschließen, Kabel und Steckverbindungen prüfen.**

#### »Battery overheating«

**Bedeutung: Die Temperatur des Akkus ist zu heiß, sie überschreitet 42 Grad Celsius.**

Oberhalb von 42 Grad stellt der Open-MPPT das Laden zum Schutz des Akkus ein. Wenn die Umgebungstemperatur über 40 Grad liegt, lässt sich dieser Zustand kaum vermeiden. **Abhilfe: Der Akku sollte generell im Schatten und nicht in der Sonne stehen**.

#### »Low battery temperature«

**Bedeutung: Die Temperatur des Akkus ist sehr niedrig, sie unterschreitet -10 Grad Celsius.**

Das ist nicht weiter schlimm, allerdings reduziert sich vorübergehend die nutzbare Kapazität des Akkus. Werden Akkus mit flüssigem Elektrolyten verwendet, sollte berücksichtigt werden, dass diese bei sehr niedrigem Ladestand einfrieren können. 

#### »Warning: Energy storage capacity too small. Check battery size and/or wear«

**Bedeutung: Das Verhältnis zwischen Solarleistung und Akkukapazität ist ungünstig.**

Die Kapazität des Akkus und die maximale Leistung des Solarmoduls sollten in einem sinnvollen Verhältnis stehen. Allzu schnelles Laden und allzu schnelles Entladen beschleunigt den Akkuverschleiß bei jeder Art von Akku. Wird ein Solarakku mit unverhältnismäßig großem Ladestrom – größer als 1/5 seiner Nennkapazität – geladen, verkürzt sich die Lebensdauer.

Erscheint diese Meldung, schätzt die ISEMS-Software die Akkukapazität im Verhältnis zu angegebenen Solarmodulleistung als zu klein ein. Dieser Effekt tritt auch am Ende der Lebensdauer des Akkus auf, wenn die tatsächliche Kapazität des Akkus durch Verschleiß immer kleiner wird. Die auf dem Gehäuse aufgedruckte Angabe der Kapazität weicht immer stärker von der tatsächlichen Kapazität ab. Das ISEMS-System versucht, die verbleibende Speicherkapazität des Akkus abzuschätzen.

**Abhilfe:** Erscheint diese Meldung häufig und fällt das System bereits im Frühjahr und Herbst häufig aus, deutet das auf einen verschlissenen Akku hin.

**Bitte beachten:** Diese Funktion beruht auf Abschätzung des Ladezustands und des Akkuzustands und ist davon abhängig, dass auf der Seite des Routers die Konfigurationsdatei

		/etc/config/ffopenmppt

vorhanden ist, und dass dort korrekte Angaben bezüglich Stromverbrauch, Akkukapazität im Neuzustand und Solarmodulleistung angegeben sind.

Hier ein Beispiel:

		config ffopenmppt
		        option powersave '0'
		        # Rated solar module power in Watt
		        option solar_module_capacity '20'
		        # Average power consumption of router in Ampere (measured)
 		        option average_power_consumption '0.1'
 		        # Rated battery capacity in Amperehours
        		option rated_batt_capacity '7'


## Fehlermeldungen

#### »No information. Error: No communication with solar controller«

**Bedeutung: Keine Kommunikation zwischen Open-MPPT und Router. ISEMS fliegt im Blindflug.**

Auf keinen Fall ein Firmwareupdate des Routers aus der Ferne machen, da unbekannt ist, wann der Tiefentladeschutz oder der Watchdog die Stromzufuhr des Routers unterbricht. Dies würde den Router in einen Briefbeschwerer verwandeln, der nur durch fortgeschrittenes technisches Handauflegen repariert werden kann.

**Abhilfe:** Tritt der Fehler im laufenden Betrieb auf, ist vermutlich das Kabel der seriellen Verbindung zwischen Router und Open-MPPT unterbrochen oder die Steckverbindung abgezogen. 

###Tritt das Problem bei der ersten Installation auf, kommen mehrere Fehlermöglichkeiten in Frage:

* Die eingestellte Baudrate oder andere Einstellungen der seriellen Schnittstelle stimmen nicht. Es sind* 9600 Baud, 8N1*, keine Hardware-Flowcontrol.

* TX/RX-Leitungen der seriellen Schnittstelle vertauscht oder keine Masseverbindung zwischen Router und Open-MPPT.

* Kein kompatibler 3,3 Volt-Pegel der seriellen Schnittstelle. Abhilfe: Pegelwandler benutzen.

* Die serielle Schnittstelle des Routers ist belegt durch ein serielles Terminal-Login.

Folgendes muss in der Datei /etc/inittab stehen:

		#::askconsole:/usr/libexec/login.sh

Durch das vorangestellte Hashzeichen **#**  wird die üblicherweise aktivierte serielle Login-Konsole deaktiviert. Danach Router neu starten oder ***init q*** auf der Kommandozeile ausführen, um die Datei neu einzulesen.

* Die serielle Schnittstelle des Routers funktioniert generell nicht. 

Häufig erfordern preiswerte Router neben dem Bestücken von Pins einfache Modifikationen (Einlöten von Widerständen), damit die serielle Schnittstelle funktioniert. Nähere Informationen findet man für das jeweilige Modell/die jeweilige Hardwarerevision eines bestimmten Modells im [OpenWRT-Wiki.](https://wiki.openwrt.org/toh/start) 

* Masseschleife in der Stromversorgung. 

Sind die Kabel zwischen Router und OpenMPPT, die das negative Spannungspotential (Minus, Masse, 0 Volt) führen, zu lang oder zu dünn, schwebt der Nullpunkt abhängig vom Stromfluss (Ampere). Der Effekt: Es kommt zu Kommunikationsfehlern, oder die Kommunikation funktioniert nur in eine Richtung. Abhilfe: Bessere und/oder kürzere Masseverbindung.
