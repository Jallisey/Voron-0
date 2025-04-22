# Voron Zero

 
## Formbot V0.2r1 Kit

- Kirigami Bed Frame
- BTT Pi V1.2
- BTT SKR Pico
- BTT V0 Display
- Revo Voron Hotend 24v
- Double Sided PEI Sheet
- Crimped Wiring Looms
- Moons Motors
- Stainless Steel Rails
- MIC6 Cast Aluminum Build Plate
- Polycarbonate Panels
- Gates Belts
- Vivedino 60W Silicone Bed Heater
- Stainless Steel Hardware
- Umbilical Board + Harness
- NOT Makerbeam XL Extrusion!!! LDO Style
- Meanwell 150W PSU

## Motor Models

Helpful for the Autotune TMC Klipper Plugin

- A/B - MS14HS5P4150-11
- Z - LE174S-T0808-200-0-S-065
- E - CSE14HRA1L410A-01

Link: <https://github.com/andrewmcgr/klipper_tmc_autotune>

### Max Motor Currents

- A/B - 1.5A
- Z - 0.65A
- E - 1.0A
- 
### 65% Run Currents

Voron recommends 60-70% (0.6-0.7) to start
I chose 65%. Increase as needed but try to stay below 80-90%

Run Current = rated_motor_current x 0.707 x 0.65

Plug the max currents above into the equation with your desired percentage

- A/B - 0.65 x 0.707 x 1.5A = 0.69 (NICE!)
- Z - 0.65 x 0.707 x 0.65A = 0.3A
- E - 0.65 x 0.707 x 1.0A = 0.46A

### Thermistors

- Formbot Bed - "Generic 3950"
- Formbot V6 CHC Hotend - "ATC Semitec 104NT-4-R025H42G"
- Check Klipper docs for the correct sensor type based on your thermistor/hotend

### Extrusion Identification

All of the extrusions in the Formbot V0 kit are tapped on both ends. This means that using the V0 Manual extrusion identification diagrams can be a bit confusing. For 4 sets of extrusions where the manual differentiates them by tapped ends, you can consider those extrusions to be identical.

![Extrusions Identification](Images/Kit/formbot-v0-kit-extrusions-organized.jpg)

#### Identical Extrusions

- A/B
- C/H

## Kirigami Bed

