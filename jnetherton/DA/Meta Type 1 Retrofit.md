Default Programs - X:\DA\Dept\_Lazer\_Facebook - All Sales Orders\00 - Current Program & Documentation\1 - Motorized Design
Retrofit Folder - \\gwfs04.loc.gwelec.com\New-Dept\DA\Dept\_Lazer\_Facebook - All Sales Orders\Prot. Settings Updates and MM Updates_
My Retrofit Folder - C:\Users\jnetherton\Downloads\Meta\Retrofit

Rev. 1.3 - JN - 03/07/24
- Changes made per project DCI 1434
- Added ERMS status to MODBUS map


RTAC:
- Update Project Name (eg. CCO1_Non-Motorized_ERMS_MVS-1X1_Rev1.2_03-07-24_R143)
- Enable LB01 and LT28 metering under both relays in RTAC, but ensure the rest of the local bits are disabled
- Add registers to every modbus map for each way
	- Ensure the registers match what's in the spec:
	- ![[Pasted image 20240116160652.png|500]]

	- HREG_00078_W3_ERMS_ENABLED
	- HREG_00079_W4_ERMS_ENABLED
	- ![[Pasted image 20240119113213.png|500]]


- Add lines to the tag processor, converting the LB01 status from each relay to a modbus output (OR it also with LT28 status)
	- HREG_00078_W3_ERMS_ENABLED.status.stVal
	- BOOL_TO_INT(MVS1_W1_SEL.FM_INST_LB01.stVal OR MVS1_W1_SEL.FM_INST_LT28.stVal)
	- HREG_00079_W4_ERMS_ENABLED.status.stVal
	- BOOL_TO_INT(MVS1_W2_SEL.FM_INST_LB01.stVal OR MVS1_W2_SEL.FM_INST_LT28.stVal)
	- ![[Pasted image 20240119113306.png|850]]

**For Local Bit Implementation:**
- Check Relay for Maintenance Mode Logic (LB01)
	- LB01 in 50P4TC and 50P4 values entered
		- LB01 # MAINTENANCE MODE OVERCURRENT SETTINGS
	- Add 50P4P into trip unlatch equation (add other 50/51 elements if needed)
	- Enable 1 local bit
	- Add LB01 to T04 Target LED
		- N
		- R
		- LB01 # MAINTENANCE MODE
	- Add Display Point
		- LB01,,"MAINTENANCE MODE"
	- Add LB01 labelling
		 ![[Pasted image 20231130110708.png|300]]
	- Add to SER Trigger List
		- 50P4P,50P4T,LB01
	- Add to Event Report Trigger
		- R_TRIG 50P4P OR R_TRIG 50P4T


**For Pushbutton Implementation:**
- Check Relay for Maintenance Mode Logic (LT28)
	- Update Protection Settings
	- LT28 in 50P4TC and 50P4 values entered
		- LT28 # MAINTENANCE MODE OVERCURRENT SETTINGS
	- Ensure TRIP equation has 50P4T (or ORED50T)
	- Add 50P4P into trip unlatch equation
	- Edit LT28
		- SET28 := NOT LT28 AND R_TRIG PB01_PUL # ERMS ON
		- RST28 := LT28 AND R_TRIG PB01_PUL # ERMS OFF
	- Disable manual battery test
		- SV09 := 0 # MANUAL BATTERY TEST
	- Add IN303 to T04 Target LED
		- T04LEDL := N
		- T04LEDC := R
		- T04_LED := IN303 # BATT FAIL
	- Edit PB1 LED's
		- PB1ALEDC := RO
		- PB1A_LED := LT28 # ERMS ON
		- PB1BLEDC := GO
		- PB1B_LED := NOT LT28 # ERMS OFF
	- Add Display Point
		- LT28,,"MAINTENANCE MODE"
	- Add to SER Trigger List
		- 50P4P,50P4T,LT28
	- Add to Event Report Trigger
		- R_TRIG 50P4P OR R_TRIG 50P4T

### If using PB safety timer:
- Edit LT28
	- SET28 := NOT LT28 AND R_TRIG SC03QU # ERMS ON
	- RST28 := LT28 AND R_TRIG SC03QU # ERMS OFF
- Check SV18
	- SV18PU := .05
	- SV18DO := .05
	- SV18 := NOT SV18T # PUSHBUTTON SAFETY TIMER
- Check SC03
	- SC03PV := 3
	- SC03R := NOT PB01
	- SC03CU := PB01 AND SV18T

### For 6-way switch (ways 5-6):
**For Pushbutton Implementation:**
- Check Relay for Maintenance Mode Logic (LT28)
	- Update Protection Settings
	- LT28 in 50P4TC and 50P4 values entered
		- LT28 # MAINTENANCE MODE OVERCURRENT SETTINGS
	- Ensure TRIP equation has 50P4T (or ORED50T)
	- Add 50P4P into trip unlatch equation
	- Move LT27/LT28 to LT17/LT19
		- **SWAP BASED ON WAY 5 OR WAY 6**
			- SET17 := 1 # 751-3 RELAY IDENTIFIER
			- RST17 := 0
			- SET19 := 0 # 751-4 RELAY IDENTIFIER
			- RST19 := 1

		- SET27 := 0
		- RST27 := 1
	- Edit LT28
		- SET28 := NOT LT28 AND R_TRIG PB01_PUL # ERMS ON
		- RST28 := LT28 AND R_TRIG PB01_PUL # ERMS OFF
	- Disable manual battery test
		- SV09 := 0 # MANUAL BATTERY TEST
	- Add IN303 to T04 Target LED
		- T04LEDL := N
		- T04LEDC := R
		- T04_LED := IN303 # BATT FAIL
	- Edit PB1 LED's
		- PB1ALEDC := RO
		- PB1A_LED := LT28 # ERMS ON
		- PB1BLEDC := GO
		- PB1B_LED := NOT LT28 # ERMS OFF
	- Add Display Point
		- LT28,,"MAINTENANCE MODE"
	- Add to SER Trigger List
		- 50P4P,50P4T,LT28
	- Add to Event Report Trigger
		- R_TRIG 50P4P OR R_TRIG 50P4T