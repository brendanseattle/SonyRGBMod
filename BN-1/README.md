# Sony BN-1 RGB Mod
### (KV-9PT50, KV-9PT60, etc)

<img src="https://user-images.githubusercontent.com/41927604/193102948-0b21a97f-89a2-4627-aa30-4a912703e66b.jpg" width="600" />

RGB Mod for Sony BN-1 CRT televisions.

Written by Brendan Eddy (FlyingFlygon). Credits to:
* Stabarz for Y/C Jungle information

## Overview

This RGB mod is noteworthy because it is _not_ a mux mod - meaning we are not going to be multiplexing our external RGB signal with the set's OSD RGB input. Instead, we can simply input our RGB singal to the Y/C jungle integrated circuit (IC301 CXA1465AS) directly. This is possible due to the jungle having unpopulated pins for RGB input and blanking. So the mod ends up being as simple as plugging your lines directly into those pins.

![YCJungle](https://user-images.githubusercontent.com/41927604/193158816-3feb0990-86c8-4f46-a845-07bf3442c835.jpg)


## Components Needed

Since there's no multiplexing, the only resistors needed are those for your blanking line and terminating to ground.

* Properly shielded wires (I use 24 AWG)
* 2x 1k Ohm resistors
* 3x 75 Ohm resistors
* 3x 0.1 uF ceramic capacitors
* 1 SPDT switch
* 3 BNC chassis mount solder type female jacks
* Your choice of adapter for sync line (Most likely, BNC->RCA)

## Modification Steps

This mod will be done in three distinct but related parts: wiring the RGB and ground lines, wiring the blanking lines, and installing the BNC connectors in the case. 

1. First, disassemble the TV and disconnect the anode cap and other wires holding the board in place. On these sets, there are some wires on the neckboard that are permanently soldered on each end, so you won't likely be able to take it all apart. No worries - as it's easy enough to set it on its side with the tube face down.

<img src="https://user-images.githubusercontent.com/41927604/193157514-56513f1a-40bf-4d95-9d35-b5086b38ab3f.jpg" width="400" />

2. Solder a wire to a 5V source on the board. There are likely many places you can do so. I chose a leg of the Q607 transistor as the schematic states it outputs into the Set 5V circuit.

<img src="https://user-images.githubusercontent.com/41927604/193157941-091ce4cb-1742-4c9f-9930-64bc573fac64.png" width="300" />

Route your wire from this transistor up to the input section of the case. You can poke it through some small holes near the tuner to keep it snug.

<img src="https://user-images.githubusercontent.com/41927604/193157870-e50dc64c-445d-462c-98d9-ccc02f1acf59.jpg" width="500" /> <img src="https://user-images.githubusercontent.com/41927604/193157876-3e5c09ed-579b-4468-9cb5-5d98dc6f0be0.jpg" width="300" /> 

3. Solder a wire to an audio/video ground pin and route it the same way.

<img src="https://user-images.githubusercontent.com/41927604/193158677-2a422a02-66e4-424e-940b-b2fd156967e6.jpg" width="500" />

4. Identify and cut pins 15, 16, 17, and 18 of the Y/C Jungle chip (IC301 CXA1465AS). Alternatively, you can cut the traces on the other side or figure out a circuit to ensure the signal doesn't get grounded, but I just do the easy way and cut the pins.

<img src="https://user-images.githubusercontent.com/41927604/193159204-61df232d-b7c5-412f-9a50-ed6608e87dc9.jpg" width="400" /> <img src="https://user-images.githubusercontent.com/41927604/193159213-2c1e9587-d45a-4250-a767-96ba1dfe615b.jpg" width="400" />

5. Solder your blanking, red, green, and blue wires to pins 15, 16, 17, and 18 respectively. (Note - this picture is from my PT60 while the rest are from my PT50. I forgot to take a picture for the latter, so I artistically corrected the color of the blanking line to ensure it matches with the rest of the pics. In my PT50 I actually soldered from above since it gives more clearance with the capactors next to the IC. Either way is fine.)

<img src="https://user-images.githubusercontent.com/41927604/193159611-152a0416-6d2e-40c4-b11c-a80dccb59bee.jpg" width="400" />

6. Optional - crimp your wires to utilize quick connectors (JST). I chose to go this route so that I can keep a short run of wires and be able to disconnect the case once the mod is done. If you choose not to do this, you can skip this step and just have longer wires that can extend to your BNC connectors on the case. 

<img src="https://user-images.githubusercontent.com/41927604/193159948-dd6a86bd-7d1c-438a-a6c6-922ee56db664.jpg" width="400" /> <img src="https://user-images.githubusercontent.com/41927604/193159953-63cf9cf7-3c17-4393-85f0-a0f9d3b6fe72.jpg" width="300" /> <img src="https://user-images.githubusercontent.com/41927604/193159957-479fc526-0da6-4721-b6de-03d3620d99d4.jpg" width="200" />

7. Your blanking circuit will involve the wire to pin 15 (yellow in my case) and the wire to the 5V regulator (white in my case). The 5V line will be the center pull of your switch, while the blanking line will be one of the throws. The other throw can be left unpopulated or sent to ground if you really care about safety. I read the voltage of the regulator and it came to about 5.6V, so I attenuated it with two 1k Ohm resistors to bring it down to a level I am more comfortable with. Honestly, I could have brought it down even more. Feel free to experiment with this and find what works best. 

<img src="https://user-images.githubusercontent.com/41927604/193160395-74433892-5712-4b95-b0b7-36685d33e364.jpg" width="500" />

8. Prepare your BNC connectors for the RGB line connection. This will involve the coupling capacitors, the terminating resistors, and attaching the ground line to the tabs of the connectors. I recommend you do this all before modifying the case so that you can test the mod first. 

Start with the ground tabs. I daisy chain them together with small wires, and connect one of them to the ground point we connected earlier (black wire). Also solder in the 75 Ohm resistors.

<img src="https://user-images.githubusercontent.com/41927604/193162625-3c7ee8ea-a971-406e-a081-3598d332fe08.jpg" width="500" />

Next, you can solder the coupling capacitors and attach the 75 Ohm resistors to the video line.

<img src="https://user-images.githubusercontent.com/41927604/193161706-4dc0531d-2eb9-48f7-b8a2-85d2dc5d1535.jpg" width="500" />

Lastly, connect your red, green, and blue wires to each and test with your console. If everything looks good, disconnect the terminating resistors and the RGB lines so you can insert the BNC connectors into the case (step TODO). 

9. Case modification will always be up to personal preference. In my opinion, I'm not too worried about cutting holes as long as it doesn't make a huge impact. For this reason I decided the rear corner of the case is an alright solution. I used a small drillbit to outline the circles for the BNC connectors, and a file to smooth it out. Same for the switch hole.

<img src="https://user-images.githubusercontent.com/41927604/193163294-64b521fa-092f-464f-9d7f-6a006ebf4617.jpg" width="400" />

10. Once you have decided on placement, you can install the switch and BNCs. If there's a snug enough fit, it should just be a matter of screwing them in. I opted to add some hot glue as well because my fitment wasn't perfect.

<img src="https://user-images.githubusercontent.com/41927604/193163726-9642f9d2-10ec-4ffd-8044-153e94c9f2bb.jpg" width="400" />

Once you have a tight fit, go ahead and resolder the 75 Ohm resistors to the video lines. 

<img src="https://user-images.githubusercontent.com/41927604/193163937-7566133c-8a33-4c8f-9915-66a0af26c10d.jpg" width="400" />

The last step is to resolder the RGB lines to the coupling capacitors. This is where having quick connectors is handy since you can move the case around and twist the wires as needed. 

<img src="https://user-images.githubusercontent.com/41927604/193164071-65ae8138-864e-41b1-b1f8-cad0b6ca8c4c.jpg" width="400" />

Finally, we can connect both ends of the mod and reassemble the set.

<img src="https://user-images.githubusercontent.com/41927604/193164143-f15c8c7a-ec3e-44a0-b5df-d91af6fdf05e.jpg" width="600" />

## Differences by Model

* The PT60 model is the higher-end of the two, with a larger power supply block sticking out from the board and a power cable that can be disconnected. I recommend disconnecting the cable as it makes maneuvering in a tight spot easier. But the rest of the mod is the same. 

## Notes, Tips, and Tricks

* Sync should be sent directly into the composite video port. If your cables are 4 BNC (one each for red, green, blue, and sync) you'll want to get a BNC to RCA adapter to be able to plug your sync line into the stock composite port. 
* SCART port RGB mods are popular as a lot of RGB equipment utilizes SCART, but I would find it nearly impossible to fit such a large port anywhere on this tiny case. That's why I opted for the small cluster of BNC connectors in the back corner. 

## Sources and Further Readings
* Stabarz' RGB mod for KV-13TR29 (etc) models: https://imgur.com/a/Cq2Yngd
