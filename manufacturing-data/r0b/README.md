# Manufacturing with JLCPCB

## Errata

* Q7 is wrong

## Manufacturing settings
Manufacturing of R0B was done with JLCPCB, including PCB Assembly.

The following settings were used:

### PCB Prototype
* Gerber file: GERBER-open-control-board_Y54
* Build Time: 3 days (PCBA Only)
* Base Material: FR-4 
* Layers: 4
* Dimension: 69 mm* 54 mm 
* PCB Qty: 5
* Product Type: Industrial/Consumer electronics 
* Different Design: 1
* Delivery Format: Single PCB 
* PCB Thickness: 1.6
* Impedance Control: no No requirement 
* Layer Sequence: 
* PCB Color: Green 
* Silkscreen: White
* Material Type: FR4-Standard TG 135-140 
* Via Covering: Epoxy Filled & Capped
* Surface Finish: HASL(with lead) 
* Deburring/Edge rounding: No
* Outer Copper Weight: 1 oz 
* Inner Copper Weight: 0.5 oz
* Gold Fingers: No 
* Flying Probe Test: Fully Test
* Castellated Holes: no 
* Edge Plating: No
* Remove Order Number: No 
* Min via hole size/diameter: 0.3mm/(0.4/0.45mm)
* 4-Wire Kelvin Test: No 
* Paper between PCBs: No
* Appearance Quality: IPC Class 2 Standard 
* Confirm Production file: Yes
* Silkscreen Technology: Ink-jet/Screen Printing Silkscreen 
* Package Box: With JLCPCB logo
* Board Outline Tolerance: ±0.2mm(Regular)

The observant will note that this is the default settings, except Via Covering and Confirm Production File.

### PCBA

* PCBA Type: Economic
* Assembly Side: Top Side
* PCBA Qty: 5
* Tooling holes: Added by JLCPCB
* Confirm Parts Placement: Yes
* Photo Confirmation: No
* Board Cleaning: No
* Conformal Coating: No
* Bake Components: No
* Packaging: Antistatic bubble film
* Depanel boards & edge rail before delivery: No
* Solder Paste: Sn96.5%, Ag3.0%, Cu0.5%(260℃)
* Others: No
* Add paste for unpopulated pad & step stencil opening: No
* File provided as: Complete File, just proceed with my own files
* Panel Format: 1 * 1
* Build Time: 1-2 days

Except for "Confirm Production File", this too is the default settings.

Economic PCBA doesn't allow for assembling the ESP32-S3, but it is fairly easy to solder on yourself, which is what I'll be doing.