# All-purpose Espresso Controller R0D Manufacturing

## PCB Manufacturing parameters (JLCPCB)

* 6 layer board
* Material: FR-4 TG155
* Surface finish: ENIG
* Outer copper weight: 1oz
* Inner copper weight: 1oz
* Via covering: Epoxy filled and capped
* Min via hole size: 0.2 mm

## PCBA parameters (JLCPCB)

* PCBA Type: Standard
* Assembly side: Top side (You *could* do both sides, but the SD Card reader is reasonable easy to hand solder)

## PCB and PCBA price:
Approximately $520 ex VAT for a 10 board run.

## Additional components

In addition to the components in the JLCPCB BOM, you'll need some other (hand soldered) components.

* Connectors CN1, CN7
	* Cheapest option is Dupont style pin headers
	* Recommended: TE AMPMODU Mod 2, either angled or straight (depending on mounting preference)
* Connector CN2
	* Depends entirely on mounting
	* Recommended: 2.5 mm pitch ribbon cable, 6 positions, 0.75 mm^2 conductor, 3 cm length
* Connector CN3
	* Optional
	* Recommended: 2 pin screw terminal
* Connector CN4
	* Cheapest option is Dupont style pin headers
	* Other options include
		* TE AMPMODU Mod 2, 2 pin angled (single channel)
		* TE AMPMODU Mod 2, 5x2 pin straight
* Connectors CN10, CN11, CN12, CN13
	* Cheapest option is Dupont style pin headers
	* Recommended: TE AMPMODU Mod 2, either angled or straight (depending on mounting preference)
* Connectors CN5, CN6
	* Cheapest option is Dupont style pin headers
	* Other options include:
		* TE AMPMODU Mod 2, 2 pin either angled or straight
		* TE AMPMODU Mod 2, 3 pin either angled or straight
* Connector CN7
	* Cheapest option is Dupont style pin headers
* Connector CN14
	* Cheapest option is Dupont style pin headers
* REF0 Reference resistor
	* Recommended values
		* PT100: 470 ohm
		* PT1000: 4.7 kohm
		* 50K NTC: 470 kohm
* SD card reader
	* Hirose DM3D-SF
* RP2040 SWD Debug Connector J13
	* ARM Cortex Debug Connector 10-pin, 0.05"
	* Recommended: DNF
	* Example: Samtec FTSH-105-01-L-DV-007-K  
* ESP32-S3 JTAG Connector J15
	* ESP-Prog JTAG connector, 10-pin, 0.05"
	* Recommended: DNF
	* Example: Samtec FTSH-105-01-L-DV-007-K
* ESP32-S3 PROG Connector J3
	* ESP-Prog PROG connector, 6 pin, 0.05"
	* Recommended: DNF
	* Example: https://www.aliexpress.com/item/32951697063.html