  
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\121288 - Minnesota Power Co>)  

IP:
- relays: 192.168.1.5-8
- RTAC: 192.168.1.2

Voltage Ratio - 10000:1
CT Ratio - 1000:1

System Voltage - 19.92kV
Live - 15.936kV
Under - 11.952kV
Dead - 2.988kV


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
  
- Maggie Nevrly  
- Kurt Blomquist  
  
To Do:
- Fix DNP map order
- based on provided breaker reclosing settings, make suggestions and have discussion on proper LOV timings
- add a section for customer settings in FAT doc
- double check programming spec based on changes

Customer Questions:
- Tie behavior after closing:
	- Should it be able to auto open?
	- Sectionalize/Reclose/1-trip protection?
- Added alternate settings PB
	- Alternate settings are ONLY for reclosing (loop scheme will be disabled)
- Made changes to DNP map
	- Added settings group, alternate settings activation, and voltage angles
- Changed placement of target LED's
	- Saw that the colors were not configurable, had to move a bit
- Changed default settings
- Subsequent faults will only be tested after system has finished initial reconfiguration
- Directional Ties
	- Should TIE 2 be directional? (is there load on F)
	- Disable REC 1 auto closing to feed A?
	- Disable REC 2 auto closing to feed G?

Notes:
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
- Blocking LS auto close if recloser is in 79 cycle (79CY3P)
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


- WHAT SHOULD DICTATE PROPER RECLOSE FROM LOCKOUT TIMES??

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

