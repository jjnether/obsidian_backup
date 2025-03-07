
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
- Removed `NOT (CLOSEA OR (CC3 OR CCA) AND LT03 OR 79CYA)` term from all ULCL equations
- Changed single-ph close equations so user can close all 3 phases when in 1ph trip-3ph lockout mode
- Changed TR3P equation so a PB press open only opens all 3 phases if in 3ph lockout or 3ph trip mode
- Removed MV18 (operating mode) supervisory from SV42 (PB trip conditions)
- Changed 79DTL3P so it does 3ph lockout upon pushbutton trip only in 3ph lockout or 3ph trip mode
- Added to 79DTLA/B/C so it locks out upon PB press and the respective phase selected
- Added SV19 for indicating 3ph trip, 3ph LO, or 1ph selected on panel
	- Added SV19 to LT21 (close PB latch)
- Added SV44 and SV45 variables for indicating if selected ph is closed or open (supervises PB close/open latches)
	- Added SV44 and SV45 to LT21 and LT22 (open/close PB latches)
- Added LT06 (HLT) to LT21 (close PB latch) so latch won't set when HLT is enabled

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
- Should we define a default DNP map? Maybe just use what we have for the 32-pin template?
- We ok with keeping functionality where when in 1ph lockout mode, user can only close 1 phase at a time?
	- If so, maybe only allow 1ph to be selected at a time when in this mode (selecting b phase will reset the other 2)
	- What about opens? - it said multiple phases could be selected for opening in 1ph-lockout mode
	- if tripping just one phase, only that phase should lockout, right?
- After opening one or two phase, when opening another phase, the fault indication comes on for that phase
- Lockout is enabled for a bit on all 3 phases when just opening one phase


Test Plan:
- Do a compare with the 32-pin template and test any changed functionality
- test basic but frequently used functions


One of these needs to be high for it to close:
- (LT05 OR CLOSE3P OR CC3 AND LT03 OR 79CY3P) 


LT21 AND NOT IN102 AND NOT SV13T AND NOT SV21 AND NOT SV14 AND LT06 # CLOSE PUSHBUTTON DELAY
(PB11_PUL AND NOT SV13 OR NOT PB11_PUL AND SV13) AND NOT PB12_PUL AND NOT SV13T AND NOT SV21 AND NOT SV14 AND LT05 AND LT06 # CLOSE PUSHBUTTON DELAY


1ph trip - 1ph lockout


1ph trip - 1ph lockout (3ph lockout for multi-ph fault)


1ph trip - 3ph lockout


3ph trip



(PB02_PUL AND LT05 OR RB03 AND LT03) AND NOT LT02 AND LT06 OR R_TRIG LT06 # RECLOSE ENABLED

((PB02_PUL AND LT05 OR RB03 AND LT03) AND NOT LT02 AND LT06) AND MV23 = 0.00 # RECLOSE ENABLED




MEETING NOTES:
- Differences:
	- HLT - initiate trip based on HLT activating - should not cause a trip
- Blinking
- implified setup