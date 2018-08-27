---
title: Logfile csv and error codes
url: /documentation/codes
draft: false
---

#ISEMS CSV file format and hex error codes#


The ISEMS CSV communication and storage data output** revision 1 **uses the following format:

#Data fields

~~~
01 Node-ID = nodeid ;
02 ISEMS-Paket-Format-Revision = packetrev ;
03 Epoch-Timestamp = timestamp ;
04 FREIFUNK-OPEN-MPPT-Firmware-Version and controller type = firmware_type ;
05 Time-until-next-scheduled-power-shutdown (in minutes) = nextreboot ;
06 Power-save-mode-of-Router On/Off = powersave;
07 Solarmodule Open-Circuit-Voltage V_oc, Value Volt DC = V_oc;
08 Solar-MPP-Voltage V_in, Value Volt DC = V_in ;
09 Battery voltage V_out, Value Volt DC = V_out;
10 Battery Charge State estimate (in percent) charge_state_int;
11 Battery Health estimate (in percent) health_estimate;
12 Battery temperature in Celsius = battery_temperature; 
13 Low Voltage Disconnect Voltage, Value Volt DC = low_voltage_disconnect;
14 Temperature corrected charge end Voltage, Value Volt DC = temp_corr_V_end ;
15 Rated Battery_Capacity in Amperehours Ah = rated_batt_capacity;
16 Rated Solar module capacity in Watt = solar_module_capacity;
17 Latitude = lat;
18 Longitude = long;
19 Status code (hex value) = statuscode
~~~

#CSV packet content summary:
~~~   
01 packetrev; 02 packetrev; 03 timestamp; 04 firmware_type; 05 nextreboot; 06 powersave; 07 V_oc; 08 V_in; 09 V_out; 10 charge_state_int; 11 health_estimate; 12 battery_temperature; 13 low_voltage_disconnect; 14 temp_corr_V_end; 15 rated_batt_capacity;  16 solar_module_capacity; 17 lat; 18 long; 19 statuscode
~~~


#ISEMS bit error hex codes
 

~~~c
(Big endian: Bit_0 left, Bit_11 right)

Bit_0:  1 = Charging

Bit_1:  1 = Discharging

Bit_2:  1 = Fully charged

Bit_3:  1 = Healthy

Bit_4:  1 = Warning: Battery level low. Increased battery wear.

Bit_5:  1 = Error: Energy storage capacity too small. Check battery size and/or wear.

Bit_6:  1 = Warning: Temperature sensor not connected.
	       
Bit_7:  1 = Error: No communication with solar controller.

Bit_8:  1 = Battery overheating.

Bit_9:  1 = Low battery temperature.

Bit_10: 1 = Firmware upgrade not allowed

Bit_11: 1 = 
	
~~~