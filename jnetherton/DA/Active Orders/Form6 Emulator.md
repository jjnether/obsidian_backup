
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\Products\FORM 6 EMULATOR>)

119407 - Clearwater Polk Elec
- Skim tested and shipped
118682 - PRAIRIE LAND ELECT COOP (Border States)
- Pick Date - 2/20 and 3/20 (single unit)
120518 - United Cooperative Services
- Pick Date - 3-12

- 0651R229XGG8AE1113WWWW (border states)
- 651R#CLAX
	- dedicated front LED's for open/close/HLT
	- toggle switch for HLT
	- dedicated front PB's for open/close

72513 - midwest - GWI - 32 pin template


Changed:
- Added logic so all 3 phases are always selected when in single ph enable - 3 ph trip mode
- LT5 (previously PB lock when low) removed from CL3P equations
- Removed `NOT (LT05 OR CLOSE3P OR CC3 AND LT03 OR 79CY3P)` term (and all similar) from ULCL equations
	- This term is only used for to allow certain ways to close when PB lock is enabled (LT05=0), but we removed PB lock
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
- Added original open/close LED logic to open/close external LED's
	- Also changed so there is alternate blinking when SPO=1
- Changed A/B/C Fault TLED's to the overcurrent logic from the TRIPA/B/C equations
	- This was because the previous values used were PHASE_A/B/C, but these assert anytime TRIPA/B/C asserts, so they were asserting when opening via PB when in 1ph mode
- Modified Change mode so it resets for each action
- Added functionality so CLPU activates upon PB close if it sees the mechanism close
- Added SV47 and SV48 to add a delay for PB open/close 2nd press (so it doesn't operate on the same processing cycle as the PB press, it should wait until after first press to then operate on a 2nd press)
- Changed all 3 lockout LED's to green to match Form6
- Edited SV21 so the 3-phase terms only assert when in 3-phase mode, and same for single phase
- Moved NOT SV21 from SV13 to LT21 (more upstream on the close logic)
	- Did this because close initiate was latching, but not executing close because SV21 was blocking, then when SV21 deasserted, it closed (not good)


Questions
- Should we define a default DNP map? Maybe just use what we have for the 32-pin template?
- When yellow handle is pulled on one phase, it trips all 3 if in 3ph LO mode, but only trips the one if in 1ph LO mode
	- ==should we add this?==
	- For 32-pin default, 3-ph trip from yellow handle is directly controlled from the template setting
-  If the the control shuts down due to low battery voltage before AC power is restored, and the connected energized recloser is CLOSED, it will only TRIP and LOCKOUT via front panel pushbutton command.
	- can we do this?
- In the event of main microprocessor failure, the trip circuit can operate independent of the main microprocessor
- REVIEW FRONT PANEL
	- Maybe use spare PB's for ALT2/3?

Test Plan:
- Do a compare with the 32-pin template and test any changed functionality
- test basic but frequently used functions

DIFFERENCES:
- No alarm for 52A/B discrepancy (can do with 42-pin, but we only get 52A back with 32-pin)

MEETING NOTES:
- Differences:
	- HLT - initiate trip based on HLT activating - should not cause a trip
- ==Blinking LED's when only one phase open==
- design template should exactly match simplified setup
- copy template settings from one group to another?
- HLT - add definite time delay in ms
- HLT has two separate latches for remote and local
- HLT doesn't have a separate 50, but a distinct time delay for HLT
- repurpose ABC 51 curves for CLPU


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
- Lockout LED is enabled for a bit on all 3 phases when just opening one phase

---
# FUNCTIONALITY

### HOT LINE TAG
- All closing is disabled
- One trip-to-lockout
- Trips out all 3 phases no matter which mode
- Can be activated only from toggle switch
- ==Form6 takes precedence over cold load pickup, non-reclosing, and fast trips disabled
- ==HLT opens all 3 phases independent mode or timing that defines the trip time. If any one phase is already open and HLT is activate the other 2 phases will **NOT**  open.
- ==HLT opens all 3 phases independent mode or timing that defines the trip time. If any one phase is already open and HLT is activate the other 2 phases will immediately open.
- ==specific curve allowed to be programmed for HLT?
- ==form 6 allowed activation from other sources, but only allowed deactivation when all sources are disabled
	- ==may only be reset by the source that set it (if activated at the operator panel, must be deactivated there, and not by SCADA)
- ==Add definite time delay for HLT elements?
- ==HLT will act on whatever is fastest, active curve or time delay
- ==If above ground pickup and below phase, trips all 3 phases on TCC1 or HLT definite time delay?
- ==HLT trips on TCC1 or Time delay whichever is faster. If unit trips on HLT time then all 3 phases operate and lockout. If trip on TCC1 then only phase involved trips and LO
 

### COLD LOAD PICKUP
- Phase and ground CLPU can be enabled in the template
- CLPU doesn't latch until loss of diversity timer times out
	- Aph loss of diversity -> (Aph is in LO, 3ph LO, or reclosing defeated) AND SPOA AND (phase or ground CLPU enabled) (template set pickup)
	- Ground latches if any phase loss of diversity latches and ground CLPU is enabled
	- CLPU latches reset via natural or forced restoration
		- Natural -> current below default TOC minimum trip setting and Aph closed (15sec pickup)
		- Forced -> setting enabled and Aph closed (template set pickup)
- While CLPU is active, fast curves are disabled and puts a blinder on the delay curves (same curve, but won't trip until it exceeds the CLPU pickup)
	- Uses template set mult. of min. trip settings as CLPU pickup
- ==Form6 has many options for CLPU such as minimum trip value time-current curve, reclose interval, and number of independent operations to lockout for each protection profile. Cold Load Pickup also includes TCC Multipliers, TCC Adders, Minimum Response Time, Time Dial Reset, and High Current Lockout. 
- ==Form6 initiates CLPU upon PB close if it's enabled

### OPEN/CLOSE PUSHBUTTONS/LED'S
- When in 3ph LO mode, all 3 phases are always selected
- Any selected phases can be opened via PB
- Only one selected phase can be closed at a time via PB
- Open/close LED's are solid when all three phases in open/close position
- When 1 or 2 phases are opened, open/close LED's blink alternately
- Options in the template for double PB press
	- does nothing
	- executes command immediately
	- cancels command


NOT (3PO OR SPO) AND NOT (SV13 AND SV41T) OR (3PO OR SPO) AND (SPO AND NOT SV13 AND SV01T OR SV13 AND SV41T) # CLOSE LED ON EXTERNAL PANEL
- 3 phases closed and not timing to PB trip (2hz blinking)
- 1/2/3 phases open and timing to PB trip (2hz blinking)
- 1 OR 2 phases open and not timing to PB trip (1hz blinking)


3PO AND NOT (SV14 AND SV41T) OR NOT 3PO AND (SPO AND NOT SV14 AND SV01T OR SV14 AND SV41T) # OPEN LED ON EXTERNAL PANEL
- 3 phases open and not timing to PB trip (2hz blinking)
- 3 phases closed and timing to PB trip (2hz blinking)
- 1 OR 2 phases open and not timing to PB trip (1hz blinking)

50P1P - High current lockout (no trip)
50P2P - High current trip
50P3P - CLPU
50P6P - Minimum trip (same as 51 min. trip), only used for CLPU natural restoration, not used for tripping

50G1P - High current lockout (no trip)
50G2P - High current trip
50G5P - CLPU
50G6P - Minimum trip (same as 51 min. trip), only used for CLPU natural restoration, not used for tripping