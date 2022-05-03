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

I will be detailing the mod using BNC connectors and an on/off switch. You can instead choose a SCART port that automatically switches using the 5V signal that should be provided from your RGB console. I have not done that myself, so I won't be giving a tutorial on that method yet.

For this mod you will need:
* Properly shielded wires (I chose 20AWG silicone wire, you can use smaller gauge however)
* 3x 2400 Ohm resistors (assuming you use diodes, see next section)
* 3x 1N4148 Logic diodes (assuming you use diodes, see next section)
* 1x 1000 Ohm resistor
* 3x 430 Ohm resistors
* 3x 75 Ohm resistors
* 1 SPDT (single pull, double throw) switch
* 3 BNC chassis mount solder type female jacks
* Your choice of adapter for sync line (In my case, I use BNC->S-Video for KV-27S42)

## Modification Steps

In order to implement the mux circuit, we need to remove the existing resistors on the OSD's R, G, and B lines and replace them with the appropriate value resistors that can attenuate our signal to 0.7V. We will connect our external RGB lines to these new resistors. Also, we need to implement blanking by an external switch. We will pull 5V from the set into the switch and throw it to the OSD's blanking pin through an appropriate sized resistor. 

![Sony-BA-4D---OSD-Mux-Circuit-with-Diodes md](https://user-images.githubusercontent.com/41927604/166327672-9cb0c464-649c-4389-90cd-98dad2a0e45c.png)
![Sony-BA-4D---Blanking-via-Switch md](https://user-images.githubusercontent.com/41927604/166327687-a96b2d13-3066-4fde-b11e-3a17121711c9.png)

##### Credit to MarkOZLAD

Let's break that down step by step. (Note, sections marked with an asterisk * may have differences by model. Check next section).
Pictures in steps 1-4 credit John M.

1. Locate and remove the throughhole resistors R025, R026, and R027 between the Microcontroller (Micon) chip (IC001) and Y/C Jungle chip (IC301).

<img src="https://user-images.githubusercontent.com/41927604/166329294-31490b43-3513-4b6a-b5f1-7b377c4041f6.png" width="400" /> <img src="https://user-images.githubusercontent.com/41927604/166329304-d1c05df7-dd81-44ec-a11a-6ae2ac787d74.png" width="400" />


2. Locate and remove the surface mount resistors R086, R087, and R088 on the underside of the board. *

<img src="https://user-images.githubusercontent.com/41927604/166325181-1a3ad6cf-4625-486e-85ea-68a7f084d674.png" width="300" /> <img src="https://user-images.githubusercontent.com/41927604/166329054-63de9141-0e3a-4c52-ad52-8e8f3aa4a606.png" width="350" /> <img src="https://user-images.githubusercontent.com/41927604/166329070-40a0e06b-a7d4-4bdd-960b-8290b032a2fc.png" width="350" />

3. Replace the throughhole resistors with 2400 Ohm soldered to the 1N4148 diodes. 

<img src="https://user-images.githubusercontent.com/41927604/166329771-2dbe3194-56bc-449a-968f-f983df38b8c2.png" width="500" />

4. Solder your R, G, and B wires to the leg of the diode closest to the Y/C Jungle (IC301). R025 is red, R026 is green, R027 is blue. 

<img src="https://user-images.githubusercontent.com/41927604/166329959-339a0ddc-960c-416b-ae45-0f653347fddd.png" width="500" />

5. Solder the other side of your RGB wires to a 430 Ohm resistor before reaching your external input (SCART/BNC etc). Terminate to ground by soldering the same end to a 75 Ohm resistor to ground. Here I use the tab on my BNC connectors for ground. 

<img src="https://user-images.githubusercontent.com/41927604/166331829-604e6aab-0086-43ac-a492-fcadd0751747.jpg" width="800" />


### Note
We came up with the 430 Ohm value through the following calculation:

![Sony-BA-4D---OSD-Mux-Circuit-Calculation](https://user-images.githubusercontent.com/41927604/166330401-9e8f1b6c-e449-4839-ad29-95375134bf5c.png)

If you choose to not use diodes, you can instead use a 330 Ohm resistor (assuming your resistor on the R, G, B lines is 2400 Ohm, which ours is).

![Sony-BA-4D---OSD-Mux-Circuit-without-Diodes](https://user-images.githubusercontent.com/41927604/166330673-f7b23ddd-6a00-4545-b922-f5feee326819.png)
##### Credit to MarkOZLAD for formulas

6. Attach another wire to the side of surface mount resistor R028 that connects to a throughhole leg. See schematic and example. This should go through a 1000 Ohm resistor * to match the voltage normally exiting R028. (NOTE: My picture here is the R028 on my KV-13M42, not the KV-27S42 as other pictures. However the location is very similar.)

<img src="https://user-images.githubusercontent.com/41927604/166333113-a9086432-233c-48a7-89d4-f02efbf5337d.png" width="400" /> <img src="https://user-images.githubusercontent.com/41927604/166333424-227c5158-24c2-41ab-bd9c-eb32344989c1.png" width="550" />

7. Attach a final wire to a 5V source on the board. An easy one in the same section of the board is the EEPROM chip (IC003). You can solder your wire to leg 8 like so.

<img src="https://user-images.githubusercontent.com/41927604/166333815-798be779-aa06-4ee9-aa1b-a84d71050350.png" width="700" />

8. Solder your R028/OSD wire to the middle leg of the SPDT switch. This is where the switch pulls from. Solder your 5V wire to one of the legs, and leave the other leg untouched. This sends the 5V back to the OSD blanking circuit when switched on, and to nothing when switched off.

<img src="https://user-images.githubusercontent.com/41927604/166334322-dc016701-815e-4c95-88f2-1c9d949c1b58.png" width="600" />

9. Cut into the back case of your set to mount your connectors in a way that suits you. Here's how I ended up doing mine (a second time...) on my KV-27S42. Also for your consideration is /u/Puzzleheaded-Sign-89's implementation with a SCART port.

<img src="https://user-images.githubusercontent.com/41927604/166334631-6e253c1a-bcd8-4efb-a323-6680b9f56821.jpg" width="450" /> <img src="https://user-images.githubusercontent.com/41927604/166334677-0ad372b6-8e28-482d-9d3c-fa3e8db7b0d1.png" width="450" /> 

## Differences by Model

## Notes, Tips, and Tricks

The following notes are in no particular order or grouping. These are just some things I encountered while modding that I think are useful to know or look into.




