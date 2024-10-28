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
- PTX alarms - only 1 alarm for W2, but 4 different alarms for other ways? (high temp, low/high press., low oil)


Changes:
- Commented out W2 close output contact
- How should I handle mech failure TLED's?
- TLED's
	- Remove Auto-Blocked and MB Failure
	- Added W2 PTX Alarm
	- Spread out PTX Alarms so each gets a dedicated LED



ALT10S := R_TRIG BFITS OR R_TRIG PCT06Q OR ACT10Q OR ACT11Q # W2 MECH ISSUE
ALT11S := R_TRIG BFITT OR R_TRIG ACT28Q OR ACT12Q OR ACT13Q # W3 MECH ISSUE


AMV030 := 0.500000 # TIMER FOR MANUAL VFI OPEN OPERATION FAIL
ACT28PU := AMV030
ACT28IN := PSV05 # W3 MANUAL OPEN

PCT06DO := 30.000000 # OPERATION FAILURE INDICATION PULSE LENGTH
PCT06PU := AMV008 # MOTORIZED OPERATION FAILURE TIME
PCT06IN := PSV03 OR PSV04 # W2 OPERATION FAILURE TIMER