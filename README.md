# All Purpose Espresso Controller

Espresso electronics are usually proprietary affairs with little to no expandability. The purpose of this project is to give everyone an open source alternative with lots of features and flexibility. 

It is designed to be useful in many different espresso machines, and for many different hardware configurations. It has the same PCB size as many very common Gicar controllers, making it fairly easy to swap this board into your existing enclosure. It also comes with screw holes, so a 3D printed enclosure is another option.

There's also a [corresponding 100-240 VAC board](https://github.com/open-lcc/all-purpose-espresso-controller-hv-board), with relays and an AC/DC converter, designed to also fit into those same Gicar enclosures.

## High-level features

* RP2040 microcontroller with 2 MB of program flash, and 2 MB of settings flash
* ESP32-S3 for extra processing power and Wi-fi/Bluetooth connectivity
* SD card reader
* Plenty of IO, at 12V, 5V and 3V3 levels
* Dedicated connector for a UART based user interface device, like an [Open LCC](https://github.com/open-lcc/open-lcc-board) or a Nextion touchscreen (selectable 5V or 3V3 level)
* EyeSPI connector for ESP32-S3
* ADS124S08 ADC (intended for e.g. pressure transducers or NTCs)
* FDC1004 Capacitance-to-digital (inteded for e.g. water level probes or capitance based controls)
* QWIIC ports (one per microcontroller) for additional expandability

[IBOM](https://raw.githack.com/open-lcc/all-purpose-espresso-controller/r0d/manufacturing-data/r0d/ibom.html)

![PCB](.github/pcb.png?raw=true "PCB")
![3D render](.github/3d-render.png?raw=true "PCB 3D render")
![3D render back](.github/3d-render-back.png?raw=true "PCB 3D render of back side")


## Project status

The current hardware revision is R0D. It hasn't been manufactured yet, and you shouldn't be the first one to do it.

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
* CN5 - ADC port
  * See note below
* CN6 - ADC port
  * See note below
* CN7 - ADC port
  * See note below
* CN8 - Outputs
  * 4x 5V/12V Outputs
    * Voltage selectable by JP4-6/JP16
  * GND
* CN9 - Open drains and 3V3 IO
  * 3x Open drains (SR1 DRAIN5-7)
  * 3x 3V3 IO (RP2040 GPIO12-14)
  * 12V/GND
* CN10 - Open drain
  * SR2 DRAIN1
  * 12V
* CN11 - Open drain
  * SR2 DRAIN0
  * 12V
* CN12 - 3V3/5V GPIO
  * RP2040 GPIO22
  * Shifted through MOSFET level shifter
  * Can be switched to a 500 mA output with solder jumper
  * GND
* CN13 - 3V3/5V GPIO
  * RP2040 GPIO23
  * Shifted through MOSFET level shifter
  * Can be switched to a 500 mA output with solder jumper
  * GND
* CN14 - GPIO
  * RP2040 GPIO18-21
    * GP19 can be connected to SD Card Detect via a solder jumper
    * GP21 is also connected to an LED
  * RP2040 GPIO26-29
    * ADC Capable

### ADC
By default, CN5 and CN6 are configured for a ratiometric measurement. In order to use it as such, you need to fit a reference resistor for REF0. The reference resistor needs to be larger than the measured values (e.g. for a PT100, use a 400 ohm resistor), and needs to be high accuracy and low drift. 

AIN1-2, AIN4-7, and AIN9-10 are all outfitted with RC filters, as is REF0. The board is also designed in such a way that you can, by sacrificing an RC filter, convert a channel to instead use an upstream resistor divider. 

The ADS124S08 features two external references (REF0 and REF1), as well as an internal 2.5V reference. AIN6-7 double as REFP1/REFN1. The board is designed with footprints for a reference resistor.

#### Common configurations

##### PT100 RTD

##### PT1000 RTD

##### 50k NTC - Ratiometric

##### 50k NTC - Resistor divider

##### 0.3 – 4.5 V Pressure trandducer - 5 V Reference

##### 0.3 – 4.5 V Pressure trandducer - Resistor divider