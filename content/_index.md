---
title: Home
---

# Was ist das Independent Solar Energy Mesh System (ISEMS)?

Das Independent Solar Energy Mesh System ist eine Softwarelösung zum Betreuen von energieautarken Solarroutern, entwickelt vor dem Hintergrund und zur Erweiterung von Community-(Mesh)-Netzwerken.

# Wo hilft ISEMS?

<div class="example">
    <div class='copy'>
        <h2> Schwer zugängliche Orte</h2>
        <p> ISEMS-Stationen können an Orten ohne bestehende Infrastruktur installiert
        werden und somit schwer zugängliche Orte mit einem Kommunikationsnetz versorgen.
        </p>
    </div>
    <img src="images/villages.svg">
</div>

<div class="example">
    <div class='copy'>
        <h2>In der Stadt</h2>
        <p> Da das ISEMS-System keine bestehende Infrastruktur benötigt, kann
        es einfach auf Hausdächern installiert werden, ohne Stromleitungen verlegen zu müssen. <p>
    </div>
    <img src="images/cities.svg">
</div>

<div class="example">
    <div class='copy'>
        <h2>Ad-Hoc</h2>
        <p>
            Die einfache Installation von ISEMS ermöglicht die spontane Versorgung von Notlagern oder Festivals.
        </p>
    </div>
    <img src="images/festivals.svg">
</div>


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

## Wo macht der Einsatz eines solarbetriebenen Meshknotens Sinn?

Überall da, wo es kein Stromnetz für Kommunikationstechnik gibt oder spontan ein drahtloses WLAN-Netzwerk gebraucht wird. Solche Anwendungsszenarien gibt es nicht nur in Community-Netzwerken, sondern auch in Krisengebieten, nach Katastrophen, Stromausfällen, in Flüchtingslagern oder Schwellen- und Entwicklungsländern. Auch in reichen Ländern wie Deutschland, wo es ausserhalb der Ballungsgebiete Funklöcher gibt, kann ISEMS sinnvoll eingesetzt werden.

Durch Solarenergie lassen sich z.B. erhöhte Standorte für Community-Netzwerke erschließen, wo es keinen Strom gibt: Auf einem Berg, der zwischen zwei Dörfern die Funkstrecke blockiert. Auf einem Dach ohne Strom, weil der Eigentümer nicht will, dass man Löcher bohrt. Für die Wasserstand-Messstation am Fluss, für geologische Messungen auf einem Gletscher oder Vulkan...

## Warum liegt der Fokus von ISEMS auf Meshnetzwerken?

Der Vorteil von Meshnetzwerken ist, dass sich jeder Knotenpunkt im Mesh mit beliebig vielen anderen Knoten verbinden kann ohne eine Master-Client-Hierarchie koordinieren zu müssen. Meshknoten arbeiten funktechnisch im Multipunkt-zu-Multipunkt-Modus – jeder Knoten kann mit jedem Knoten direkt kommunizieren, sofern sie sich in Funkreichweite befinden. Ein Meshroutingprotokoll sorgt darüber hinaus automatisch dafür, dass auch Knoten ausserhalb der direkten Reichweite erreichbar sind, indem alle Knoten als Vermittler (Relaisstationen) arbeiten und die Kommunikation weiterleiten. Fällt ein Knoten aus, sucht das Meshroutingprotokoll automatisch nach alternativen Routen. Kommen Knoten hinzu, werden sie automatisch in das Netz eingebunden. Für ISEMS ist das ein großer Vorteil. Man kann in einem Gebiet ISEMS-Solarknoten verteilen und hat eine laufende Kommunikationsinfrastuktur.

In der am meisten stromsparenden Low-Cost-Variante braucht man nur ein WLAN-Radio pro ISEMS-Station. Mit ein wenig mehr Aufwand und zwei WLAN-Radios pro Gerät bekommt man bedeutend mehr Performance und niedrigere Latenzen.

**Meshing ist für ISEMS von großem Vorteil, aber für den Einsatz der Softwarelösung nicht zwingend.** Auf Grund der Vorteile bevorzugen wir die Vernetzung der Knotenpunkte per Funkmesh, aber es ist für den Einsatz der ISEMS-Software nicht grundsätzlich erforderlich, dass die Solarknoten meshen. Meshen vereinfacht die Anwendung und erhöht die Ausfallsicherheit.

## Was kostet ein ISEMS-Solarknoten?

Für ein einfaches, preiswertes und effizient konzipiertes System, das im Dauerbetrieb z.B. in Norddeutschland das ganze Jahr funktioniert, muss man im Selbstbau etwa 200-250 Euro für Material ausgeben.

Hier ein Beispiel:

| Bauteil                                             |  Preis  |
|-----------------------------------------------------|--------:|
| Router WR940N                                       | 25 Euro |
| Wasserdichtes, UV-beständiges Gehäuse               | 20 Euro |
| Akku Kung-Long 12 V 18 Ah                           | 40 Euro |
| Solarmodul 50 Watt                                  | 60 Euro |
| Freifunk-Open-MPPT Solarcontroller                  | 40 Euro |
| Kleinteile (Befestigungsmaterial, Schrauben, Kabel) | 20 Euro |


In dieser Beispielrechnung sind keine externen Antennen aufgeführt. Der Solarnode mit rundstrahlenden Antennen kann z.B. auf einem Bergrücken stehen und von mehreren Dörfern aus einigen Kilometern Entfernung mit guten Richtantennen angefunkt werden. Es erzeugt kaum Windlast und kann an einem leichten Mast montiert werden.
