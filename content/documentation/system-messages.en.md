---
Title: ISEMS System-Messages
draft: false
---

# Explanation of the status messages

# Normal status messages

### »Healthy«

The ISEMS system is working properly. It should always be like this :) 

### »Charging«

The battery is charging. The system runs on solar energy and stores surplus solar energy in the battery.

### »Discharging«

The battery is discharging. This happens at night or at very low solar radiation. The system now consumes solar energy stored in the battery. This message should not appear during the day except at dusk or in very dimly lit conditions. If there is no charge during the day, this indicates an imminent problem.

### »Fully charged«

The battery is fully charged. The system runs on solar energy. There is excess energy that is not stored or consumed.

# Warnings

## »Warning: Battery level low. Increased battery wear«

**Meaning: The charge level of the battery has fallen below 50% charge level. When the battery level is low, the life of the battery decreases, depending on the operating time and depth of discharge.**

This message should only appear on some days in winter. Occurs frequently or even in summer, this can have several causes:

* The battery is too small or its storage capacity has decreased due to wear. **Remedy:** Increase the battery capacity by connecting batteries in parallel or install larger battery or replace worn battery.

* The solar module is dimensioned too small, it is basically consumed more energy than produced. **Remedy:** Install an additional solar module or a larger solar module. Pay attention to the maximum load capacity of the open-MPPT controller and possibly replace it with a more powerful version. Enable power saving mechanisms or use a more economical router.

* The solar panel is shaded during the day (for example, through branches of trees.) The solar panel should not be out of shade from sunrise to sunset. **Remedy:** Find a better mounting location or remove the objects that cause shading of the solar module.

* The solar module is misaligned. **Remedy:** It should face the sun at an angle of 0 degrees at noon.

* The solar panel is dirty (covered by leaves, bird droppings), iced or snow covered. **Remedy: The solar module should be mounted steeply (45-55 degrees), so that dirt is easily washed off by rain or snow slides down easily.** The resulting performance loss caused by a steep mounting angle poses no problem in summer and is optimal in winter. As a rule, the solar module should be mounted steep enough so it clean itself, without intervening manually. The lower edge of the solar module should have sufficient distance to the roof or floor, so that snow in the winter months does not pile up in front of the solar module.

* **The system is not charging during the day?** The solar module is not connected, the solar module went missing or is covered. **Remedy: re-connect solar module, check connections, remove obstacles.**

## »Warning: Temperature sensor not connected«

**Temperature sensor missing or the connection to the temperature sensor is interrupted.**

The temperature sensor is required so that the Open-MPPT can measure the temperature of the battery and calculate the maximum charging voltage. Without a temperature sensor, the Open-MPPT always assumes a 20-degree battery temperature. If the battery is exposed to temperatures above 30 degrees and below 10 degrees, a missing temperature sensor accelerates the battery wear.

**Remedy: Connect temperature sensor, check cables and plug connections.**

## »Battery overheating«

**The temperature of the battery is too hot, it exceeds 42 degrees Celsius.**

Above 42 degrees battery temperature, the Open MPPT will stop charging to protect the battery. If the ambient temperature is above 40 degrees, this condition can hardly be avoided. **Remedy: The battery should generally be in the shade and not exposed to the sun**.

## »Low battery temperature«

**The temperature of the battery is very low, it falls below -10 degrees Celsius.**

This is not indicating a damage or big issue, but low temperatures temporarily (no pun intended) reduce the usable capacity of the battery. If batteries are used with liquid electrolyte, it should be taken into account that they can freeze at very low charge level.

## »Warning: Energy storage capacity too small. Check battery size and/or wear«

**The ratio between solar power rating and battery capacity is unfavorable.**

The capacity of the battery and the maximum power of the solar module should be in reasonable proportion. Too fast charging and fast discharging speeds up battery wear on any type of battery. If a solar battery with a disproportionately large charge current - greater than 1/5 of its nominal capacity - charged, the life is reduced.

If this message appears, the ISEMS software estimates the battery capacity to be too small in relation to the specified solar module power. This effect also occurs at the end of the life of the battery when the actual capacity of the battery deteriorates due to wear. The indication of the capacity printed on the housing deviates more and more from the actual capacity. The ISEMS system attempts to estimate the remaining storage capacity of the battery..

**If this message appears frequently and the system often fails in spring and autumn, this indicates a worn out battery.**

**Note:** This feature is based on state of charge and battery state estimation and is dependent on correct information in the configuration file on the router side:

		/etc/config/ffopenmppt



Example:

		config ffopenmppt
		        option powersave '0'
		        # Rated solar module power in Watt
		        option solar_module_capacity '20'
		        # Maximum power consumption of router in Ampere
		        option maximum_power_consumption '0.1'
 		        # Rated battery capacity in Amperehours
        		option rated_batt_capacity '7'


# Error messages

## »No information. Error: No communication with solar controller«

**The system is flying blind.**

**Caution:** If this message appears, then do not attempt to perform a firmware update of the router remotely because it is unknown whether the power supply of the router might be interrupted during the update. This would turn the router into a high-tech paperweight that can only be repaired through advanced hands-on hacking ;)

An interruption of the power supply may occur by the deep discharge protection or if the watchdog reset timer accidently kicks in while you are flashing. 

**Remedy:** If this error message occurs during operation, the cable of the serial connection between router and Open-MPPT is interrupted. It may simply be disconnected.

### If the problem occurs during the first installation, there are several possible causes for this error message to look for:

* The set baud rate or other settings of the serial interface are not correct. They are *9600 baud, 8N1*, no hardware flow control.

* The TX / RX lines of the serial port are reversed or there is no ground connection between the router and the Open MPPT.

* No compatible 3.3V level serial interface. Remedy: Use the level converter.

* The serial port of the router is blocked by a serial terminal login program. Serial terminals are active by default in most router firmware and must be disabled for other purposes before using the serial port.


To fix this, in /etc/inittab file, the line containing ::askconsole must look like this:

		#::askconsole:/usr/libexec/login.sh

The hash mark **#** at the beginning of the line disables the start of the serial login console, which is the reason why access to the serial port fails. After changing the file, restart the router or run ***init q*** on the command line to reload the file.

* The serial interface of the router simply does not work.

Often, low-cost routers require simple modifications (adding one or two resistors in addition to populating pins by soldering) for the serial interface to work. Further information can be found for the respective model / hardware revision of a particular model in the [OpenWRT-Wiki.](https://wiki.openwrt.org/toh/start) 

* Ground loop in the power supply.

If the cables between the router and the OpenMPPT, which carry the negative voltage potential (minus, ground, 0 Volt), are too long and too thin, the zero point voltage goes up and down depending on the current flow (Ampere). The effect: You might see communication errors or the communication only works in one direction. Remedy: Better cable cross section and/or shorter ground connection.
