  
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\121288 - Minnesota Power Co>)  

IP:
- relays: 192.168.1.5-10
	- DNP: 1-6
- RTAC: 192.168.1.2

Voltage Ratio - 10000:1
CT Ratio - 1000:1

System Voltage - 19.92kV
Live - 15.936kV
Under - 11.952kV
Dead - 2.988kV - (8KV for Sec Z side)

Auto Timings:
- Auto Open - 75s (4500cyc)
	- Alternative - 30s (1800cyc)
- Auto Close - 90s (5400cyc)
	- Alternative - 45s (2700cyc)
- For alternative, set total upstream reclosing time to 15s


CPS POD:  
- 66402  
- 76820  
- 107931  
  
Other MP switches:  
- 117837
	- D8706PT3LEH0
	- D8706PT1LNP0
	- D8706PT1LNR0
- 117456  
	- D8706PT2LJE0
  
Relay MOT: 0651R22CXGAXAE1112B302
New MOT: 0651R22CXGAXAE1112M702
  
- Maggie Nevrly  
- Kurt Blomquist  
  

Customer Questions:
- Tie behavior after closing:
	- Should it be able to auto open?
	- Sectionalize/Reclose/1-trip protection?
- What are your reset times for substation reclosers?
	- Reclosers should have the same reset times

Notes:
- Manual operations kick out of auto
- If there's a yellow handle signal, it holds the auto latch in reset
- HLT trips when the specified elements time out
- When closing into a fault after an auto open, switch will trip if current exceeds 51 pickup value
- Remote mode does not block local PB commands (that is for PB lock to do)
- We will ignore/disable inrush, but can mention it in case customer needs it
- If we have LOV on CB3 and system reconfigures, but then there's a fault on G, both sectionalizers would see fault current, but SEC 2 would lock out before SEC 1 or REC 2
	- would need another settings group to account - could be dependent on directional current
- Reclose NOT supervised by healthy batt
- trip PB is not blocked by PB lock - for safety
- Can only activate reclosing and fast curve if sectionalizing is disabled
	- Ground can be activated so it can still be used in HLT for a sectionalizer
- Alternate profile only does reclosing
	- Sectionalizing set to 0 in template
	- Hardcode loop scheme latch to 0
- Blocking LS auto close timer if recloser is in 79 cycle (79CY3P)
- Applicable to all LOV timers - when does this time start? Is it upon 3 phase LOV, or is it upon losing at least 1 phase (which could happen upon initial fault before the recloser opens - ie voltage sag due to high fault current - also think about how this timer reacts for a system that might reclosers single phase but lockout 3 phase incase they would like to move to that method of operation).
- Applicable to all LOV timers - when does this time start? Is it upon 3 phase LOV, or is it upon losing at least 1 phase (which could happen upon initial fault before the recloser opens - ie voltage sag due to high fault current - also think about how this timer reacts for a system that might reclosers single phase but lockout 3 phase incase they would like to move to that method of operation)
	- The current logic looks at each phase individually for dead voltage on both sides, 52A, and no overcurrent pickup exceeded. In the case of single phase reclosing but 3 phase lockout, we would have to ensure that the LOV trip time is greater than the time between each shot, or maybe we can add blocking, so if phase is in 79 cycle mode, timer will deassert.

Nic Question:
- For Fault on A:
	- Will want to review this closely with them. At this point if the tie and recloser are too close to coordinate they will both trip … if the tie is in the reset state it should recloser back in an hold … just a matter of curve coordination and settings timing coordination (which right now with a 15s auto close and 60s reset from lockout they would not coordinate).


EXTRA TESTING:
- Section 3, 2. Permanent Fault on Line Segment C … _l. Verify that TIE 1 does not close_

- 2.5 sec minimum for reclose timers for DER's - due to standard requiring DER's trip after 2sec LOV
- Concerned with long recloser timer (45s) - this will push out the restore timing

CIRCUIT AUTOMATION SETTINGS:
- Pine River - 34500V (19920V L-G)
	- Circuit 1
		- RECLOSER - R1-Akeley 88
		- TIE - Tie 509-543 NO
		- SECTIONALIZER - R2 Ten Mile Lake 88
		- RECLOSER - R1-Hackensack 88
	- Circuit 2
		- RECLOSER - R1-Backus 77
		- TIE - Tie 516-550 NO
- West Cohasset - 23000V (13280V L-G)
	- RECLOSER - R1-Stevens Lake 77
	- TIE - Boswell 88
	- RECLOSER - R1-Foxtail 88
	- RECLOSER - R1-Boswell 99
- Long Prairie - 34500V (19920V L-G)
	- Circuit 1
		- TIE - TIE 501-517 NO
		- RECLOSER - R1-Long Prairie Rural North
	- Circuit 2
		- 75s Auto Open
		- 90s Auto Close

Follow Up-items:
- 300 cycles event report length was requested, but longest available is 180 cycles

LOGIC (recloser):
- Auto mode:
	- SET32 := ((PB04_PUL AND LT05) OR (R_TRIG RB09 AND LT03)) AND LT06 AND NOT LT32 # LOOP SCHEME ENABLED
	- RST32 := (((PB04_PUL AND LT05) OR (R_TRIG RB10 AND LT03)) AND LT32) OR NOT LT06 OR (TRIP3P AND SV64T AND MV25 = 0.00) OR SV55 OR (SV64T AND MV24 = 0 AND NOT 52A3P)
		- PB or Remote Open
		- HLT
		- Trip signal and LOV trip and Auto close disabled
		- LOV trip and it's a directional switch and it's open
		- SV55 := (79LO3P AND (SV26 OR 51P OR 51G1) AND TRIP3P) OR (52A3P AND SV56T AND MV26 = 0.00) # EXTRA EQUATION FOR LOOP SCHEME RESET
			- Lockout and fault indication or fault active and trip signal active
			- Closed and it just auto closed and auto open is disabled

ADDED LOGIC SINCE FAT:
- Hardcoded alt settings and fast curve to 0
- Added logic for shortened auto close timing if device opened due to LOV
- HLT now trips to lockout upon current exceeding pickup level, rather than waiting to time out
	- Had to add an extra variable for this
- if a device is directional, when it opens, it will be kicked out of auto
	- Keeping it on ties as well, even though there may be edge cases where we would want to restore, but it won't be in auto
		- Doing this to air on the side of safety and consistency across devices
	- Edge case where kicking all directional devices out of auto can be undesirable:
		- Fault on F - Tie 2 will not operate and will sit there still in auto
		- If we lose source CB1, Tie 1 will close to restore B, but if we then subsequently lose source CB3, when TIE1 opens due to LOV, it will be kicked out of auto, so it won't close back in to restore B from source CB2
- ==Added kicking out of auto upon manual operation (pb press or remote) or upon yellow handle execution
	- yellow handle signal will hold auto mode in reset
- Fixed logic so reclosing re-enables after disabling HLT if it was initially on, but doesn't enable if it was initially off


NOTE:
- The extra logic we added for the shortened auto close timers was probably unnecessary given the current use case of the devices. Reclosers/Sectionalizers will always only be timing to close after they've opened due to LOV (so longer timer will never be used) and Ties shouldn't really ever be using the shorter timer. We just needed to think about the logic of deciding the times of each device differently
	- Will keep this logic for MP for now, as it distinguishes two different times, even though only one will be used at a time
- TO REMOVE:
	- remove SV54
		- remove SV54 from CL3P, ULCL3P, SV56
	- remove LT26
	- remove from template