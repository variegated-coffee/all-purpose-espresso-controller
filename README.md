# Open Control Board

## Connectivity IO

### LCC Connector
* CN10
  * RP2040 UART0
  * 1 FET controlled 12V pin (RP2040 GPIO13)
  * 1 FET controllec 3V3 pin (RP2040 GPIO14)
  * 1 3V3 pin
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
    * Reserved for RP2040 - ESP32 UART connection
  * Pin 19
    * GPIO21
    * SPI0 CSn
    * PWM2 B
    * UART1 RX
    * PWM2 B
    * Reserved for RP2040 - ESP32 UART connection
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
    * Reserved for RP2040 - ESP32 Firmware update

### ADC Inputs

* CN3, ADS1115, fixed divider
* CN4, ADS1115, fixed divider
* J11, ADS1115, 2 pins, with THT resistor dividers
* J12, RP2040, 4 pins, no divider (see GPIO 3V3)

### Capacitive to digital inputs

* CN1
* J14, 3 pins

## Worst case scenario IO Assignment

### Machine spec

* 2 group triple boiler (2 coffee, 1 service), all PID controlled with level sensors
* Dual PWM gear pumps for coffee boilers
* Single rotary pumps for service boiler
* Dual flow sensors
* Triple NTC thermistors
* Triple pressure transducers
* Five solenoids (3 line solenoids, 2 three-way group solenoid)
* Two brew microswitches
* One water tank level switch

### IO Assignments

* Brew Boiler 1 HE Relay - JP2 Pin 2
* Brew Boiler 2 HE Relay - JP2 Pin 3
* Service Boiler HE Relay - JP2 Pin 4
* Service Boiler Rotary Pump Relay - JP2 Pin 5
* Gear pump 1 PWM - CN6 Pin 3
* Gear pump 2 PWM - CN6 Pin 5
* Flow sensor 1 - J12 Pin 4 GP18
* Flow sensor 2 - J12 Pin 6 GP19
* NTC Brew 1 - CN3
* NTC Brew 2 - CN4
* NTC Service - J11 Pin 2
* Pressure Transducer 1 - J12 Pin 3 GP26
* Pressure Transducer 2 - J12 Pin 5 GP27
* Pressure Transducer 3 - J12 Pin 7 GP28
* Brew Boiler 1 Level sensor - J14 Pin 2
* Brew Boiler 2 Level sensor - J14 Pin 4
* Service Boiler Level sensor - CN1
* Water Tank Switch - CN6 Pin 7
* Brew switch 1 - CN2
* Brew switch 2 - CN7
* Solenoid 1 - J10 Pin 2
* Solenoid 2 - J10 Pin 3
* Solenoid 3 - CN6 Pin 4
* Solenoid 4 - CN6 Pin 6
* Solenoid 5 - CN6 Pin 8
* ESP32 UART J12 Pin 8 GP20
* ESP32 UART J12 Pin 10 GP21
* ESP32 Firmware update J12 Pin 9 GP29

#### Free pins

* CN5 (Output)
* CN9 (Output)
* J10 Pin 4 (Output)
* J11 Pin 3 (ADC)
* J14 Pin 7 (Capacitance)
