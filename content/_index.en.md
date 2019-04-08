---
---

# What is the Independent Solar Energy Mesh System? (ISEMS)?

The Independent Solar Energy Mesh System is a open source software solution to monitor and maintain energy autonomous solar routers. The background of this project is the expansion of wireless community mesh networks into remote places or for disaster recovery.

# Where can ISEMS help you?

<div class="example">
    <div class='copy'>
        <h2>Remote places that lack infrastucture</h2>
        <p> ISEMS stations can be installed in locations without existing infrastructure, providing a hard-to-reach location with a communications network.
        </p>
    </div>
    <img src="/images/villages.svg">
</div>

<div class="example">
    <div class='copy'>
        <h2>In the city</h2>
        <p> Since the ISEMS system does not require an existing infrastructure, it can easily be installed on rooftops without having to lay power lines or drill holes. <p>
    </div>
    <img src="/images/cities.svg">
</div>

<div class="example">
    <div class='copy'>
        <h2>Ad-Hoc</h2>
        <p>
            The easy installation of ISEMS allows ad-hoc communication service for emergency camps or festivals.
        </p>
    </div>
    <img src="/images/festivals.svg">
</div>


![Mobile Solarnode at Tempelhofer Feld in Berlin](/images/freifunk-mast-thf-klein.jpg)

The concept builds on the Freifunk OpenMPPT solar controller and is designed to operate and manage independent network nodes in hard-to-reach locations using solar energy.

![Hardware](/images/Blockschaltbild-Foto-klein.png)

The ISEMS system consists of a web app that provides an overview of the operating data and error messages of all solar nodes. The web app can be hosted on a small computer like the Raspberry Pi. The solar routers use a data logger and analysis software that processes the data of the local system. The data of all participating solar nodes are retrieved from the Web App and processed into an overview.

![Physical Layer and Software Layer](/images/ISEMS-data-flow.svg)


The status information of the individual solar nodes can also be viewed locally and decentrally by the users via a web browser, as each solar node has its own small web server.

![ISEMS HTML status page embedded in Freifunk-Luci](/images/ISEMS-Router-Status-HTML-Embedded-in-LUCI.png)

The lowest hardware and software level of ISEMS is based on the ISEMS firmware for the Freifunk OpenMPPT solar controller, an open source and open hardware electronics design. The Freifunk OpenMPPT solar controller is the starting point of the project.

![PCB of the Freifunk-OpenMPPT-Controller Type A](/images/freifunk-mppt-innen.jpg)

The typical application scenario of ISEMS: Solar codes connect to the existing mesh network of a community or form their own local network, which may consist only of solar nodes. Each node also provides a Wi-Fi hotspot that end devices like smart phones can connect to use the mesh. Solar nodes with ISEMS can be installed inexpensively almost anywhere.

## Where does the use of a solar powered mesh node make sense?

Wherever there is no power network for communication technology or spontaneously a wireless Wi-Fi network is needed. Such application scenarios exist not only in community networks, but also in crisis areas, after disasters, power outages, in refugee camps or emerging and developing countries. ISEMS can also be used effectively in rich countries such as Germany, where there are dead spots outside the metropolitan areas.

By using solar energy you can install a node where there is no power: on a mountain top that blocks the radio link between two villages. On a roof without electricity, because the owner does not allow you to drill holes or is concerned about the energy bill. For a water level measuring station on the river, for geological measurements on a glacier or volcano ...


## Why is ISEMS focusing on mesh networks?

The advantage of mesh networks is that each node in the mesh can connect to any number of other link-local nodes without having to coordinate a master-client hierarchy. Mesh nodes work by radio in multipoint-to-multipoint mode - each node can communicate directly with each node if they are within radio range. Furthermore, a mesh routing protocol automatically ensures that nodes outside the direct range can also be reached, because all nodes can act as relay stations and forward the communication, if required. If a node fails, the mesh routing protocol automatically searches for alternate routes. If nodes are added, they are automatically integrated into the network. This is a big advantage for ISEMS.

In the most energy-efficient low-cost version, you only need one Wi-Fi radio per ISEMS station. With a little more effort and two wireless radios per device you get significantly more performance and lower latencies.


**Meshing is of great advantage for ISEMS, but not mandatory for the use of our software solution.** Due to the advantages, we prefer to connect the nodes via wireless mesh networking, but mesh networking is not essential for the use of the ISEMS software. Mesh networking simplifies the use of our application and increases the reliability of the network.

## How much does an ISEMS solar node cost?

For a simple, inexpensive and efficiently designed system, which  works all year in continuous operation e.g. in northern Germany, you have to spend about 200-250 euros for material, if you build it yourself.

Here's an example calculation:


| Compontent                                          |  Price  |
|-----------------------------------------------------|--------:|
| Router WR940N                                       | 25 Euro |
| Wasserproof, UV-resistant housing                   | 20 Euro |
| Battery Kung-Long 12 V 18 Ah                        | 40 Euro |
| Solar module 50 Watt                                | 60 Euro |
| Freifunk-Open-MPPT Solarcontroller                  | 40 Euro |
| Small assembly parts                                | 20 Euro |


In this example calculation, no external antennas are listed. A solar node with an omnidirectional antennas may e.g. stand on a ridge and can operate as a relay between several villages a few kilometers away, that connect with good directional antennas to it. It hardly generates wind load and can be mounted on a light duty mast.
