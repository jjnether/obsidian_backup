
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\121288 - Minnesota Power Co>)

- Maggie Nevrly
- Kurt Blomquist
- Use in-house controls
- Virtual FAT?

Programming Spec by middle of August

- after reconfiguration, does it ever go back to normal state?
- sel tie logic having to do with voltage?

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
- Add to template time to look for a trip after closing due to healthy voltage?
- Tie acts as a recloser or sectionalizer after it's been closed?
- So the tie auto close time is a 30s delay ...in this example?  
	- We might want to check with Erich and/or Bob on events they have seen. During reclosing depending on logic I'm not sure if the Tie will see voltage re-established to restated it's auto close timer. If not the auto close timer might need to be extened longer than the reclosers total reclose cycle.

Sectionalizer
- LOV
	- Upstream device tripped for upstream fault
- FC
	- Downstream fault 
- LOV + FC
	- Upstream device tripped for downstream fault