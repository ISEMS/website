---
Title: FAQ
menu: header
---

# Can I save money in the long term with a solar node?

First of all, you have to realize that supplying a battery-backed autonomous system with solar energy throughout the year is a bit more expensive than using electricity from the power outlet, if energy from the grid is already in place. After all, we not only have to produce electricity but also store it. The process of charging and discharging must be electronically monitored, controlled and ideally optimized. Of course, all this costs effort and money.

But if a Wi-Fi community has to pay an electrician and a roofer to get power from the grid on the roof because the owner of the building demands it, investing in a solar system for a smaller location will pay off immediately.

A small, economical WLAN router uses around 8-10 euros of electricity per year in operation on the conventional power grid. This is money we can save. If there were no battery wear, the extra effort would be amortized over the years alone on the savings in the electricity bill. Generating a kilowatt-hour of solar power costs about 0.05 euros with large solar modules, if you operate a solar module for 20 years. Once installed, subsequent electricity price increases no longer play a role.

A solar module with 50 watts of power costs 50-60 euros and generates about 800 kWh of electricity in Berlin in 20 years. In an island system, the solar module produces less, because excess energy is not consumed or stored, when consumers consume less than the solar panel can deliver and the battery is already full. The Freifunk-Open-MPPT Type B will have an excess energy output, e.g. to charge via USB smartphones, tablets, power banks.

Unfortunately, in battery-backed systems there is battery wear, which, depending on the type of battery, causes costs again after 5 to 10 years of operation, if it is properly designed and installed. If it isn't, the battery will wear out sooner.

Therefore, it is very worthwhile to minimize the battery wear. In a poorly dimensioned and built system, the batteries age much faster, which can reduce the fun with a photovoltaic autonomous system.

An AGM lead-acid battery has to be replaced after about 5 years of operation, if used properly. Very good gel batteries last up to 10 years. Other costs are not applicable and the remaining hardware should last for at least 20 years, unless destroyed by external influences (vandalism, theft, lightning). You are probably updating the router or expanding the system much sooner.

#### A solar system without a rechargeable battery is cheaper after a few years than a system with mains power

It would only work during the day, though. For some applications, this can be an option.

The ISEMS design can not work without a battery. During normal operation, the battery should only discharge by about 10-20% overnight. A typical AGM battery loses 40% of its capacity during 1300 discharge cycles of 30% depth (from 100% full to 70% full). Only after several days without any considerable sun irradiation in the dark season, it may discharge deeper. For a few cycles per year, this can be tolerated.

It is important to keep the number of deep discharge cycles as small as possible.

The Freifunk-Open-MPPT can be configured to shut down the system as soon as the battery is slightly discharged and only turned on when the battery is full. As a result, the battery life would approach the shelf life. Even if one just stores a battery in a cool place and frequently compensates self-discharge by recharging it, it will be worn out after a number of years. 


# Are single-board computers like Raspberry Pi and the like also suitable for ISEMS?

If you want to run the ISEMS Web-App on it, the answer is "Yes, of course. A good choice." Even a low-cost single-board computer has more CPU, RAM, and storage than a small WiFi router, consumes relatively low power and produces no noise, so it is ideal for hosting the ISEMS web app. It can be connected to the ISEMS mesh via WiFi or Ethernet. 

If you want to run the single board computer with solar power as well, the RaspberryPi Zero W is hard to beat since it consumes very low power and can connect to the ISEMS mesh via WiFi. It is also small, low cost, sufficient, albeit a bit slow.

If you want to use an Raspberry Pi or the like as a solar powered mesh node itself, the answer is "Yes, but..."

* At least multi-core SBCs (single board computers) are relatively power-hungry. Raspberry 3B and 3B+ are therefore not the first choice for low cost solar powered operation. On the other hand, the Zero W under low CPU load consumes very low power, just 0.5 Watt at 5 Volt, with WiFi and Bluetooth running. By disabling WiFi, the power consumption drops to 0.35 Watt, when idle.

* Advanced WiFi operation modes and range are usually not the strength of their integrated WiFi solutions. Most USB-WiFi dongles have similar issues. The WiFi performance of their integrated radio interfaces and antennas is limited in terms of range, versatility and data throughput. They lack features that one might miss.

* Advanced WiFi chipsets and drivers can emulate two or more virtual wireless interfaces on one physical wireless interface. (Confusingly, virtual wireless interfaces are named VAPs = Virtual Access Point by the industry, even though they can be APs, stations, ad-hoc or 802.11s depending on the capabilities of the chipsets and drivers).

* For "real" multipoint-to-multipoint mesh networking operation, one needs to have at least one 802.11s or ad-hoc mode interface available. The Zero W can do ad-hoc, but not 802.11s.

* In general, one may implement a fake version of a mesh, if you can run at least one AP-VAP and one Client-VAP per physical WiFi interface, to build multi-hop-chains of interconnected AP+Client nodes. However, such a solution can not work as a full mesh, but this can be sufficient. Such a pseudo mesh networking structure resembles a tree with branches. For the IoT-Community it is usually enough to claim that they have an actual mesh network.

