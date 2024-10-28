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
- Set W2 close variable to 0
- Do we still want W2 healthy voltage TLED?
- Ok to leave mech failure TLED's as is?
- Ok to remove W2 
- TLED's
	- Remove Auto-Blocked and MB Failure
	- Added W2 PTX Alarm
	- Spread out PTX Alarms so each gets a dedicated LED