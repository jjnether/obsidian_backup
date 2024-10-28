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
- Inrush for W1?
- Can they provide coordination study so we can take a look at settings?
- Does local/remote apply for W2 ERMS PB?


- Fix open/close variables
- Clean up SER triggers?

PSV01 := (((R_TRIG ACT01Q AND PLT01) OR (R_TRIG RB03 AND NOT PLT01)) OR (R_TRIG PSV51 AND PLT02) OR F_TRIG PSV58) AND PSV10 AND SF6_OK AND NOT PSV18 AND NOT ALT09 OR (PSV01 AND NOT PSV11 AND NOT PCT05Q) # W1 OPEN - LATCHES IN UNTIL SUCCESFUL OR TIMEOUT

PSV03 := (((R_TRIG ACT03Q AND PLT01) OR (R_TRIG RB05 AND NOT PLT01)) OR (R_TRIG PSV53 AND PLT02) OR F_TRIG PSV55) AND 52CLS AND SF6_OK AND NOT ALT10 OR (PSV03 AND 52CLS AND NOT PCT06Q) # W2 OPEN

PSV05 := (((R_TRIG ACT05Q AND PLT01) OR (R_TRIG RB07 AND NOT PLT01)) OR ((R_TRIG PSV14 OR R_TRIG PLT16 OR (R_TRIG PLT09 AND PSV11 AND NOT 52CLS)) AND PLT02) OR F_TRIG PSV58) OR (PSV05 AND 52CLT AND NOT ACT28Q) # W3 TRIP