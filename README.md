# Sony BA-4D RGB Mod
### (KV-27S42, KV-27V42, KV-20M42, KV-13M42, etc)

<img src="https://user-images.githubusercontent.com/41927604/166306640-f9bdade9-1c80-46ad-8329-f599bfd9f642.jpeg" width="600" height ="450" />


RGB Mod for Sony BA-4D CRT televisions.

Written by Brendan Eddy (FlyingFlygon). Credits to:
* MarkOZLAD for method and diagrams
* Syntax for method
* John M for installation pictures
* Puzzleheaded-Sign-89 for installation pictures

## Overview

This mod uses the OSD mux circuit to combine the analog RGB signal produced by the television's On Screen Display (menus, etc) with the external RGB signal from your retro video game consoles. This method is newer than the legacy, outdated methods of snipping the existing circuits and injecting the console signals. The benefit of this method are 1) you can have the menu display on top of your RGB video, 2) no permanent damage is done to the TV and 3) it's easier. 

See following diagram for an overview of what this circuit looks like. (Note these chip names and pins are specific to the Sanyo set. Can be ignored for the purposes of this guide)

<img src="https://user-images.githubusercontent.com/41927604/166302867-327fab37-5817-43e2-9fba-3f42af5b9b40.png" width="800" height="800" />

##### Credit to Syntax and MarkOZLAD

The BA-4D Sony sets have been successfully modified using the mux method for SCART input as well as BNC. If you choose to use BNC connectors, I recommend purchasing a BNC to S-Video adapter (if your set is one of the larger models, such as KV-27x) or a BNC to RCA adapter for the sync line. This is because it is much easier to use an existing video input on the TV for your RGB's sync signal than installing a 4th BNC line injected to the Y/C Jungle. 

## Components Needed

For this mod you will need:
* Properly shielded wires (I chose 20AWG silicone wire, you can use smaller gauge however)
* 3x 2400 Ohm resistors (unless you choose to not use diodes, see next section)
* 3x 1N4148 Logic diodes (unless you choose to not use diodes, see next section)
* 3x 430 Ohm resistors
* 3x 75 Ohm resistors
* 1 SPDT (single pull, double throw) switch
* Your choice of adapter for sync line (In my case, I use BNC->S-Video for KV-27S42)

## Modification Steps

In order to implement the mux circuit, we need to remove the existing resistors on the OSD's R, G, and B lines and replace them with the appropriate value resistors that match the diagram above. We will connect our external RGB lines to these new resistors. Also, we need to implement blanking by an external switch. We will pull 5V from the set into the switch and throw it to the OSD's blanking pin through an appropriate sized resistor. 

![Sony-BA-4D---OSD-Mux-Circuit-with-Diodes md](https://user-images.githubusercontent.com/41927604/166327672-9cb0c464-649c-4389-90cd-98dad2a0e45c.png)
![Sony-BA-4D---Blanking-via-Switch md](https://user-images.githubusercontent.com/41927604/166327687-a96b2d13-3066-4fde-b11e-3a17121711c9.png)

##### Credit to MarkOZLAD

Let's break that down step by step. (Note, sections marked with an asterisk * may have differences by model. Check next section)

1. Locate and remove the throughhole resistors R025, R026, and R027 between the Microcontroller (Micon) chip (IC001) and Y/C Jungle chip (IC301).


2. Locate and remove the surface mount resistors R086, R087, and R088 on the underside of the board. *
![SurfaceMount](https://user-images.githubusercontent.com/41927604/166325181-1a3ad6cf-4625-486e-85ea-68a7f084d674.png)

3. Replace the throughhole resistors with our 430Ohm attached to the 1N4148 diodes.

4. Solder your R, G, and B wires to the diode side. R025 is red, R026 is green, R027 is blue.  
___

The basic process is:
- remove the existing inline throughole resistors R025, R026 and R027
- replace each of them with a 2K4R and a 1n4148 diode
- remove surface mount resistors R086, R087 and R088
- On the external RGB lines use 75R terminations to ground and then 430R inline
- Connect the external RGB lines to the leg of the diodes closest to the jungle
- Connect 5V to switch the switch to 1KR and solder after the existing R028 inline resistor on the blanking circuit
___




## Differences by Model

## Notes, Tips, and Tricks

The following notes are in no particular order or grouping. These are just some things I encountered while modding that I think are useful to know or look into.




