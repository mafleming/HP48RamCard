HP48RamCard Repository

# A 128K RAM Card for the HP48SX/HP48GX Calculator

This repository contains the schematics and Gerber files needed to create
a 128K RAM card for the HP-48SX/GX calculators. Data sheets for the parts
used are also included. The Bill of Material calls out specific vendor and
vendor part numbers for the passive components used, but any equivalent
part in the SMD 0805 package can be substituted.

The PCB board dimension is 2.125" wide by 3.375" high. The board thickness
is 0.8 mm (1/32") and a 0.8 mm plastic strip must be added so that the card
makes a snug fit in the calculator connector. A PCB thickness of 1.6 mm
can be used instead if a direct fit is desired, but many PCB houses treat
this as a special order size and charge accordingly.

Battery backup is by use of a 12 mm lithium coin cell, either the CR1216 or
the CR1225. The CR1225 has the higher capacity rating of the two at 48 mAh.
The Cypress MoBL SRAM memory device only requires 1 uA in standby mode when
the memory is not selected so battery life should be reasonably long.

## Repository Content

The **Board** directory contains the schematic and PCB board images. Gerber
files are in the Gerber subdirectory. The **Datasheets** directory contains
relevant device information, copyright the manufacturer of course.

## Project Status

A set of boards were built and tested in HP48SX calculators and outside of
a calculator shell. All cards showed an initial decline in battery cell
voltage before stabilizing around 3 Volts. All cards maintained their
content across the multi-week test period.

The pullup resistor R1 on the Output Enable input to memory was found to be
unnecessary, but did not affect battery life during the test period. I
recommend not installing R1 on any board build.

Improvements to the design include using a smaller square pad for the battery
bottom since the current size presents a slight risk of a short between the
bottom pad and battery housing if a metal probe is inserted in the general
area. Some designs show a 2.2K current limiting resistor in series with the
CdDet input. A resistor could be added to the design and a zero Ohm short
could be used if the resistor is unnecessary.

The supply voltage to the switch when in the RAM position could be VccOn
from the calculator rather than the memory device supply Vcc. No detrimental
effect has been seen with the arrangement, but if battery life is
compromised as a result, the switch can be moved to the ROM position when
the card is not in use.

## Bill of Material

| Symbol | Device | Part Number | Notes       |
| ------ | ------ | ----------- | ----------- |
| IC1 | Cypress 128Kx8 SRAM| CY62128ELL45SXI | SOIC28 |
| D1 | Dual Schottky Diode | ON Semi BAT54CLT1G | SOT23 |
| R2 | 470K, 5% | Panasonic ERJ-P06J474V | 0805 SMD |
| R3 | 1M, 5% | Yageo RC0805JR-071ML | 0805 SMD |
| C1 | 470nF, 16VDC | Taiyo Yuden EMK212B7474MG-T | 0805 SMD |
| U1 | Battery Hldr | Linx BAT-HLD-012-SMT | Use CR1216 or CR1225 |
| U2 | SPDT Switch | Apem MA12R | |
