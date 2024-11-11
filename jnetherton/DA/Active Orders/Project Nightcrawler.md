- MOT is same between 4 way and 6 way
- Consistency for Way 2
	- modify design template
	- ERMS
		- PB02 used for ERMS (works no matter in local or remote)
	- PTX alarm
- IN303 group alarm
- Make new DNP map and test
	- No binary outputs (no commands)
	- Way 2 LEA and current
- KND POD

NOTE:
- 14 switches done within 3-day time-span
- PSV58 nowhere to be found, used in W1, W3, and W4 open equations?
- Clean up SER triggers?

TESTING:
- 50P - .5
- 50G - .3
- 51P - .2
- 50P Maint Mode - .1

---

PSV01 := ((R_TRIG ACT01Q AND PLT01) OR (R_TRIG RB03 AND NOT PLT01)) AND PSV10 AND SF6_OK AND NOT PSV18 AND NOT ALT09 OR (PSV01 AND NOT PSV11 AND NOT PCT05Q) # W1 OPEN - LATCHES IN UNTIL SUCCESFUL OR TIMEOUT
- local and remote open
- W1 lb closed
- sf6 ok
- W1 below 600A
- No W1 mech issue
	- or
- PSV01
- W1 lb not open
- no W1 operation failure timeout
	- removed:
- PLT02 term - auto mode
- PSV58 - F_TRIG of all bus fault indications - used to open all ways

PSV02 := ((R_TRIG ACT02Q AND PLT01) OR (R_TRIG RB04 AND NOT PLT01 AND PSV23)) AND PSV11 AND SF6_OK AND PSV31 OR (PSV02 AND NOT PSV10 AND NOT PCT05Q) # W1 CLOSE - LATCHES IN UNTIL SUCCESFUL OR TIMEOUT
- local and remote open
	- remote permissive
- W1 lb open
- sf6 ok
- W1 close permissive
	- or
- PSV02
- W1 lb not closed
- no W1 operation failure timeout
	- removed:
- PLT02 term - auto mode
- PCT26Q - DETECT CLOSE IN PROGRESS AT ADJACENT MVS AND CANCEL ANY CLOSE OPERATION

PSV03 := ((R_TRIG ACT03Q AND PLT01) OR (R_TRIG RB05 AND NOT PLT01)) AND 52CLS AND SF6_OK AND NOT ALT10 OR (PSV03 AND 52CLS AND NOT PCT06Q) # W2 OPEN
- local and remote open
- W2 closed
- sf6 ok
- no W2 mech issue
	- or
- PSV03
- W2 closed
- no W2 operation failure timeout
	- removed:
- PLT02 term - auto mode
- PSV55 - Open all ways from breaker failure on load fault fed from Way 1

PSV05 := ((R_TRIG ACT05Q AND PLT01) OR (R_TRIG RB07 AND NOT PLT01)) OR (PSV05 AND 52CLT AND NOT ACT28Q) # W3 TRIP
- local and remote open
	- or
- PSV05
- W3 closed
- no W3 open failure timeout
	- removed:
- PLT02 term - auto mode
- PSV58 - F_TRIG of all bus fault indications - used to open all ways

PSV06 := ((R_TRIG ACT07Q AND PLT01) OR (R_TRIG RB08 AND NOT PLT01)) OR (PSV06 AND 52CLU AND NOT ACT29Q) # W4 TRIP

PSV21 := (PSV11 AND NOT PSV02 AND NOT ALT02) OR ASV256 # W1 OPEN AND NO CLOSE IN PROGRESS
- W1 lb open
- W1 not closing
- W1 not timing to close
	- removed:
- 52CLS W2 closed
- PSV04 - W2 close
- ALT04 - W2 close timing
- extra PSV02 - redundant
- PCT25Q - PULSE EXTENSION THE LENGTH OF THE WALKAWAY TIMER TO BLOCK COMPETING CLOSE OPERATIONS

PSV23 := PSV21 # CLOSE PERMITTED BY LOCAL MVS
- BOTH LOOP WAYS OPEN AND NO CLOSE IN PROGRESS - LOCAL CLOSE PERMITTED
	- removed:
- PSV22 term - PERMISSIVE FROM ADJACENT MVS

PSV31 := NOT ALT09 AND NOT (ALT18 OR PLT11) # CONSOLIDATED W1 CLOSE PERMISSIVE
- no W1 mech issue
- no bus fault fed by W1
- no cable fault
	- removed:
- ALT17 - bus fault fed by W2 
- PLT09 - breaker failure on load way while in auto

PLT11S := R_TRIG ALT15 # LATCH TO INDICATE CABLE FAULT
- fault on W1
	- removed:
- PLT17 - TAKE ACTION FOR CABLE FAULT - TRANSFER TRIP RECEIVED WITH NO FAULT LATCHES

---
Inrush:
51 torque control := NOT ((PCT29Q AND NOT 52CLS) OR PCT31Q) # W2 PH TOC WITH INRUSH RESTRAINT
- 
	- removed:
- PCT28Q - ENERGIZATION OF MVS BUS THRU W2 - BLOCK TRIPPING ON ALL VFI WAYS