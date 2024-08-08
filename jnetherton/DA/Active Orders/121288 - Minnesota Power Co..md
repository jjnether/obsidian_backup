
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

Sectionalizer
- LOV
	- Upstream device tripped for upstream fault
- FC
	- Downstream fault 
- LOV + FC
	- Upstream device tripped for downstream fault