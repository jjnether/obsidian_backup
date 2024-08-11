Stack code 550



-   554 AE hold - waiting for AE to get your answer, order
    -   If something is wrong, write an AE NCR, change to 554, and it puts it in a hold pattern





A and S lane (fast lane)

-   automation (order is already configured from a design standpoint)
-   S is for shanghai
-   Levels 1 and 1plus



V lane

-   EE level 2
-   More design changes

U lane

-   More complex underground stuff

JDE is for A and S lane, U and V lane uses smart sheet

-   551 is smart sheet

Pole

Substation

Pad-mount

Record

Approval

Proposal

SEL

-   Check secondary input voltage
-   (6) 8 Vac Max LEA Inputs
-   If hooking up a PT, power supply must have 120 Vac
-   Print to PDF
-   Also get dimensions at bottom (pdf)
-   Make sure control voltage sensing matches the recloser

ODC - customer change

Overcurrent protection note: 50P, 50G, 51P, 51G



Density Switch (DS) or Low Pressure wiring device (LPWD) notes are in motor control standard

Encoder motor doesn't need internal feedback

Mag latch - only opens

Mag actuator - opens and closes

Pad-mounts use only solid-di PT's



PT BIL rating should be as good or stronger than control and switch BIL rating

Fuses only used on solid di, not oil filled



220.021 - general drawing requirements

222.601-1a - Cable Selection Table standard

227.002-1a - Viper S Configuration Table

What are things to check on SEL, comparing with AECS



If you have motors, you need low pressure warning device





Viper-s ABC

Viper-ST 123

Pad-mounts - ABC

Switch BIL ratings

38kV - 150kV

27kV - 125kV

15.5kV - 110kV

CT polarity dot on z-side (flow from line to source)



24V platform for trip boards, motor boards, etc.



Mainly overcurrent protection

Overhead - 651

Underground - 751

Metering - 735

Differential Protection - 411

Module section done by mechanical group

Each is a formC

