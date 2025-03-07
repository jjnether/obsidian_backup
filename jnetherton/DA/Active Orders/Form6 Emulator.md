
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\Products\FORM 6 EMULATOR>)

119407 - Clearwater Polk Elec
- Skim tested and shipped
118682 - PRAIRIE LAND ELECT COOP (Border States)
- Pick Date - 2/20 and 3/20 (single unit)
120518 - United Cooperative Services
- Pick Date - 3-12

- 0651R229XGG8AE1113WWWW
- 651R#CLAX

Problems between program and documentation
- A,B,C select PB's aren't all active when in 1ph trip-3ph lockout mode (documentation says they should be)
	- In this mode, you can also only close one phase at a time (documentation says this should only happen when in 1ph trip-1ph lockout)

72513 - midwest - GWI - 32 pin template


Changed:
- Added logic so all 3 phases are always selected when in single ph enable - 3 ph trip mode
- LT5 (previously PB lock when low) removed from CL3P and ULCL equations

To add?
- Alt profile #2, alt profile #3? - we have 3 spare PB's
- no close circuit disable fuse to remove
- only one function changed per change mode activation?
- Add phase/gnd cold load pickup display points for indication?


Operation:
- On our 32-pin template, if in operating mode 2 (1ph lockout, but 3ph lockout for multiph fault) or 3 (3ph lockout), 


to test:
- lockout modes
- pushbutton double press modes

Questions
- 3ph-drive to lockout conditions - goes to lockout on SV14T and MV<>18 (trip PB timeout and operating mode 2 or 3)
	- Do we want to drive all 3 phases to lockout when in mode 2? (1ph lockout unless multi-ph fault)
		- no, when in mode 2, user should be able to select which phase to control
- Why did we add the whole phase selector thing? - is this in the form6?
- Should we define a default DNP map? Maybe just use what we have for the 32-pin template?
- Can't close when in 1ph trip - 3ph lockout????
- We ok with keeping functionality where when in 1ph lockout mode, user can only close 1 phase at a time?
	- If so, maybe only allow 1ph to be selected at a time when in this mode (selecting b phase will reset the other 2)



Test Plan:
- Do a compare with the 32-pin template and test any changed functionality
- test basic but frequently used functions



1ph trip - 1ph lockout
- When 3 phases are open, whether 1, 2, or 3 phases are selected, can still hit open PB and it will time (I don't think should be able to do this)
- Can't ever close anything
1ph trip - 1ph lockout (3ph on multi-ph fault)
- all same
1ph trip - 3ph lockout
- all same
3ph trip
- cannot deselect phases - we want this
- can still hit open and start the timer


One of these needs to be high for it to close:
- (LT05 OR CLOSE3P OR CC3 AND LT03 OR 79CY3P) 