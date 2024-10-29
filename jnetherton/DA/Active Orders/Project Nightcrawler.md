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
- Does local/remote apply for W2 ERMS PB?
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


PSV01 := ((R_TRIG ACT01Q AND PLT01) OR (R_TRIG RB03 AND NOT PLT01)) AND PSV10 AND SF6_OK AND NOT PSV18 AND NOT ALT09 OR (PSV01 AND NOT PSV11 AND NOT PCT05Q) # W1 OPEN - LATCHES IN UNTIL SUCCESFUL OR TIMEOUT
- local and remote open
- W1 closed
- sf6 ok
- 

PSV02 := ((R_TRIG ACT02Q AND PLT01) OR (R_TRIG RB04 AND NOT PLT01 AND PSV23)) AND PSV11 AND SF6_OK AND PSV31 OR (PSV02 AND NOT PSV10 AND NOT PCT05Q AND NOT PCT26Q) # W1 CLOSE - LATCHES IN UNTIL SUCCESFUL OR TIMEOUT

PSV03 := (((R_TRIG ACT03Q AND PLT01) OR (R_TRIG RB05 AND NOT PLT01)) OR F_TRIG PSV55) AND 52CLS AND SF6_OK AND NOT ALT10 OR (PSV03 AND 52CLS AND NOT PCT06Q) # W2 OPEN

PSV05 := ((R_TRIG ACT05Q AND PLT01) OR (R_TRIG RB07 AND NOT PLT01)) OR (PSV05 AND 52CLT AND NOT ACT28Q) # W3 TRIP

PSV06 := ((R_TRIG ACT07Q AND PLT01) OR (R_TRIG RB08 AND NOT PLT01)) OR (PSV06 AND 52CLU AND NOT ACT29Q) # W4 TRIP


