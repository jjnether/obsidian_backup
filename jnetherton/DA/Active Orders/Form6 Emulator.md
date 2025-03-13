
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
- Added "NO AC PRESENT" display point

To add?
- no close circuit disable fuse to remove
- only one function changed per change mode activation?
- Add phase/gnd cold load pickup display points for indication?


Operation:
- On our 32-pin template, if in operating mode 2 (1ph lockout, but 3ph lockout for multiph fault) or 3 (3ph lockout), 

Questions
- Should we define a default DNP map? Maybe just use what we have for the 32-pin template?
- We ok with keeping functionality where when in 1ph lockout mode, user can only close 1 phase at a time?
	- If so, maybe only allow 1ph to be selected at a time when in this mode (selecting b phase will reset the other 2)
	- What about opens? - it said multiple phases could be selected for opening in 1ph-lockout mode
	- if tripping just one phase, only that phase should lockout, right?
- After opening one or two phase, when opening another phase, the fault indication comes on for that phase
- Lockout is enabled for a bit on all 3 phases when just opening one phase
- Add original open/close LED logic to open/close external LED's
- Add cold load pickup for when closing via PB and phase is locked out?
- Only one function can be changed per change mode activation?
	- I think this isn't necessary?
- When yellow handle is pulled on one phase, it trips all 3 if 3ph LO, but only trips the one if in 1ph LO
	- should we add this?
- Protection profiles? I assume probably not
-  If the the control shuts down due to low battery voltage before AC power is restored, and the connected energized recloser is CLOSED, it will only TRIP and LOCKOUT via front panel pushbutton command.
	- can we do this?
- Lockout LED (only one) is green on Form6, should we change ours to green? Also, it blinks when in 1ph-1LO mode and 1/2 phases are in lockout, but not all 3. Maybe implement if a phase is locked out, but not all 3 are, the locked out phases blink?
- In the event of main microprocessor failure, the trip circuit can operate independent of the main microprocessor
	- can we do this?
- For HLT, there's a couple different behaviors for F6:
	- HLT opens all 3 phases independent mode or timing that defines the trip time. If any one phase is already open and HLT is activate the other 2 phases will **NOT**  open.
	- HLT opens all 3 phases independent mode or timing that defines the trip time. If any one phase is already open and HLT is activate the other 2 phases will immediately open.
	- specific curve allowed to be programmed for HLT?
	- form 6 allowed activation from other sources, but only allowed deactivation when all sources are disabled
		- may only be reset by the source that set it (if activated at the operator panel, must be deactivated there, and not by SCADA)
	- Add definite time delay for HLT elements?
	- HLT will act on whatever is fastest, active curve or time delay

Test Plan:
- Do a compare with the 32-pin template and test any changed functionality
- test basic but frequently used functions


MEETING NOTES:
- Differences:
	- HLT - initiate trip based on HLT activating - should not cause a trip
- Blinking LED's when only one phase open
- design template should exactly match simplified setup


Missing LED's
- No AC present (add display point)
- RAM failure
- ROM failure
- Power Supply Malf
- RIF Comm Failure
- Alarm
- Above minimum trip

TO CHECK:
- HLT takes precedence over CLPU
- HLT takes precedence 

---
# FUNCTIONALITY

### HOT LINE TAG
- All closing is disabled
- one trip-to-lockout
- takes precedence over cold load pickup, non-reclosing, and fast trips disabled
- can be activated only from toggle switch
	- 



NOT (3PO OR SPO) AND NOT (SV13 AND SV41T) OR (3PO OR SPO) AND (SPO AND NOT SV13 AND SV01T OR SV13 AND SV41T) # CLOSE LED ON EXTERNAL PANEL
- 3 phases closed and not timing to PB trip (2hz blinking)
- 1/2/3 phases open and timing to PB trip (2hz blinking)
- 1 OR 2 phases open and not timing to PB trip (1hz blinking)


3PO AND NOT (SV14 AND SV41T) OR NOT 3PO AND (SPO AND NOT SV14 AND SV01T OR SV14 AND SV41T) # OPEN LED ON EXTERNAL PANEL
- 3 phases open and not timing to PB trip (2hz blinking)
- 3 phases closed and timing to PB trip (2hz blinking)
- 1 OR 2 phases open and not timing to PB trip (1hz blinking)