* Most wireless communities are used to run at least two virtual WiFi interfaces per physical interface on their mesh nodes: 1 Accesspoint VAP and 1 Ad-hoc VAP or one 802.11s VAP. There is no support for 802.11s in the Hard-MAC Broadcom WiFi + Bluetooth chips used on board the Zero W, Raspberry 3B and 3B+ and it can only run either AP or ad-hoc, but not both at the same time.

* Hard-MAC chipsets are often limited by the number of peers they can handle in AP or ad-hoc mode. Usually it works with up to 7 peers that are link-local, but not more. 

* You can not set up the link distance. This is required to make wireless long distance links work.


You can easily connect Raspberry Pi's (and the like) to the Freifunk-Open-MPPT solar controller and run the ISEMS data logger and data analysis software and all kinds of sensors and a HAT and the ISEMS Web App and so on and so on. All you need to read data from the Freifunk-Open-MPPT are the software components **stty**, Lua, UCI (optional). Connecting the serial ports of the Pi and the Freifunk-Open-MPPT solar controller just requires three jumper cables, as the serial port is already available on the Pi's pin header.

As a side note:

We have been hacking and playing with the Rasperry Zero W and mesh networking in ad-hoc mode, while running it as a Bluetooth Network Accesspoint. This way we can surf the mesh and the Internet via Bluetooth. While being much slower (around 100-130 KByte/s on the side of Bluetooth Network Accesspoint client), the power consumption of the Zero W is very low and also the wireless power consumption on the side of the tablet, smartphone, laptop is only about 10% or less, compared to WiFi. So their batteries last much longer if you always stay connected to the local wireless network.

# Does the ISEMS software work without mesh?

Yes, it is universal.

# Why are you focusing on mesh networks?

Radio is a broadcast medium on the physical layer. So every device in range already receives the data that is transmitted on the same channel. The reason that stations can't communicate directly with each other on MAC layer in the traditional Accesspoint-Client model is actually artificial, if one considers this fact. The reason why the development of WiFi historically went the way from the first point-to point links to a hub and spoke model probably happened due to established hierarchical thinking, MAC implementation and management considerations, despite the obvious lack of effectivity:

If two stations in an AP network exchange data, their communication is reduced to half the network bandwidth, in the best case. Consider station A sending data to station B. Station A sends data to AP X, AP X sends it to station B. Instead of one transmission from A to B, there are two. To make matters worse: In an office situation, station A and station B might be devices on the same table, 30 cm away from each other and 50 meters away from X. A transmission from A to B could take place as one transmission at maximum speed in ad-hoc mode, but instead it takes two transmissions via AP X at much slower speed, which again is divided in half.

It is possible to built larger wireless networking solutions without mesh networking, but our main reason would be if the WiFi radios can not be set up to operate in multipoint-to-multipoint mode reliably, as is the case with most consumer devices. Nevertheless, a mesh routing protocol is always an advantage, otherwise you have to enter or fix routes by hand, or one might use a different routing protocol for classic Internet infrastructure, but they are not actually suitable for radio applications.

Community networks such as Freifunk or commercial wireless service providers use point-to-point or point-to-multipoint mode primarily for fast backbone connections. At least for Freifunk the reasons are regulatory issues and driver stability considerations. For this purpose, several fast and energy hungry routers per site are used, which are connected via a switch. This is not suitable for solar operation because the solar system would be quite expensive. For a solar powered backbone site you have to reach deeper into the bag of tricks.

# What pros and cons have multi-radio setups?

Having multiple interfaces per node substantially increases data throughput and reduces latency. This also increases the power consumption. Per Wi-Fi interface you have to expect a consumption of about 0.5-1 watts. That doesn't sound like much, but consider that it will operate 24h a day. For a low-cost, low-energy mesh node to get started, you should use a Wi-Fi device with just a Wi-Fi interface or a low-power dual-band device that works reliably with OpenWRT in multipoint-to-multipoint mode.

## Is there a ready-to-use ISEMS free-wireless firmware for my router?

Yes and no. For the Mesh-Potato AWD aka Dragino MS14 and the TP-Link WR940N we did a generic free-radio firmware with OLSR, but different free-radio communities have different firmwares with different routing protocols. Here you can install ISEMS as an OpenWRT package or as a generic installation.

## How does the generic tarball installation work?

TBD

## What are the system requirements on the ISEMS solar nodes?

Linux, Lua, stty, the already existing shell (ash or better), UCI.

## What do you think about USB WiFi dongles?

The number of WiFi interfaces per device can be extended via USB, if there is at least one USB host port. To save energy they might be switched on or off. However, USB WiFi chipsets are usually not really that great. As a wireless client, they all work more or less. Unfortunately, we only know one USB Wi-Fi chipset, which works reasonably well at the moment:

Ralink / Mediatek RT5572
