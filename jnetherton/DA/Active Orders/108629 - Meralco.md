
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\_Meralco\108629 - Meralco>)

- POD - 78209
- S1 and S2 always closed and paralleled - close transition
- RCPMSG
	- remote controllable pad mount switchgear
- Make sure production has the latest revision files
- F-00238 - ATC production test

- For DNP testing, make sure relay and RTAC time are synced
	- Relay will request time from RTAC
- MAKE SURE ANY SETTINGS EDITS ALSO GET UPDATED IN PRODUCTION FOLDERS
- 19920V Nominal (L-G)
	- 34.5 kV L-L


Relays:
- A13413579ADF (700G)
- A13413591HD0 (451)

==108629
- D94980173ADS (4 way)
- D94980173ADT (3 way)
108630
- D94980173ADS
- D94980173ADT
- DM8SCLLFFY00
- DMSLLFF00AX0
- DMSLFFL00P00
108631
- DM8SCLLF0D00
- DMSLLF000Z00
- DMSLFL000G00



RTAC IP: 192.168.1.10
451 IP: 192.168.1.5
700G IP: 192.168.1.6

BAUD: 57600

Vnom setting: 19900
dead voltage: 15920 (80%)
live voltage: 17910 (90%)

3-WAY RCF:
Y
1.123
1.048
1.116

Z
1.118
1.120
1.109

4-WAY RCF:
Y
1.118
1.117
1.114

Z
1.128
1.100
1.126

==RTAC change time before shipment

NOTES:
- For testing SF6, pull IN107 (451)

QUESTIONS:
- SCADA aliases?
- Is it ok that DNP maps match even though one is 3 way, so it has points for a way that doesn't exist?
- will power supply automatically run battery test upon startup, or does relay need logic for that to happen?
- FAT said to set batt test to every hour and verify with SER?
	- Can't set to 1 hour in template, and do we even need this? (removed for now)
- How to simulate hardware alarm?
- 451 analog inputs for current are showing at actual value (4000 A) while the 700G shows it at x100 - this ok?



TO TEST:
- Insert 220VAC through circuit breaker and show it powers up
	- Also verify 24 VDC out for telecoms
- Demonstrate switch mode for 700G
- 700G check 51P overcurrent fault indication
- Check Fault current analog input for 451 (seemed scaled too high)
- remove redundant SF6 DNP point?

- Check Fault current analog input on 451
- send scanned FAT to engelbert


MEETING:
- 7 units - 6 installed (5 online, one had flashover)

- Values reported for voltage were in kV (forced scaling to 1.0)
	- Changed scaling forced to 100, so user can see kV with 2 decimals
- The pickup values are SETTINGS. These settings are input as secondary values. When sent over DNP, they are scaled by 1000. Note that if 50 settings are disabled, they get set to 100. This means the sent DNP value will overflow, showing 32767
- Tested remote target reset - works
- Tested binary inputs for 51P/51G - THEY DO NOT LATCH