  
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\121288 - Minnesota Power Co>)  

IP:
- relays: 192.168.1.5...8
- RTAC: 192.168.1.2

Voltage Ratio - 10000:1
CT Ratio - 1000:1

Settings:
- Open loss of voltage timer should be longer than longest reclose events (10 seconds for slack accounting for curves)
- Close due to LOV maybe 10s longer than open from LOV
- Sectionalizer reset should match the upstream recloser reset timer

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
	- LOV open?
	- Sectionalize/Reclose/1-trip protection?
- Load between device and substation?
	- If not, should disable back-feeding toward source in template
- I misspoke in the programming spec - typically HLT trips upon the element timing out
- Make customer aware that when they enable auto-close, they should pay attention to coordinating timings so that there aren't paralleled sources on a temporary fault (a switch closes due to LS, then the recloser recloses and parallels them)
- Added alternate settings PB
	- Alternate settings are ONLY for reclosing (loop scheme will be disabled)
- Made changes to DNP map
	- Added settings group, alternate settings activation, and voltage angles
- Changed placement of target LED's
	- Saw that the colors were not configurable, had to move a bit
- Changed default settings
- Subsequent faults will only be tested after system has finished initial reconfiguration
- Directional Tie or just coordinate timing? Directional will prevent closing for LOV in the direction we don't want, but we also won't be able to restore anything else from that substation if both others go down

Notes:
- HLT trips when the specified elements time out
- When closing into a fault after an auto open, switch will trip if current exceeds 51 pickup value
- Remote mode does not block local PB commands (that is for PB lock to do)
- We will ignore/disable inrush, but can mention it in case customer needs it
- If we have LOV on CB3 and system reconfigures, but then there's a fault on G, both sectionalizers would see fault current, but SEC 2 would lock out before SEC 1 or REC 2
	- would need another settings group to account - could be dependent on directional current
- Reclose NOT supervised by healthy batt
- trip PB is not blocked by PB lock - for safety
- If sectionalizing is enabled, sets reclosing, ground, and fast curve to 0
- Can only activate reclosing and fast curve if sectionalizing is disabled
	- Ground can be activated so it can still be used in HLT for a sectionalizer
- Alternate profile only does reclosing
	- Sectionalizing set to 0 in template
	- Hardcode loop scheme latch to 0
- Blocking LS auto close if recloser is in 79 cycle (79CY3P)
- Applicable to all LOV timers - when does this time start? Is it upon 3 phase LOV, or is it upon losing at least 1 phase (which could happen upon initial fault before the recloser opens - ie voltage sag due to high fault current - also think about how this timer reacts for a system that might reclosers single phase but lockout 3 phase incase they would like to move to that method of operation).
- If customer wants protection on Tie, they simply add it to the template (protection will be disabled when sectionalizing is enabled)


For Fault on A:  
- Will want to review this closely with them. At this point if the tie and recloser are too close to coordinate they will both trip … if the tie is in the reset state it should recloser back in an hold … just a matter of curve coordination and settings timing coordination (which right now with a 15s auto close and 60s reset from lockout they would not coordinate).  
For Fault on G:  
- They seem fair enough away but ties need to coordinate with REC so that only 1 trips … if not and they both trip one of the SEC will open ...

QUESTIONS:
- Fast curve is tripping 3 times when it should only be 2???
	- It's also ending on fast curve?? - 79SKP3P?

EXTRA TESTING:
- Section 3, 2. Permanent Fault on Line Segment C … _l. Verify that TIE 1 does not close_

- 2.5 sec minimum for reclose timers for DER's - due to standard requiring DER's trip after 2sec LOV
- Concerned with long recloser timer (45s) - this will push out the restore timing