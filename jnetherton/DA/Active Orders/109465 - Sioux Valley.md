
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\109465 - Sioux Valley Energy (RESCO)>)

Top Level - DM80CLLFFAJ0
Wiring - B13440085DX0
Relay PN - A13413541JH0

NEW - GWI523-664CD
- This GWI will just be left alone, it was decided we'll just update GWI523-370CD
POD - GWI523-370CD

Scope:
Motor operation (NO ATC) for ways 1 and 2 and single phase Overcurrent protection for ways 3 and 4.

CHANGELOG
- Settings Group 1 is the default config
- Settings Group 2 uses single phase tripping
- Added single phase tripping to template
- Edited 3 phase tripping labels in template for consistency
- Updated Breaker Monitors to account for both 3 and single phase tripping
- Removed hanging variables (AMV005 - AMV016)
- Consolidated S3/S4 manual open into PSV58 and PSV59
- Needed more PSV variables
	- Replaced PSV09 (low SF6) with ASV003
	- Removed variables that were only input contacts (PSV11-13, PSV21-23, PSV31-33, PSV41,43) and replaced with respective input contacts
- Added aliases for trips
	- Removed aliases for 51 settings - redundant, and inconsistent based on 3ph or single ph
- Removed close/motor operations on Ways 3/4 for settings group 2
	- When in settings group 2, Ways 3/4 will only do single phase O/C, not close/motor operations
- Added variables for 50 and 51 pickup (AMV017-AMV028)
- Added variables for Fault Target LED indication (PLT25-PLT32)
- Edited DNP Map settings 2 for single phase tripping
- Edited W3/W4 open pushbutton LED's to account for single-phase tripping
- Edited pushbutton and target LED's (and labels), along with the proper logic based on if there is 3 or single phase tripping
- Edited trip equation for group 2 (only for trip target LED indication)

Variables removed from Group 2 (still included in group 1):
- PCT03-04
- PLT21
- PLT24
- PSV05-08
- PSV36-38
- PSV46-48
- PSV55
- PSV57
- PSV62-63

INSTRUCTIONS FOR GROUP 2:
- Open pushbutton and open remote command opens all 3 phases on the respective way
- While W1/W2 are operating, cannot manually trip W3/W4 (this is for consistency. This logic was originally here so motors aren't running at the same time)
- TRIP LED's for W3/W4 will only assert when all 3 phases are open