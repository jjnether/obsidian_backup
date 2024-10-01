  
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
- Do you want HLT to trip instantaneously upon exceeding the pickup, or to trip upon the element timing out?
	- I misspoke in the programming spec - typically HLT trips upon the element timing out
- Make customer aware that when they enable auto-close, they should pay attention to coordinating timings so that there aren't paralleled sources on a temporary fault (a switch closes due to LS, then the recloser recloses and parallels them)
- Added alternate settings PB
	- Alternate settings are ONLY for reclosing (loop scheme will be disabled)

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
- Can only activate reclosing, ground, and fast curve if sectionalizing is disabled
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
- LOV close command and LS auto open is disabled and sectionalizing is disabled
# Tie
SV14T OR OC3 AND LT03 OR 81D1T OR SV58 OR (51PT OR 50P2T OR 51G1T OR 50G2T) AND NOT LT06 OR ==SV36== # 3-PHASE TRIP CONDITIONS

SV36 := (51PT OR 50P2T OR (51G1T OR 50G2T) AND NOT (SPE AND SV26T)) AND MV23 = 0.00
- (overcurrent settings) and sectionalizing disabled

((PB02_PUL AND LT05 OR RB03 AND LT03) AND NOT LT02 AND LT06 OR R_TRIG LT06) AND MV23 = 0.00 # RECLOSE ENABLED
(PB02_PUL AND LT05 OR RB04 AND LT03) AND LT02 OR NOT LT06 OR MV23 = 1.00 OR SV02 # LAST TERM IS "RECLOSING RELAY DEFEATED"

(PB05_PUL AND LT05 OR RB05 AND LT03) AND MV23 = 0.00 AND NOT LT04 # FAST CURVE ENABLE
(PB05_PUL AND LT05 OR RB06 AND LT03 OR MV23 = 1.00) AND LT04 # FAST CURVE DISABLE

PWR_SRC1 # SUPPLY
SV39 # BATTERY PROBLEM
PHASE_A # A FAULT ----
PHASE_B # B FAULT ----
PHASE_C # C FAULT ----
50G6 OR 51G1 # GROUND ----
LT17 # INST OC ALARM INDICATION
51G1S AND 51G1T OR 51PS AND 51PT OR 51AS AND 51AT OR 51BS AND 51BT OR 51CS AND 51CT # DELAY CURVE ----
50P2T OR 50G2T OR 50A2T OR 50B2T OR 50C2T # HIGH CURRENT ----
81D1T # FREQUENCY ----
LT07 # PHASE DISCORDANCE TRIP
LT08 #  SINGLE-PHASE TRIP FAILURE
79RS3P OR 79RSA AND 79RSB AND 79RSC # 79 RESET
79CY3P OR 79CYA OR 79CYB OR 79CYC # 79 CYCLE
79LOA OR 79LO3P # A-PHASE LOCKOUT
79LOB OR 79LO3P # B-PHASE LOCKOUT
79LOC OR 79LO3P # C-PHASE LOCKOUT
51P OR 51G1 OR SV26 # ABOVE MIN TRIP
LT10 OR LT11 OR LT12 # PHASE COLD LOAD ACTIVATED
LT13 # GROUND COLD LOAD ACTIVE
NOT SPOA
NOT SPOB
NOT SPOC
SPE