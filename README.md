# All Purpose Espresso Controller

Espresso electronics are usually proprietary affairs with little to no expandability. The purpose of this project is to give everyone an open source alternative with lots of features and flexibility. 

It is designed to be useful in many different espresso machines, and for many different hardware configurations. It has the same PCB size as many very common Gicar controllers, making it fairly easy to swap this board into your existing enclosure. It also comes with screw holes, so a 3D printed enclosure is another option.

There's also a [corresponding 100-240 VAC board](https://github.com/open-lcc/all-purpose-espresso-controller-hv-board), with relays and an AC/DC converter, designed to also fit into those same Gicar enclosures.

## High-level features

* RP2040 microcontroller
* Optional ESP32-S3 for extra processing power and Wi-fi/Bluetooth connectivity
* Plenty of IO, at 12V, 5V and 3V3 levels
* Dedicated connector for a UART based user interface device, like an [Open LCC](https://github.com/open-lcc/open-lcc-board) or a Nextion touchscreen (selectable 5V or 3V3 level)
* ADS1115 ADCs (intended for e.g. pressure transducers or NTCs)
* FDC1004 Capacitance-to-digital (inteded for e.g. water level probes or capitance based controls)
* QWIIC ports (one per microcontroller) for additional expandability

[IBOM](https://raw.githack.com/open-lcc/all-purpose-espresso-controller/r0b/manufacturing-data/r0b/ibom.html)

![PCB](.github/pcb.png?raw=true "PCB") ![3D render](.github/3d-render.png?raw=true "PCB 3D render")

## Project status

The current hardware revision is R0B. It hasn't been manufactured yet, and you shouldn't be the first one to do it.

## Disclaimer

Anything you do with this, you do at your own risk. This hardware hasn't even been manufactured by it's creator yet. Your machine uses both line voltage power, high pressured hot water, steam and other dangerous components. You *really* shouldn't be using this yet; in fact, you shouldn't even consider it. Risks include but are not limited to, damaging your machine, personal injury, property damage and summoning dead Cthulhu from his sleep at R'lyeh.

## Connectivity
* CN1 - Display Connector, either for Open LCC or a Nextion Display
  * UART (selectable 3V3 or 5V, default 3V3)
    * JP9 selects voltage
    * RP2040 UART0
    * ESP32 GPIO17/GPIO14
  * 1x 12V output (SR2 DRAIN6)
  * 1x 3V3 output (SR2 DRAIN7)
  * 1 3V3/5V pin and GND pin
* CN2 - HV Board Connector
  * 12V and GND
  * 4 Open drains (SR1 DRAIN0-3)
* CN3 - Separate PSU Connector
  * 12V and GND
* CN4 - Capacitive sense connector
* CN5 - Differential ADC with RC filter
  * AVCC is 5V or 3V3 depending on JP13, default is 5V
  * ADC1 AIN0-1
  * Hand solder R14 0805 Resistor with a precision resistor to create a voltage divider
  * Convertable to single ended channels by removing C26 and cutting JP18
* CN6 - Differential ADC with RC filter
  * ADC1 AIN2-3
  * AVCC is 5V or 3V3 depending on JP13, default is 5V
  * Hand solder R14 0805 Resistor with a precision resistor to create a voltage divider
  * Convertable to single ended channels by removing C26 and cutting JP17
* CN7 - 4 RC filtered ADC channels
  * AVCC/AGND pins
  * AVCC is 5V or 3V3 depending on JP13, default is 5V
  * ADC2 AIN0-3
  * Hand solder R40-43 0805 Resistors with a precision resistors to create a voltage dividers
  * Convertable to differential channels, by replacing 0402 components (see schematic for details)
* CN8 - Outputs
  * 4x 5V/12V Outputs
    * Voltage selectable by JP4-6/JP16
  * GND
* CN9 - Open drains and 5V IO
  * 3x Open drains (SR1 DRAIN5-7)
  * 3x 5V PWM capable outputs (RP2040 GPIO12-14)
  * 12V/GND
* CN10 - Open drain
  * SR2 DRAIN1
  * 12V
* CN11 - Open drain
  * SR2 DRAIN0
  * 12V
* CN12 - 3V3/5V GPIO
  * RP2040 GPIO22
  * GND
* CN13 - 3V3/5V GPIO
  * RP2040 GPIO23
  * GND
* CN14 - GPIO
  * RP2040 GPIO18-21
    * Also connected to ESP32-S3 GPIO4-7
    * Can be level shifted to 5V through JP1/JP10-12
    * GP18 can be connected to ADC1 RDY through JP14
    * GP19 can be connected to ADC2 RDY through JP15
  * RP2040 GPIO26-29
    * ADC Capable

