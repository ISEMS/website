---
Title: Hardware
menu: header
---
# Hardware

# To set up an ISEMS solar node, the following hardware components are required:

1. A wireless router. It should be an energy-efficient model that is supported by OpenWRT and has a serial port with 3.3 Volt TTL levels built in (practically all of them have this feature, but most of the time you need to populate pins with a solder iron).


2. A Freifunk OpenMPPT solar charge controller with temperature sensor. Currently there is a version for solar modules up to 50 watts (type A) available as a kit and there are prototypes up to 100 watts (type B). A powerful version that can handle up to 300 watts solar power is in the planning phase. A pre-soldered kit for type A costs 40 euros without housing, a kit for type B is expected to cost around 60 euros. 

3. A lead-gel or lead-AGM lead-acid battery with 12 Volt nominal voltage.

4. A solar panel with up to 50 Watts for 12 volt systems with a maximum power point of 18 volts for Freifunk OpenMPPT Type A regulators. This is sufficient for a system with one radio interface or a very economical two radio system. Solar modules of the same type can be connected in parallel.

5. Small parts such as mounting hardware, cables, a fuse, a waterproof housing.

## Diagramm

Here are the components of a running node example in an overview.

![Hardware](/images/Blockschaltbild-Foto-mittel.png)



# 1. Suitable WLAN-Routers

For ISEMS, we do not use expensive mesh routers from commercial vendors offering proprietary and incompatible products, but free software and the free embedded Linux OpenWRT, which we use to hack low-cost, low power wireless routers. ISEMS is also free software and the Freifunk solar controller used is open hardware and open software. We strive to keep the costs per solar node as low as possible. The important thing is to choose an energy-saving router. If you resort to a wrong model, high follow-up costs arise, because the energy supply costs considerably more. Another criterion is important if you want to mesh: The wireless chipset of the router must be able to build stable multipoint-to-multipoint connections.

#### Which WLAN mode and which WLAN chipset?
For a "real" mesh network you need at least one WLAN interface per node, which is stable in ad-hoc mode or in 802.11s. The reason: We need the multipoint-to-multipoint mode of WLAN for "real" Meshen. Today there are two multipoint-to-multipoint operating modes available in WLAN according to IEEE 802.11:

* Ad-Hoc (Old school ;)

* 802.11s (New, hot! ;)

A few years ago, the IEEE (Institute of Electrical and Electronics Engineers) decided to add an improved multipoint-to-multipoint operating mode to the IEEE 802.11 protocol family. The idea was to introduce two mesh routing protocols amongst an improved MAC layer protocol into the new mesh standard named 802.11s. In my view (Elektra) without having a solid base of experience in the practical use of the chosen mesh protocols. Disabling the routing defined in 802.11s provides a slightly improved multipoint-to-multipoint mode on MAC layer. 802.11s MAC layer is incompatible with the old ad hoc mode, hence 802.11s MAC mode and 802.11 ad-hoc mode are incompatible. However, 802.11s provides a solid foundation for proven mesh routing protocols, if you disable the routing features in 802.11s. In the long run, 802.11s will replace the old ad hoc mode. The conversion from Ad-Hoc to 802.11s is of course a logistical effort for already existing communities and it is still fine to use one or the other.

Meshing with Atheros / Qualcom's 802.11n Wi-Fi chips with the ath9k Linux driver still works best. Ath9k can do any mode of operation well. Mediatek's 802.11ac chipsets also work, but driver support for 802.11n in the 2.4GHz band on dual-band devices still causes problems. Atheros / Qualcomm's 802.11ac WLAN in the 5 GHz band uses binary, closed firmware. After all, it can be 802.11s.

If you use 802.11s in mesh, you need to switch all other devices that used to run in ad-hoc mode to 802.11s so that they can continue to connect with each other. 802.11s with internal routing turned off is more advantageous over ad-hoc because the multipoint-to-multipoint mode of 802.11s offers slight advantages over the old ad hoc mode. But you have to disable the 802.11s defined internal mesh routing and use one of the "right" mesh protocols like OLSR, B.A.T.M.A.N., batman-adv, BMX, Babel etc as is common practice in wireless community networks.
 
Unfortunately, the range of suitable routers is constantly changing, and major manufacturers such as TP-Link tend to change the chipset from hardware revision to hardware revision of their devices. For smaller manufacturers such as Dragino and GL.iNet this is less of a problem. They know that hackers and tinkerers are an important group amongst their customers, so they make it clear if they change the chipset. For example, for GL.iNet, the manufacturer of the chipset is the name of the device. AR stands for GL.iNet for Atheros / Qualcomm, MT for Mediatek.

The outdoor routers Nanostation M2, M5, Bullet and other Ubiquity devices are unsuitable for the use with solar power, as they have a rather high power consumption of about 4-6 watts. There are probably also economical models from Ubiquity. If you know any, let us know. Here are a few recommended examples.

## Dragino

A small Chinese manufacturer from Shenzhen, which manufactures open hardware products with OpenWRT for makers, hackers and Wi-Fi community networks.

