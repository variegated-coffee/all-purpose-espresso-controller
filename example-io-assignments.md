## Lelit Bianca v2 with Open LCC, Gear Pump, and Pump Pressure Transducer

### IO Assignment

* CN10 - Open LCC
* CN1 - Water level probe
* CN2 - Water tank level switch
* CN3 - Service Boiler NTC
* CN4 - Brew Boiler NTC
* CN5 - Brew Boiler SSR
* CN9 - Service Boiler SSR
* CN7 - Brew Switch
* JP2 Pin 3 - Water line / Low flow solenoid
* JP2 Pin 4 - Service boiler solenoid
* CN6 Pin 3 - Gear pump speed PWM
* CN6 Pin 5 - Gear Pump Tacheometer Input
* J11 Pin 2 - Pressure Transducer Analog Input

### Configuration

* ADC Vcc - 5V
* CN10 Vcc - 3V3
* DNF ESP32


## Rancilio Silvia with ESP32, SSD1309 display, Rotary encoder, Gear Pump, and Pump Pressure Transducer

### IO Assignment

* CN10 - Open LCC
* CN4 - Boiler NTC
* CN5 - Boiler SSR
* J12 Pin 8 - Display MOSI
* J12 Pin 4 - Display SCLK
* J12 Pin 6 - Display RES
* J12 Pin 10 - Display DC
* Hard-wire Display CS
* CN7 - Brew Switch
* CN2 - Water Switch
* J12 Pin 9 - Steam Switch
* J12 Pin 3 - Rotary Encoder Clk
* J12 Pin 5 - Rotary Encoder D
* J12 Pin 7 - Rotary Encoder SW
* JP2 Pin 4 - Three-way solenoid
* CN6 Pin 3 - Gear pump speed PWM
* CN6 Pin 5 - Gear Pump Tacheometer Input
* J11 Pin 2 - Pressure Transducer Analog Input

### Configuration

* ADC Vcc - 5V
* CN10 Vcc - 3V3
* DNF ESP32

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