![Machine generated alternative text: S2A CLOSED STATUS OPEN NOT S2A 52B STATUS NOT 52B GROUND (YEL/3LK) (ELK) (YEL) (BLU,'BLK) (ORG) (BLU) (RtO/BLK) (ERN) (RED) CONTACT CABLE (10/0 (AUXI 5EE CONTROL OR JLJNcr10N sOX GROUND STATUS NOT GROUND ](Quick-Notes-PE-image1.png){width="9.854166666666666in" height="5.166666666666667in"}

Record - what you need
-   Wiring diagram
-   Control and its BOM
-   Lower level components like enclosure, relay drawing, wiring kit (wiring diagram with accompanying reference diagrams)



Approval - what you need
-   Wiring Diagram (if asked for) (no connection logic diagrams needed in EEH unless new drawings)
-   Rough view of control (panel view if asked for)
-   The rest depends



300 VAC - HEA

8 VAC - LEA



Each micro switch is form-C

-   Both NO and NC

2FormC is standard

SWITCH IS EQUIPPED WITH ONE FIBERGLASS NEMA 4X JUNCTION BOX. JUNCTION BOX INCLUDES SIX 24-POINT TERMINAL STRIPS AND A 12A FUSE BLOCK. JUNCTION BOX CONTAINS CUSTOMER CONNECTIONS FOR THE AUXILIARY CONTACTS ON ALL WAYS, AUXILIARY-IF CONTACTS ON ALL WAYS, EXTERNAL POWER/ EXTERNAL TRIP FEATURE ON WAYS 2, 3, 4, AND 5, LOW PRESSURE WARNING DEVICE, AND POTENTIAL TRANSFORMER SECONDARY CONNECTION.

AUX-IF - intended for G&W use

AUX - for customer use



ME decides which bushing PT is attached to (for notes section)

ME handles phasing test pins (we do top level note for it with VS section)



VI Controls: 1 and 2 don't need programming kit, 2 and 3 do



Sales Code 4: 800 for Pole Top

Sales Code 5: 600 for Electrical (always used)



External CT's should always be hooked up to a shorting block - if there's no relay
-   test switches with the shorting feature also works for ug controls
-   we'll do internal CT's on them as well if the customer asks for them, or if they're not wired to the control



If a check-sheet calls for Trident-S, use compact trident instead (we don't make trident S anymore)



EEH CT section is only asking about external CT's

![Machine generated alternative text: Type 1 • Smart Part Number • B5402 0029 AOI • B54020029A ENCLOSURE A = NEMA4X Type 1 B = NEMA4X CLR LID Type 1 C = NEMA 6P Type 1 D = NEMA4X Type 2 E = NEMA 4X CLR LID Type 2 F = NEMA 6P Type 2 3 TIEPET 1 = 500•.1 CT 2 = 500:1 12-24V EP/ET 3 = 500•.1 48V EP/ET 4 = 500:1 120V EPIET 5 = 500:1 220V EP/ET A = 1000•.1 CT B = 1000•.1 12-24V EP/E C = 1000:1 48V EP/ET D = 1000:1 120V EPIET = 1000.1 220V EP/ET ENTRY O = LEFT 1 = BOTTOM 02 = RIGHT 3 = LEFT with EPIET 4 = BOTTOM with EP/ET 5 = RIGHT with EPIET ](Quick-Notes-PE-image2.png){width="11.4375in" height="8.625in"}

When setting something to obsolete, you won't get the "set state" option if it's not released and if it's not the latest of the version (can't obsolete A.1 when A.2 exists)



GWI control note:

-   GWI-DASalesOrder-Line (ex GWI-DA100504-1)
    -   It's just a pn we pull, meaning you can find similar pn's in jde



UBOM - AFTER TABLE SELECTED
-   Upload Single Level BOM
-   Submit (no check marks selected)
-   File name (with .txt extension)



VS Wiring:

-   VA (BLK-1)
-   VB (WHI-1)
-   VC (BLK-2)
-   VN (WHI-2)
-   Drain - if going to a j-box, drain should be hooked to the terminal strip so the customer can shield the signal from the j-box to the control



Wiring Kit: A64751344*

Logic Diagrams: B13440053*



Labels: X:SWG_EngEE FolderProductLabels

Label heat shrink: A13410113*



No * on EP/ET wiring (only CW)

* is only on microswitches



For multiple EP/ET, add jumpers and one input for 120VAC

![](Quick-Notes-PE-image3.png){width="10.0in" height="7.520833333333333in"}

B13440054ATF - NEW JBOX WIRING 3 WAY EPET



SCHEMATICS:



If getting * when you want a blank field, put in a space for the parameter instead of leaving it blank



For description, update in Design Properties under Design



For check-in:

-   If importing an old schematic, it will always fail the first check-in, then should work the second time
-   If you get an error about stale secondaries, select remove stale secondaries and try again



For "used on", use top level PN

-   For other things like PT wiring diagram, can just leave "used on" blank



For updating title section:

-   Design > Edit Global Parameters
-   On left, select DOCUMENT > FORMAT
-   Edit Values (hit green check for each) and close
-   G&W Diagramming > Model Explorer
-   Select everything below Design folder on left
-   Hit remove on everything in bottom box
-   Hit Set... next to Type
-   Select FORMAT and hit Ok
-   Apply and close
-   Update All Sheets



OR FOR EACH PAGE

-   Right click sheet tab, hit properties, and edit from there



For updating sheet numbers and total:

-   G&W Diagramming > Location Set Explorer
-   If ordering is correct, but there's a gap in the sequence, hit "remove any gaps..." button on the right



Wiring AWG

-   18 unless specified
-   For 120VAC, 14AWG from switch to power supply to VSR to terminal block then 18AWG from terminal block to GFCI, Fan, Heater, etc. only got to the terminal block if you have more than two devices if you have two you can do 18AWG from the VSR to those devices



harnesses are used to go from the backpanel to the swing frame or vice versa

cables are used to go from components on the same plane



Fiber End Details:

-   Design > Design Properties > Fiber End Details (In. values should usually be 0.1)



For ° USE ALT+0176



We need to make sure the spares are also at the top.

We should arrange the signals as seen below per our "standard":



<top of terminal block>

BLANK SPACES

MOTOR

AUX IF

CT MAG

LPWD

VS

AUX VB

AUX

24VDC PWR

<bottom of terminal block>



For CT's, tie all neutrals together and ground at the test switch

![Machine generated alternative text: Motor Interface Board Operating Modes TW&Position Encoder Motor TW&Position Internal Feedback Load area k Motor Three-position Encoder Motor Three-position Internal Feedback TW&Position Encoder Motor Fault Interrupter motor TW&Position Internal Feedback Position I Position 2 Position 3 Position 4 Position 5 Position 6 ](Quick-Notes-PE-image4.png){width="12.25in" height="2.2083333333333335in"}



Top level note for VS for customer use:

SWITCH IS EQUIPPED WITH VOLTAGE SENSING BUSHINGS AND PHASING TEST PINS. THE BUSHINGS ARE CONNECTED TO THE CONTROL USING SHIELDED TWISTED PAIR CABLE FOR CUSTOMER USE. THE SENSORS WILL BE CUSTOMER CALIBRATED. VOLTAGE SENSING DESIGNED TO WORK ON SYSTEMS WITH

NOMINAL PRIMARY VOLTAGES BETWEEN 4.6 - 21.9KV PHASE TO GROUND. MAXIMUM OUTPUT OF VOLTAGE SENSING IS 8 VAC WITH A 5000:1 RATIO.