![Kirigami Bed](https://github.com/christophmuellerorg/voron_0_kirigami_bed/blob/master/Images/stealth_beta.png?raw=true)
GitHub: <https://github.com/christophmuellerorg/voron_0_kirigami_bed>

Manual: <https://github.com/Kagee/kirigami-bed-manual>

LDO Kirigami Docs: <https://www.ldomotion.com/p/guide/18295873486461670>

Remixed Formbot V0.2 Kirigami Frame Nutblock By @manisto: <https://www.printables.com/model/837960-kirigami-bed-nut-block-for-voron-v02>

Remixed Formbot V0.2 Kirigami Frame Chain Mount: **User Deleted. Need New Model**

The Formbot kit only comes with the Kirigami Frame. There's no LED/PCBs/Wago connectors, etc... included with the kit. You can source these yourself, find a partial wiring kit that includes them, or just leave them out and hard wire the bed components. See my My Mods section for the kit I bought.

The Kirigami bed frame is a great mod/upgarde that comes with the kit. It replaces multipe extrusions and printed pieces with a single rigid bed frame. The LDO Docs and Kirigami manual by Kagee provide some great info on general installation of the bed.

I had some trouble with the provided bed. I was able to get through all the issues with small DIY fixes. Other people have also noted they've run into these issues on the Voron Discord as well as the Kirigami GitHub. YMMV

## V0 Umbilical

GitHub: GitHub: <https://github.com/VoronDesign/Voron-Hardware/tree/master/V0-Umbilical>

![V0 Umbilical](Images/Wiring/Formbot-V0-Umbilical.png)

The V0 Umbilical is a great mod included in this kit. It makes wiring much easier. All of the signals/power to the toolhead goes through a toolhead PCB breakout board, down to the back of the frame via a pre-made wire harness, through a second frame pcb breakout board and finally down to the SKR Pico.

Formbot has precut and crimped most of the wires that go from the mainboard to the frame PCB. They've also made most of the wires that hook into the toolhead pCB the correct length as well.

Be sure to print the V0 Toolhead PCB mount and strain relief found here:
<https://github.com/VoronDesign/Voron-Hardware/tree/master/V0-Umbilical/STLs/V0.2>

## Wiring

### General Wiring

![Stock Formbot V0.2(r1) Wiring Diagram](Images/Wiring/formbot-voron-v0.2r1-kit-wiring-diagram.png)

This is a general wiring diagram for a Formbot V0.2(r1) kit. The only thing specific to the `V0.2r1` is the Filament Runout Sensor (FRS) which gets plugged into the `E0 Endstop` input on the SKR Pico (next to the RGB/Neopixel). Otherwise it should serve pretty well as a general `V0.2` build.

Since the `V0.2` uses sensorless homing on the X-Y/A-B axes there's no endstops plugged into either of those inputs. In fact it's important to ensure that nothing is plugged into these inputs. Otherwise sensorless homing will not work.

** Note: ** Use this wiring diagram as a guide, but be sure to follow the polarity from the SKR Pico all the way up to the Umbilical PCB and out of the Toolhead PCB. I highly recommend using a multimeter to check for continuity of the pos/neg at the board and toolhead PCB. Some fans or intermediate wires ** MAY ** be pinned backwards. If this is the case I suggest depinning the connector and swapping the wires to ensure the correct polarity is carried all the way up to the fans.

There is no polarity for thermistors or heaters!

### Kirigami Bed Wiring

The Formbot kit does **NOT** include any wago or inline connectors!

The Kirigami Bed Frame alows splitting the wiring coming out of the bed so that the bed can be removed and worked on without being tethered to the printer.

Voron recommends using Wago connectors to allow easily disconnecting the wires. The Kirigami bed mod includes mounts for the Wago connectors.

Since the Formbot kit bed heater doesn't include an integrated thermal fuse it needs to be connected inline with one side of the bed wires.

![Bed Wiring](Images/Wiring/v0.2r1-cable-management-05.jpg)

### Generic Formbot Wiring

![Generic Formbot Kirigami Wiring](Images/Wiring/Formbot-Kirigami-Generic.png)

An inline connector can be used to split the Thermistor wires under the bed.

** NOTE: User [@Carlsans] (https://github.com/Carlsans) mentioned his Formbot kit came with a preinstalled [thermal fuse] (https://github.com/SrgntBallistic/Formbot-V0/issues/3)

### Formbot Wiring + LDO Kirigami Wiring Kit

![Generic Formbot Kirigami Wiring](Images/Wiring/Formbot-Kirigami-+-LDO-Wiring-Kit.png)

The LDO wiring kit includes 2 Wago mounts, a Thermistor breakout PCB and an LED PCB. A third wago is needed for the Formbot Thermal Fuse. The LDO V0 repo has stls for mounting its PCBs and the wagos. See the Kirigami Manual for more info.

### BTT Pi Power

Formbot provides a precut, pre-crimped wire harness to go from the BTT SKR Pico's top right pins over to the BTT Pi V1.2's VCC and GND GPIO Pins. It provides 2 5V wires and a single ground. I think these were design to work with an original Raspberry Pi 3/4 which has it's GPIO on the right.

![Pi Power Wires Janky](Images/Wiring/btt-pi-power.jpg)

Since the BTT Pi has it's GPIO on the left the only way to get the wires over to those pins I had to stretch them across both boards. I felt the looked bad and worried about the tension.

![Pi Power Fixed](Images/Wiring/v0.2r1-cable-management-03.jpg)

To solve this I used their JST connector and repinned/crimped the some longer wires with Dupont connectors on the opposite side. With the wires longer I can pas them under the edges of the boards and through the cable management channel in the middle

### BTT Pi to BTT SKR Pico Uart Communication

By default the Formbot kit connects the BTT Pi and SKR Pico by USB cable. This works well and is easily set up. However, it does limit the number of open USB ports to two (one is also taken up by the V0 Display). Since I also added a Klipper Exander and USB camera that meant all four ports were used. Leaving none for things like a USB Input Shaper Accelerometer.

Connecting the Pico and Pi via UART opens up a spare port again to help with this.

As noted in the section above the Formbot kit powers the the Pi via two +5V and a single GND set of wires going from a JST port on the SKR Pico to the GPIO Pins on the Pi. This is actually the UART comms header on the SKR Pico so we can easily add two wires (Green and Yellow in the Wiring Diagram) to free up the USB Port.

One end needs to be crimped with a JST XH connector and the other needs to be female duponts. Since this will only be transmitting data the guage isn't hugely important. You can use already crimped female-to-female Dupont bread board wires cut to size and crimped with a JST on one end. OR in my case take a pre-crimped JST wire and crimp a Dupont (harder to crimp) connector to the other end.

Then plug the extra two wires into the 5 pin JST connector housing on one end, and the Dupont connects onto the pins adjacent to the power pins on the Pi GPIO.

![UART Wiring](Images/Wiring/formbot-voron-v0.2r1-kit-uart-wiring-diagram.png)

You'll need to shut down the Pi remove the SD Card, plug it into a computer and open the `BoardEnv.txt` file on the boot sector of the card. In that file change the line with `console=`and set it to `console=serial` to tell the Pi to talk via it's UART interface.

From there you can put reconfigure the Pico firmware to use `UART0 GPIO1/GPIO0` for it's communication interface. Flash it via USB. Disconnect the USB and connect it via the new UART cable. Finally in your `printer.cfg` change the `serial:` portion of the MCU definition to `/dev/ttyS0`.

You should then be able to reboot the Pico and communication between the board and the Pi should work as normal