Disclaimer: I (Elektra) personally know owner and founder Edwin Chen and have worked with him on the design of two open hardware and open software projects (LibreMesh and Villagetelco).

#### Dragino MS14N-S

This is the indoor version of the Mesh Potato 2.0 that Edwin has developed together with Villagetelco. One of the design goals was low power consumption and best support for Wi-Fi mesh networks. All unused general input-output pins (GPIOs) and the serial interface are exposed via a socket, for which Dragino offers various extension boards (shields). There is plenty of Flash and RAM. External antenna and port.

Advantages / Disadvantages:

* Ships with OpenWRT installed.

* This indoor version also requires a waterproof housing.

* Single-Stream-WiFi only, but with a chipset that is working great for mesh.

* If you use a shield, the pins for the serial port are hidden because they sit in the same socket.

* USB 2.0 Port, so you might add a second WiFi interface via USB.

Price: Around 44 Euro in Germany

#### Dragino Pan Model D - WIFi Outdoor IoT Appliance

This is the outdoor version of the Mesh-Potato 2.0 AWD powered by passive power-over-ethernet, developed by Edwin Chen together with the Villagetelco project. All unused general input-output pins (GPIOs) and the serial interface are exposed via a socket, for which Dragino offers various extension boards (shields). There is plenty of Flash and RAM and even an internal SD card slot to expand the mass storage. There is an internal USB 2.0 port via four pins for an additional USB wireless interface, because the Mesh Potato 2.0 AWD was designed as a dual-band device. Unfortunately, Dragino does not offer the dual-band version in its shop and Villagetelco no longer sells the Mesh Potato 2.0 AWD.

Advantages / Disadvantages:

* Outdoor device.

* Same as above.

Price: Around 57 Euro in Germany

## GL.iNet

#### GL.iNet GL-AR300M16 with Dual-Stream-MIMO (2T2R)

A small pocket router with low power consumption, enough flash and RAM and a WiFi chipset that perfectly works for the mesh. Already shipped with OpenWRT. Requires a waterproof case. Available with integrated or detachable antennas. The version with removable antennas is more suitable. Has a USB 2.0 port. This could be connected to an additional USB-WLAN interface.

Price about 31 euros.

** Advantages / Disadvantages: **

* Power supply via USB with 5 volts. DC-DC-step-down converters that convert the 12 volt voltage from the lead battery into 5 volts USB are available for cheap, though.

* 4 pins to use the serial interface must be soldered.

Conclusion: Small, inexpensive, energy-saving and easy to use.


#### GL.iNet GL-AR150

The little brother of the GL.iNet GL-AR300M16. Only key difference: This model is only single-stream and costs three euros less.


## TP-Link

The "D" at the end of the model designations of the Chinese brand TP-Link stands for Detachable (Detachable Antenna). Many devices have two versions that differ only in this feature. The surcharge for the removability of the antennas is relatively expensive.


#### TP-Link WR940N with Triple-Stream-MIMO (3T3R)

This very cheap router (without D at the end) only needs about 1.2 to 1.5 watts and costs about 25 euros. This is very energy efficient for triple-stream MIMO. The device also features three good omnidirectional antennas. That is a lot of radio for little money. It is my (Elektra) current favorite for a bread and butter device, since soldering is no problem for me and I can slim down the firmware until it fits in the tight flash memory. Its disadvantages:

* Only 4 megabytes of Flash. This is very tight and just enough if you go without any extra features in the firmware. Some free-radio communities no longer support devices with 4 MB of Flash. Unfortunately, the trend in software is always to consume more space and resources.

* Must be installed in a waterproof and UV-resistant housing. This is not a big disadvantage, because in the same housing the Freifunk OpenMPPT solar controller can be accommodated.

* The three well-functioning omnidirectional antennas can not be unscrewed. You do not have to change anything here unless you really want to connect other antennas (for example directional antennas). The antenna cables are soldered to the board. The problem can be solved easily with a soldering iron.

* The pins of the serial interface are not populated. This is common with this type of equipment to save costs. Four pins must be soldered. A cheap and easy exercise.

* Two very small resistors on the serial interface are not populated and these two pads must be bridged (with a 1k2 resistor on the RX side and 0 Ohm on the TX side, as seen from the routers perspective). That would be easy if these pads were not so darn small. At this point you should get help from a person who has a fine soldering iron, fine tweezers, a steady hand and good eyesight, if you are inexperienced.

Conclusion: Little Flash, but if you can solder and slim down the firmware, you can do a lot for such a small amount of money.

#### TP-Link WR1043ND with Triple-Stream-MIMO (3T3R)

I have not tested this device myself, the current hardware revision should be similarly low power. With 35 euros a bit more expensive than 940N. Enough flash and RAM with removable antennas. The gigabit port is actually superfluous for a solar router.

Disadvantage:

* Needs a waterproof housing, too.

* Again, you have to equip the serial port with pins, as always.

