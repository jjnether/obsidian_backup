
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\121288 - Minnesota Power Co>)

- Maggie Nevrly
- Kurt Blomquist
- Use in-house controls
- Virtual FAT?

Programming Spec by middle of August

potentially end of October for commissioning

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
- Regarding Directional Ties, customer could instead choose to coordinate with different tie timings
- For sectionalizer, reclose will be permanently off, but label will still be there for consistency
- No normal/alternate profile - check in logic/DNP maps
- I assume after tie closes, it's identical to recloser logic in every way including auto open/auto close?
- what is low/middle/high word?
- single phase reclosing can be enabled, but lockout will always be 3-phase
- Can sectionalizer also operate with single phase reclosers? (open single phases?)
- yellow handle display point, remove PB



Recloser

Sectionalizer
- LOV
	- Upstream device tripped for upstream fault
- FC
	- Downstream fault 
- LOV + FC
	- Upstream device tripped for downstream fault

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

fix tie trip to lockout exit loop scheme