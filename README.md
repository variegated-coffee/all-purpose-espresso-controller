# All Purpose Espresso Controller

Espresso electronics are usually proprietary affairs with little to no expandability. The purpose of this project is to give everyone an open source alternative with lots of features and flexibility. 

It is designed to be useful in many different espresso machines, and for many different hardware configurations. It has the same PCB size as many very common Gicar controllers, making it fairly easy to swap this board into your existing enclosure.

There's also a corresponding high-voltage board, with relays and an AC/DC converter, designed to also fit into those same Gicar enclosures.

## High-level features

* RP2040 microcontroller
* Optional ESP32-S3 for extra processing power and Wi-fi/Bluetooth connectivity
* Plenty of IO, at 12V, 5V and 3V3 levels
* Dedicated connector for a UART based user interface device, like an [Open LCC](https://github.com/open-lcc/open-lcc-board) or a Nextion touchscreen (selectable 5V or 3V3 level)
* ADS1115 ADC (intended for e.g. pressure transducers or NTCs)
* FDC1004 Capacitance-to-digital (inteded for e.g. water level probes or capitance based controls)
* QWIIC ports (one per microcontroller) for additional expandability

![PCB](.github/pcb.png?raw=true "PCB") ![3D render](.github/3d-render.png?raw=true "PCB 3D render")

## Project status

The current hardware revision is R0A. It hasn't been manufactured yet, and you shouldn't be the first one to do it.

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
* CN12 - 3V3 GPIO
 * RP2040 GPIO22
 * GND
* CN13 - 3V3 GPIO
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

## Connectivity IO

### LCC/Display Connector
* CN10
  * UART (selectable 3V3 or 5V)
    * RP2040 UART0
    * ESP32 GPIO17/GPIO14
  * 1 FET controlled 12V pin (RP2040 GPIO13)
  * 1 FET controllec 3V3 pin (RP2040 GPIO14)
  * 1 3V3/5V pin
  * 1 GND pin

## Espresso IO

### Outputs - Open drain

* JP2, 4 pin, 12V tolerant
* CN5, 1 pin, 12V tolerant
* CN9, 1 pin, 12V tolerant
* CN6, 3 pins (4, 6, 8), 12V tolerant

### Outputs - 1.5A 5/12 V Switchable

* J10, 3 pins

### GPIO - 5V

* CN6, 3 pins (3, 5, 7)

### GPIO - 3V3

* CN2
  * GPIO22
* CN7
  * GPIO23
* J12, 8 pins
  * Pin 4
    * GPIO18
    * SPI0 SCK
    * PWM1 A
  * Pin 6
    * GPIO19
    * SPI0 TX
    * PWM1 B
  * Pin 8
    * GPIO20
    * SPI0 RX
    * PWM2 A
    * UART1 TX
  * Pin 19
    * GPIO21
    * SPI0 CSn
    * PWM2 B
    * UART1 RX
    * PWM2 B
  * Pin 3
    * GPIO26
    * ADC0
    * SPI1 SCK
    * PWM5 A
  * Pin 5
    * GPIO27
    * ADC1
    * SPI1 TX
    * PWM5 B
  * Pin 7
    * GPIO28
    * ADC2
    * SPI1 RX
    * UART0 TX
    * PWM6 A
  * Pin 9
    * GPIO29
    * ADC3
    * SPI1 CSn
    * UART0 RX
    * PWM6 B 

### ADC Inputs

* CN3, ADS1115, THT resistor divider
* CN4, ADS1115, THT resistor divider
* J11, ADS1115, 2 pins, with THT resistor dividers
* J12, RP2040, 4 pins, no divider (see GPIO 3V3)

### Capacitive to digital inputs

* CN1
* J14, 3 pins
