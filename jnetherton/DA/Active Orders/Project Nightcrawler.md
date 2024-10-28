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
-  Do we still want W2 healthy voltage TLED?
- Ok to leave mech failure TLED's as is?
- No W2 Maint. Mode Output or Input contact (instructions said to only use PB for W2 maint mode)?


- Look over bus logic (W2 is source instead of W1) - not cable tie fault
- S1 live purely indication - no timers
- Add ERMS - shift elements - don't interlock with Local/Remote - ASK
- Update DP for PSU
- check pct02/09 that they don't block anything
- transformer inrush for W1 - are they fine with keeping?
- Can they provide coordination study so we can take a look at settings?


Changes:
- Commented out W2 close output contact
- Set W2 close variable to 0
- TLED's
	- Remove Auto-Blocked and MB Failure
	- Added W2 PTX Alarm
	- Spread out PTX Alarms so each gets a dedicated LED


PSV50 := (((67SP1T OR 67SP2T OR 67SG1T OR 67SG2T OR 51T01) AND NOT PSV29) OR R_TRIG PSV26 OR R_TRIG PSV56) # TRIP W2 IF OC ELEMENTS TIMED OUT AND NO BLOCK RECEIVED

67TP1T OR 67TP2T OR 67TP3T OR 67TG1T OR 67TG2T OR (51T02 AND NOT (67TP2 OR 67TP3)) # WAY 3 OC ELEMENTS