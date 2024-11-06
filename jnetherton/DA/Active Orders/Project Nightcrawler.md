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

Questions:
- New label layout ok?
- Inrush for W1? - STILL USE HARMONIC BLOCKING
- Can they provide coordination study so we can take a look at settings?
- Does local/remote apply for W2 ERMS PB? - keep consistent with other local/remote switches
- Bus fault
	- check how PSV14 asserts
	- Actually, we'll use ALT18
	- on bus fault, all load ways should open, Way 1 should stay closed and indicate fault
	- what level to set for W1 fault detection?
		- set in template

- Fix open/close variables
- Clean up SER triggers?
- Check open/close permissives

NOTE:
- 14 switches done within 3-day time-span
- no PSV58
- removed PCT26Q from PSV02
	- Also replaced PSV23 with PSV21

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
- PSV58 - doesn't exist???

PSV02 := ((R_TRIG ACT02Q AND PLT01) OR (R_TRIG RB04 AND NOT PLT01 AND PSV21)) AND PSV11 AND SF6_OK AND PSV31 OR (PSV02 AND NOT PSV10 AND NOT PCT05Q) # W1 CLOSE - LATCHES IN UNTIL SUCCESFUL OR TIMEOUT
- local and remote open
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

PSV03 := (((R_TRIG ACT03Q AND PLT01) OR (R_TRIG RB05 AND NOT PLT01)) OR F_TRIG PSV55) AND 52CLS AND SF6_OK AND NOT ALT10 OR (PSV03 AND 52CLS AND NOT PCT06Q) # W2 OPEN
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

PSV05 := ((R_TRIG ACT05Q AND PLT01) OR (R_TRIG RB07 AND NOT PLT01)) OR (PSV05 AND 52CLT AND NOT ACT28Q) # W3 TRIP
- local and remote open
	- or
- PSV05
- W3 closed
- no W3 open failure timeout
	- removed:
- PLT02 term - auto mode
- PSV58 - doesn't exist???

PSV06 := ((R_TRIG ACT07Q AND PLT01) OR (R_TRIG RB08 AND NOT PLT01)) OR (PSV06 AND 52CLU AND NOT ACT29Q) # W4 TRIP

PSV21 := (PSV11 AND NOT 52CLS AND NOT PSV02 AND NOT (ALT02 OR PSV02)) OR ASV256 # BOTH LOOP WAYS OPEN AND NO CLOSE IN PROGRESS - LOCAL CLOSE PERMITTED
PSV21 := (PSV11 AND NOT 52CLS AND NOT PSV02 AND NOT (ALT02 OR PSV02)) OR ASV256 # BOTH LOOP WAYS OPEN AND NO CLOSE IN PROGRESS - LOCAL CLOSE PERMITTED
- W1 lb open
- W2 not closed
- W1 not closing
- W1 not timing to close
	- removed:
- PSV04 - W2 close
- ALT04 - W2 close timing
- PCT25Q - PULSE EXTENSION THE LENGTH OF THE WALKAWAY TIMER TO BLOCK COMPETING CLOSE OPERATIONS

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

- PSV58 nowhere to be found, used in both W3 and W4 open equations?