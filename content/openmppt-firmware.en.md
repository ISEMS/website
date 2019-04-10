---
Title: OpenMPPT Firmware
url: /documentation/firmware
draft: false
---

# Communication with the Freifunk OpenMPPT
***
# Requirements

The Freifunk OpenMPPT solar controller has a **RS232** interface with 3.3 Volt logic level (Only 3.3 V. Do not use 5 V level or standard RS232 level without a level shifter.) The communication parameters for the serial interface:

    9600 baud, 8N1

No hardware or software flow control.


# Receive the data from the Freifunk OpenMPPT

The Freifunk OpenMPPT solar controller sends a record of its operating status via the serial interface to the connected router at least once per minute. If the ISEMS software is installed on the router, the data will be written to 

    /tmp/mmpt.log

and evaluated and prepared by the ISEMS software.


# Send configuration commands to the Freifunk OpenMPPT

Given that the serial interface is correctly configured and connected, a configuration command can be sent from the router to the microcontroller of the Freifunk OpenMPPT during operation. This is done with the command line tool

    echo
 

## Commands that can be sent via the serial interface: ###

### Router Reset Timer (W)

This is a down counting timer. After expiration of the timer the router is powered off for 5 seconds and the counter starts again.

Example:

    echo "W=2880" > /dev/ttyXXX

The command sets the router reset timer to 2880 minutes (48 hours). This setting is stored in the non-volatile memory of the Freifunk OpenMPPT. The command *W=* expects a parameter in minutes, ranging from 60 minutes to 42200 minutes - one hour to 29 days. It is not intended to switch off this function completely.

**Why such a timer?**

It sometimes happens that a router "hangs". Malfunctions of this kind are a common woe, particularly due to issues in Wi-Fi drivers. Ideally, such hangs should never happen, but some devices malfunction at irregular intervals and need a reboot. Although there is a software watchdog in OpenWRT, it can fail to recognize the problem. The device happily continues to run as a zombie and there is no option to fix this state from remote, if there is no second remote control channel. One has to physically go to the site and perform a power-cycle. This can be time-consuming and annoying.

The flaw: The system restarts regularly even if it were not necessary.

## Powerdown Timer (P)

The power-down timer is the counterpart to the router reset timer: Disable the load for N minutes.

Example:

echo "P=12" > /dev/ttyXXX

switches off the connected router directly and without mercy after issuing the command for 12 minutes. The *P=* command is not saved but executed immediately. In addition *P =* resets the router reset timer to the preset value after the set timeout has expired. The dead time of *P=* can be set between one minute and 42200 minutes.

### On and off voltage of deep discharge protection (oN and ofF)

Lead acid batteries, regardless whether they are of the liquid acid, gel or fleece type, do not like deep discharges. If you discharge them below a certain residual voltage, they dramatically lose their capacity. Therefore, it is imperative to have a deep discharge protection.

Under load the voltage is lower than when the load is switched off. If the switch-on value and switch-off value were the same, the load would be switched off and on again in rapid succession: Load on, voltage drops, load off, voltage rises, load on, etc.

Therefore, a deep discharge protection needs to have a hysteresis between switch-off value and a switch-on value.

In the basic settings, the Freifunk OpenMPPT solar controller switches off the load at 11.7 Volt battery voltage. If the battery exceeds 12.3 volts, the load is switched on again. These are proven, practice-oriented values. Normally, there is nothing to change, unless you are an expert and know that you want a special profile. For example, one can turn the router off at a higher load off voltage level to reduce the depth of discharge cycles, extending the life of the battery. For example, consider you want to set up a public hotspot in a park that will shut down about three hours after dark.

The life of a battery depends on the operating time and the number and depth of charge-discharge cycles. Remember to also increase the switch-on voltage if you increase the switch-off level. A corresponding hysteresis must always be observed. 

Example:

    echo "N=12600" > /dev/ttyXXX

switches on the load output if the battery voltage raises above 12.6 volts.

    echo "F=12000"> /dev/ttyXXX **

switches off the loads when the voltage falls below 12.0 volts.

Both settings are automatically stored in the non-volatile memory of the Freifunk OpenMPPT.

