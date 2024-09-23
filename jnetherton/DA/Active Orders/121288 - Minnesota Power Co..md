  
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
- Check changes made between revs - might need to port some over to sectionalizer logic  
- Fix DNP map order  
- Double check all PB and RB assignments  
- Double check alternate settings (Bob's had a comment that SG2 not used in FLISR configuration, not sure what this means?)  
- We might want to check with Erich and/or Bob on events they have seen. During reclosing depending on logic I'm not sure if the Tie will see voltage re-established to restated it's auto close timer. If not the auto close timer might need to be extended longer than the reclosers total reclose cycle.  
- No normal/alternate profile - check in logic/DNP maps  
- what is low/middle/high word?  
- yellow handle display point, remove PB
	- double check all yellow handle logic
- based on provided breaker reclosing settings, make suggestions and have discussion on proper LOV timings 
- Will I be making a custom program for each device?  
- How to simulate something closing into a fault?  
	- Maybe sequencer?
- Double check tie closing in and acting as sectionalizer logic
- When tie closes

Customer Questions:
- Should ties drop out of auto when closing?  
	- depends on if ties should be able to auto open - will have to ask customer - for now will assume no auto open
		- Actually, lets use auto open - doesn't hurt anything and will let system react to more possible scenarios
	- will have recloser/sectionalizer protection regardless 
	- update programming spec based on this
	- How many shots should TIE have? Bob mentioned they are often just 1 shot?
- Is there any load on line between Tie and substation?
	- If not, will make the tie directional so that it doesn't ever backfeed the substation
- Check conditions for going into loop scheme

Notes:  
- For sectionalizer, reclose will be permanently off, but label will still be there for consistency  
- Remote mode does not block local PB commands (that is for PB lock to do)  
- No single phase operations  
- Won't use the extra logic for blocking closes into faults because we're doing all 3 phase operations  
- Will add a section for customer settings in FAT doc later  
- usually with a tie up against substation breaker, you want it to be directional and not close to backfeed sub  
	- Need to ask customer if there is load on that segment of the line  
- Will just stagger close timings for ties, no directional tie (in case there's a scenario where we lose both other sources )  
- We will ignore/disable inrush, but can mention it in case customer needs it
- HLT trips immediately upon exceeding any pickup
	- REMOVE REDUNDANT LOGIC IN TR3P
- If we have LOV on CB3 and system reconfigures, but then there's a fault on G, both sectionalizers would see fault current, but SEC 2 would lock out before SEC 1 or REC 2
	- would need another settings group to account - could be dependent on directional current
- In prior test that have had the recloser this step would including inject primary current. Since you only have the control you will have to string the current between controls and use an output for feedback to the test set to indicate when the current should stop.
	- Check how many 651's have the extra IO card needed for the output contacts we'll use for voltage/current simulation
- When closing into a fault after an auto open, switch will trip if current exceeds 51 pickup value
- Reclose NOT supervised by healthy batt
- trip PB is not blocked by PB lock - for safety
  
For Fault on A:  
- Will want to review this closely with them. At this point if the tie and recloser are too close to coordinate they will both trip … if the tie is in the reset state it should recloser back in an hold … just a matter of curve coordination and settings timing coordination (which right now with a 15s auto close and 60s reset from lockout they would not coordinate).  
For Fault on G:  
- They seem fair enough away but ties need to coordinate with REC so that only 1 trips … if not and they both trip one of the SEC will open ...  
  
  
Tie  
- After it closes and holds it would act like a traditional recloser (only operating for faults no LOV)  
  
- 50P4TC  
- `LB01 # MAINT MODE`  
- LT28 - NA  
- SV09  
- `PB01_PUL # MANUAL BATTERY TEST`  
- SV18 - 0  
- `0 # LOCAL/REMOTE MASTER`  
- SC03 - set to 1, NA  
- ELB - 1  
- TLED4  
- `LB01 # MAINT MODE`  
- PB1 - GO, RO  
- `0 # NOT IN303 #BATT OKAY`  
- `0 # IN303 #BATT FAIL`  
- DP19  
- `LB01,,"MAINTENANCE MODE"`  
- LB01  
- `MAINT. MODE`  
- `DISABLE`  
- `ENABLE`  
- `0`