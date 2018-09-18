---
title: OpenMPPT Firmware
url: /documentation/firmware
draft: false
---


# Kommunikation mit dem Freifunk-OpenMPPT
***
# Allgemein

Der Freifunk-OpenMPPT-Solarcontroller verfügt über eine **RS232**-Schnittstelle mit 3.3 Volt Logikpegel (ausschließlich 3.3 V, für Standard-RS232-Pegel oder 5 Volt TTL-Pegel ist ein Pegelwandler notwendig, da der Mikrocontroller des OpenMPPT sonst beschädigt werden kann). Die Kommunikationsparameter für die serielle Schnittstelle:

		9600 Baud, 8N1
		
keine Hardware- oder Software-Flusskontrolle.


# Empfangen der Daten vom Freifunk-OpenMPPT

Der Freifunk-OpenMPPT Solarkontroller sendet mindestens einmal pro Minute einen Datensatz über seinen Betriebszustand über die serielle Schnittstelle an den angeschlossenen Router. Ist die ISEMS-Software auf dem Router installiert, werden die Daten nach

		/tmp/mmpt.log

geschrieben und von der ISEMS-Firmware ausgewertet und aufbereitet.


# Übertragen von Konfigurationsbefehlen an den Freifunk-OpenMPPT

Vorausgesetzt, dass die serielle Schnittstelle richtig konfiguriert und angeschlossen ist, kann im laufenden Betrieb jeweils ein Konfigurationskommando vom Router an den Mikrocontroller des Freifunk-OpenMPPT gesendet werden. Das geschieht mit dem Kommandozeilentool
 
 		echo
 

## Über die serielle Schnittstelle konfigurierbar sind: ###

### Router-Reset-Timer (W)

Hierbei handelt es sich um einen nach unten zählenden Timer. Nach Ablauf des Timers wird der Router für 5 Sekunden stromlos gesetzt und der Zähler beginnt von neuem. 

Beispiel: 

		echo “W=2880” > /dev/ttyXXX

Der Befehl setzt den Router-Reset-Timer auf 2880 Minuten (48 Stunden). Dieses Setting wird im nicht-flüchtigen Speicher des  Freifunk-OpenMPPT abgelegt.  Der Befehl *W=* erwartet eine Angabe in Minuten, im Bereich von 60 Minuten bis 42200 Minuten - eine Stunde bis 29 Tage. Es ist nicht vorgesehen, diese Funktion komplett abzuschalten.  Manche Geräte funktionieren klaglos im Dauerbetrieb über Monate. Trotzdem würde wir sicherheitshalber ab und zu den OpenMPPT einen Neustart durchführen lassen.

**Wozu braucht man so einen Timer?**

Es kommt öfters mal vor, dass ein Router »hängt«. Fehlfunktionen dieser Art kommen gerne, z.B. in WLAN-Treibern vor. Idealerweise sollte das nie passieren, aber manche Geräte bleiben doch hin und wieder in unregelmäßigen Abständen hängen und benötigen einen Neustart. Zwar gibt es in OpenWRT einen Software-Watchdog, aber oft erkennt er das Problem nicht. Dann läuft das Gerät fröhlich als Zombie weiter und man kommt aus der Ferne nicht mehr an die Software ran. Dann heißt es kurz aus- und wieder einschalten.

Bei einem energieautarken Netzwerkknoten an einem einsamen, schwer zugänglichen Ort macht ein scheintotes Gerät eine Menge Ärger. In diesem Fall ist man als Administratorin froh, wenn man selbst und auch die Nutzer wissen, dass sich das System von selbst nach einem bestimmten Zeitraum in einen funktionierenden Zustand versetzt, ohne dass man auf einen entfernten Berg steigen muss, um einmal kurz von Hand den "Stecker zu ziehen". 

Der Schönheitfehler: Das System startet regelmäßig neu und setzt z.B. einmal pro Tag um 4 Uhr Nachts für eine halbe Minute aus, auch wenn es nicht erforderlich wäre.

## Powerdown-Timer (P)

Der Powerdown-Timer ist das Gegenstück zum Router-Reset-Timer: Er schaltet die am Lastausgang angeschlossenen Verbraucher - in unserem Fall natürlich den oder die Router – nach Ablauf des Timers wieder ein. Das spart Energie, z.B. Nachts, im Winter, wenn Energie knapp ist.

Beispiel: 

		echo “P=12” > /dev/ttyXXX

schaltet direkt und ohne Gnade nach Absetzen des Kommandos den angeschlossenen Router für 12 Minuten aus. Der Befehl *P=*  wird nicht gespeichert, aber sofort ausgeführt. Ausserdem setzt   *P=*  nach Ablauf der eingestellten Auszeit den Router-Reset-Timer auf den voreingestellten Wert zurück. Die Totzeit von *P=*  kann zwischen einer Minute und dem programmierten Maximalwert des Router-Reset Timers vorgegeben werden. Also Vorsicht, wenn da 29 Tage drinstehen. Sonst darf man doch auf den Berg ḱlettern!

### Ein- und Ausschaltspannung des Tiefentladeschutzes (oN und ofF)

Bleiakkus, egal ob in der Bauart mit flüssiger Säure, Gel oder Flies, mögen Tiefentladungen nicht. Entlädt man sie unter eine bestimmte Restspannung, verlieren sie dramatisch an Kapazität. Deshalb ist es zwingend, einen Tiefentladeschutz zu haben. 

Unter Last ist die Spannung kleiner, als wenn die Last abgeschaltet ist. Wären Einschaltwert und Ausschaltwert gleich, würde der Verbraucher ständig aus- und wieder eingeschaltet. Es ergibt sich sonst ein Zyklus: Verbraucher an, Spannung sinkt, Verbraucher aus, Spannung steigt, Verbraucher an usw usf.

Deshalb besitzt ein Tiefentladeschutz einen Ausschaltwert und einen Einschaltwert. Dazwischen gibt es einen Bereich, in dem der Tiefentladeschutz nicht wieder einschaltet: Die sogenannte Hysterese. 

In den Grundeinstellungen schaltet der Freifunk-OpenMPPT-Solarcontroller die Last bei 11,7 Volt Akkuspannung ab. Überschreitet der Akku 12,3 Volt, wird die Last wieder eingeschaltet. Das sind erprobte, praxisorientierte Werte. Im Normalfall gibt es daran nichts zu ändern, außer man ist Expertin und hat ein besonderes Anforderungsprofil im Sinn. So kann man z.B. schon bei einem höheren Wert abschalten, um die Tiefe der Entladezyklen zu reduzieren, was die Lebensdauer des Akkus verlängert. Ein Beispiel: Wir haben einen öffentlichen Hotspot in einer Parkanlage, der sich etwa drei Stunden nach Einbruch der Dunkelheit abschalten soll. 

Die Lebensdauer eines Akkus ist von der Betriebsdauer und der Anzahl und die Tiefe der Lade-Entladezyklen abhängig. In diesem Fall muss man aber auch die Einschaltspannung erhöhen. Eine entsprechende Hysterese muss immer vorgegeben sein, ist sie zu klein, gehen die angeschlossenen Verbraucher ständig an und aus.

Beispiel:

		echo "N=12600" > /dev/ttyXXX

schaltet den Lastausgang bei Überschreiten von 12,6 Volt ein.

		echo "F=12000" > /dev/ttyXXX** 

schaltet die Verbraucher bei Unterschreiten von 12,0 Volt aus.

Beide Settings werden im nicht-flüchtigen Speicher des Freifunk-OpenMPPT abgelegt. 

