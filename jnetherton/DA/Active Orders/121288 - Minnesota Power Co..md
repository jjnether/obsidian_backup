  
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\121288 - Minnesota Power Co>)  
  
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
	- Sectionalize/Reclose/1-shot protection?
- Load between device and substation?
	- If not, should disable backfeeding toward source in template

Nic Questions:
- Double check logic for kicking TIE/SEC out of LS when closing
	- TIE/SEC drop out of auto on LS close if LOV open and sectionalizing is disabled
- When TIE closes, how could I add reclosing/protection functionality as an option?
	- maybe template setting for protection enable when tie is closed and another setting for enabling reclosing when tie closes
	- should ground be enabled for TIE/SEC if we enable protection? - currently hardcoded to 0
	- if we allow reclosing to be enabled, how to handle fast curve?
- what is low/middle/high word (fault time/date stamp)? - they're in dnp map
- easiest way to hide group 2 template settings?
- How to simulate something closing into a fault? - maybe sequencer?
- cold load/inrush?
- I assume I need to add all the template settings to programming spec?
	- do reclosing settings need to be in programming spec? - there's some I didn't include
- Should there be permissives for putting devices in LS? (i.e. sectionalizer will only enter LS if it's closed, and tie if it's open - when would a recloser?)
- ???We might want to check with Erich and/or Bob on events they have seen. During reclosing depending on logic I'm not sure if the Tie will see voltage re-established to restated it's auto close timer. If not the auto close timer might need to be extended longer than the reclosers total reclose cycle.
- Ground trip and fast curve were hardcoded in Bob's program - I assume it's fine to let them be handled normally?
- Bob's program had high current alarm logic (50p4/50g4) - just an alarm when pickup is exceeded. Should this stay?
	- 50p2 is high current trip

Notes:  
- For sectionalizer, reclose will be permanently off, but label will still be there for consistency
- Remote mode does not block local PB commands (that is for PB lock to do)
- No single phase operations
	- Won't use the extra logic for blocking closes into faults - requires single phase operation
- Will just stagger close timings for ties, no directional tie (in case there's a scenario where we lose both other sources)  
- We will ignore/disable inrush, but can mention it in case customer needs it
- HLT trips when the specified elements time out
- If we have LOV on CB3 and system reconfigures, but then there's a fault on G, both sectionalizers would see fault current, but SEC 2 would lock out before SEC 1 or REC 2
	- would need another settings group to account - could be dependent on directional current
- In prior test that have had the recloser this step would including inject primary current. Since you only have the control you will have to string the current between controls and use an output for feedback to the test set to indicate when the current should stop.
	- Check how many 651's have the extra IO card needed for the output contacts we'll use for voltage/current simulation
- When closing into a fault after an auto open, switch will trip if current exceeds 51 pickup value
- Reclose NOT supervised by healthy batt
- trip PB is not blocked by PB lock - for safety
- No normal/alternate profile
- Removed high current alarm (50p4/50g4) - was added by bob and only went to scada


For Fault on A:  
- Will want to review this closely with them. At this point if the tie and recloser are too close to coordinate they will both trip … if the tie is in the reset state it should recloser back in an hold … just a matter of curve coordination and settings timing coordination (which right now with a 15s auto close and 60s reset from lockout they would not coordinate).  
For Fault on G:  
- They seem fair enough away but ties need to coordinate with REC so that only 1 trips … if not and they both trip one of the SEC will open ...
  
  
# Recloser
SV14T OR OC3 AND LT03 OR 81D1T OR SV58 OR 51PT OR 50P2T OR (51G1T OR 50G2T) AND NOT (SPE AND SV26T) # 3-PHASE TRIP CONDITIONS

R_TRIG SV22T AND MV17 <> 0.00 OR R_TRIG SV04T OR R_TRIG SV40T OR SV23 OR SV25 OR NOT LT06 AND SV35T AND (TRIPA OR TRIPB OR TRIPC) OR SV64T # MORE 3-PH TRIP CONDITIONS

RST32 := (((PB04_PUL AND LT05) OR (R_TRIG RB14 AND LT03)) AND LT32) OR NOT LT06 OR (TRIP3P AND SV64T AND MV25 = 0.00) OR SV55
SV55 := (79LO3P AND (SV26 OR 51P OR 51G1) AND TRIP3P) OR (52A3P AND SV56T AND MV26 = 0.00) # EXTRA EQUATION FOR LOOP SCHEME RESET
# Sectionalizer
SV14T OR OC3 AND LT03 OR 81D1T OR SV58 OR (51PT OR 50P2T OR 51G1T OR 50G2T) AND NOT LT06 # 3-PHASE TRIP CONDITIONS

R_TRIG SV22T AND MV17 <> 0.00 OR R_TRIG SV04T OR R_TRIG SV40T OR SV23 OR SV25 OR NOT LT06 AND SV35T AND (TRIPA OR TRIPB OR TRIPC) OR SV64T OR (SC02QU AND LT27) # MORE 3-PH TRIP CONDITIONS
- YELLOW HANDLE PULLED AND ENABLE 3 PHASE TRIP FROM YELLOW HANDLE (TEMPLATE)
- PHASE DISCORDANCE
- 3-PH OPERATOR TRIP FOR LOCKOUT MODE
- 3-PH TRIP AND DTL LOGIC FOR LO MODE 2-3

RST32 := (((PB04_PUL AND LT05) OR (R_TRIG RB14 AND LT03)) AND LT32) OR NOT LT06 OR (TRIP3P AND SV64T AND MV25 = 0.00) OR SV55
SV55 := (79LO3P AND (SV26 OR 51P OR 51G1) AND TRIP3P) OR ==(52A3P AND SV56T AND MV26 = 0.00 AND MV23 = 0.00)== OR (SC02QU AND LT27) # EXTRA EQUATION FOR LOOP SCHEME RESET
- LOV close command and LS auto close is disabled and sectionalizing is disabled

# Tie
SV14T OR OC3 AND LT03 OR 81D1T OR SV58 OR (51PT OR 50P2T OR 51G1T OR 50G2T) AND NOT LT06 OR ==SV36== # 3-PHASE TRIP CONDITIONS

SV36 := (51PT OR 50P2T OR (51G1T OR 50G2T) AND NOT (SPE AND SV26T)) AND MV28 = 1.00 AND MV23 = 0.00
- (overcurrent settings) and protection enabled and sectionalizing disabled
- remove option to turn off sectionalizing

(PB02_PUL AND LT05 OR RB04 AND LT03 OR ==(52A3P AND SV56T AND MV28 = 1.00 AND MV29 = 1.00 AND MV23 = 0.00)==) AND NOT LT02 AND LT06 OR R_TRIG LT06 # RECLOSE ENABLED
- LOV close command and protection enabled and reclosing enabled and sectionalizing disabled
(PB02_PUL AND LT05 OR RB04 AND LT03) AND LT02 OR NOT LT06 OR SV02 # LAST TERM IS "RECLOSING RELAY DEFEATED"


- IF SECTIONALIZING IS ENABLED, IT DISABLES RECLOSING
	- IF SECTIONALIZING IS NOT ENABLED, IT ALLOWS YOU TO ENABLE RECLOSING
- make sure when it opens due to HLT or L