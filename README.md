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
