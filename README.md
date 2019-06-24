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
this as a special order size and charge accordingly. If you take this route
be sure to notch both sides of the PCB at the connector end for a distance
of about 1" and depth 0.1" in order to clear the latch engagement pin.

Battery backup is by use of a 12 mm lithium coin cell, either the CR1216 or
the CR1225. The CR1225 has the higher capacity rating of the two at 48 mAh.
Although that's only half the capacity of a CR2016, the Cypress MoBL SRAM
memory device only requires 1 uA in standby mode when the memory is not
selected so battery life should be reasonably long.

## Repository Content

The **Board** directory contains the schematic and PCB board images. Gerber
files are in the Gerber subdirectory. The **Datasheets** directory contains
relevant device information, copyright the manufacturer of course.

## Assembly Notes

<img src="Card front and back.jpg">

The flexible contacts punched from the top of the battery holder are bent
downwards far enough to touch the PCB. Left as-is they will make it more
difficult to insert and remove the battery. The spring force can even be
enough to cause the solder bond between holder tab and PCB to fail
resulting in the battery popping out of the holder. Press the two spring
tabs upwards so that they are closer to the top of the holder.

The battery holder is held by solder to the PCB. Be sure to apply enough to
cover the contacts well because the holder will likely be subject to a
pulling force by those who grasp it to remove the card from the calculator.

The memory protect switch is a more suitable point to grasp the card when
removing it from the calculator. The switch is anchored at its four corners
by solder tabs. In addition, two pegs extend from the bottom of the switch
body into holes in the PCB. Pull upwards in the plane of the PCB.

The top of the battery holder is at the potential of the positive side of
the battery. The holder top presents a possibility of a short, so it is
advised to cover it with a strong adhesive tape or contact sheet. Better
yet, remove the chrome coating from the top with rough sandpaper prior to
soldering the holder to the board, then coat with paint or nail polish.

To insure the card contacts are pressed firmly against the card connector
contacts in a calculator, attach a strip of 0.8mm (1/32") thick plastic
behind the contacts on the component side of the PCB. The strip should
meet the lower edge of the PCB and extend upwards about 1/2", but should
not extend the full width of the PCB. Keep the strip about 1/4" from the
left and right sides so that it doesn't cause the card to be blocked by
guide tabs in the card connector block inside the calculator.

## Usage

The card may require a bit of wiggling to clear guide tabs molded into the
card connector assembly. These tabs help guide a commercial card and open
a spring-loaded cover protecting the card contacts. Insertion and removal
is fairly easy in either card slot of an HP48SX. It may help to turn the
calculator on its face and then some downward pressure applied to the back
of the card as the card is pressed down on the top edge.

Insertion in slot 1 of an HP48GX is slightly "stickier" but is easily done
by turning the calculator over. Slot 2 is a different story as the bottom
edge of the PCB catches on a ledge above the connector slot. A plastic
ruler can be use to press the back of the card near the bottom until it
clears the ledge. An alternative is to move the plastic strip from the front
to the back of the PCB just above the row of contacts. The downside is that
the card will now no longer fit in slot 1.

## Project Status

A set of boards were built and tested in HP48SX calculators and outside of
a calculator shell. All cards showed an initial decline in battery cell
voltage before stabilizing around 3 Volts. All cards maintained their
content across the multi-week test period.

The pullup resistor R1 on the Output Enable input to memory was found to be
unnecessary, but did not affect battery life during the test period. I
recommend not installing R1 on any board build.

Improvements to the design include using a smaller contact pad for the battery
bottom since the current size presents a slight risk of a short between the
bottom pad and battery housing if a metal probe is inserted in the general
area. Some designs show a 2.2K current limiting resistor in series with the
CdDet input. A resistor could be added to the design and a zero Ohm short
could be used if the resistor proves to be unnecessary.

The supply voltage to the switch when in the RAM position could be VccOn
from the calculator rather than the memory device supply Vcc. No detrimental
effect has been seen with the arrangement, but if battery life is
compromised as a result, the switch should be moved to the ROM position when
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