* In the case of newer hardware revisions, a bridge must also be soldered in at the serial interface (with a 1k2 resistor on the RX side and 0 Ohm on the TX side, as seen from the routers perspective).

Conclusion: Good device.

#### TP-Link Archer C7 AC1750 with Triple-Stream-MIMO in two bands(3T3R)

Dual band and in both bands with triple-stream MIMO (3T3R) and two USB 2.0 ports

For about 3 watts of energy consumption and about 80 euros you get a total of six MIMO streams in two frequency bands and a powerful device. Unfortunately, the 2.4 GHz antennas are only internal. However, since you have to use the soldering iron anyway to populate the pins of the serial interface as usual, you can change that immediately. Or one uses directional antennas only in the 5 GHz band. Again, you could expand the number of interfaces via USB again.

Disadvantage:

* Indoor device (but hard to beat)

* Costs much more, but also offers a lot more.

* 3 watts of power consumption are good, but in winter it is certainly precarious with 50 watts of solar module capacity. Better to take 100 watts.

Qualcomm's 802.11ac WLAN in the 5 GHz band works with binary, closed firmware. It can do 802.11s, but not "classic" ad-hoc mode.

Conclusion: Powerful device for the small solar backbone. You can split the MIMO streams and send them in multiple directions with directional antennas. Better antennas bring range and speed, but they still do not consume power because they are passive.

## 2. The Freifunk OpenMPPT

The Freifunk OpenMPPT is a programmable open-source and open-hardware solar charge controller with so-called maximum power point tracking. MPP tracking means that the solar controller calculates the voltage of the solar module at the point of highest output power and tracks it electronically, so that the highest possible energy yield is achieved. Depending on the battery charge level and temperature, the charging current can be increased by up to 40% compared to a simple PWM (pulse width modulation) charge controller. The Freifunk OpenMPPT has a 3.3 Volt serial interface through which it sends its operating data and it can also receive commands, configuration data and new firmware from the router.

On the left a finished device in a module housing, on the right a kit.

![Freifunk-OpenMPPT as finished device and kit](/images/openmppt-fertiggeraet-bausatz.jpg)

There are different power levels of the Freifunk OpenMPPT. Model A is designed for smaller systems up to 50 watts of solar module power, Model B for 100 watts and Model C (planned) for 300 watts.

![Prototyp of Freifunk-OpenMPPT Type B](/images/Prototyp_Typ_B.jpg)

The Freifunk OpenMPPT are primarily intended for the supply and monitoring of energy-autonomous free-wireless routers or wherever you need a small and efficient independent power supply, especially if you also want to monitor your operating data remotely.

## Features of the Freifunk OpenMPPT Solar Controller

* Serial interface with 3.3 volt TTL level.

* Solar charge controller with tracking of the solar generator voltage at the maximum power point (so-called maximum power point tracking)

* Increase of energy yield by efficient DC / DC-down converter with> 95% efficiency

* Deep discharge protection with programmable switch-on and switch-off point

* Monitoring of solar module open circuit voltage, input voltage in power point, battery voltage and battery temperature.

* Temperature controlled charging characteristic according to ** IU ** procedure

* Programmable Router Reset Timer (Watchdog)

* Powerdown timer to save energy

* Configurable deep discharge protection

* Works even without a router as a universally applicable solar charge controller with MPPT function.

* Firmware can be re-flashed via the bootloader.

A detailed description of the Freifunk OpenMPPT can be found [here](http://elektrad.info/download/Freifunk-OpenMPPT-Handbuch-26-August-2017.pdf)in the construction and operating manual.

## 3. Lead-acid batteries

An AGM or gel type lead acid battery with 12 Volt nominal voltage is used. Solar module size and battery size should be in a reasonable relationship. For a solar system with a 50 watt solar module, a battery with 17 Ah or more is recommended. The reason: If the battery is too small, it will charge too fast and therefore age faster. While discharging a small battery also discharges and wears out faster.

To increase the storage capacity, several lead batteries with the same voltage can be connected in parallel. In principle, the ISEMS system and the Freifunk OpenMPPT can also be adapted for rechargeable batteries with a different chemistry, such as lithium-ion or lithium-iron-phosphate. Lead acid batteries are inexpensive, robust and can be charged even at minus degrees. Li-ion batteries, on the other hand, would have to be heated for charging. The higher weight of lead-acid batteries should not be a big disadvantage in stationary operation. Depending on the type of lead-acid battery, the lifetime is 5 years (AGM) to 10 years (gel), provided the system has been correctly dimensioned and installed. ** Note: Starter batteries are unsuitable for solar operation. ** If you are very poor, you can try your luck with surplus car or truck batteries. But way better are used traction, alarm or UPS batteries. If such rechargeable batteries are recycled, costs can actually be saved. Please dispose off properly!


## Installation



## Video
<figure>
<div class="iframe-wrapper">
<iframe src="https://www.youtube-nocookie.com/embed/BxFpY2tsPtU?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
</div>
<figcaption>
This video shows the installation of a Freifunk OpenMPPT mast.
</figcaption>
</figure>
