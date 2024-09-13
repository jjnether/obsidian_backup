
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\121288 - Minnesota Power Co>)

POD:
- 66402
- 76820
- 107931

- Maggie Nevrly
- Kurt Blomquist

To Do:
- Should I have voltage status on target LED's?
- Is there bloat on target LED's I should get rid of?
- Add battery test PB?
- Should trip PB be blocked by PB lock?
- Double check display point - LOV LS timing to close
- Check changes made between revs - might need to port some over to sectionalizer logic
- Fix DNP map order
- Double check all PB and RB assignments
- Double check alternate settings (Bob's had a comment that SG2 not used in FLISR configuration, not sure what this means?)
- So the tie auto close time is a 30s delay ...in this example?  
	- We might want to check with Erich and/or Bob on events they have seen. During reclosing depending on logic I'm not sure if the Tie will see voltage re-established to restated it's auto close timer. If not the auto close timer might need to be extened longer than the reclosers total reclose cycle.
- No normal/alternate profile - check in logic/DNP maps
- I assume after tie closes, it's identical to recloser logic in every way including auto open/auto close?
- what is low/middle/high word?
- single phase reclosing can be enabled, but lockout will always be 3-phase
- Can sectionalizer also operate with single phase reclosers? (open single phases?)
- yellow handle display point, remove PB
- is trip to lockout after closing a template setting or hardcoded?
- based on provided breaker reclosing settings, make suggestions and have discussion on proper LOV timings


Notes:
- Regarding Directional Ties, customer could instead choose to coordinate with different tie timings
- - For sectionalizer, reclose will be permanently off, but label will still be there for consistency

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



Multi - fault scenario in FAT