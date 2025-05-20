
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\117631 - Kennedy Space Center>)

D97FFFFF0L00
- PN: A13413591JC0
- MOT: 04515211XB3X1H741412X
- Uniquely Contains:
	- SEL-2407 Clock
	- SEL-3530 RTAC
	- SEL-2725 Five port Ethernet Switch
D97FFFFF0M00


- Each contains an SEL-2800 serial transceiver
- Ways 2-4 use Type 3 EZset VI controls
- Ties are:
	- ATS-1 W1
	- ATS-2 W5
- Sources are:
	- ATS-1 W5
	- ATS-2 W1

## MB

|     | Switch 1     |     | Switch 2     |     |
| --- | ------------ | --- | ------------ | --- |
|     | Tx           | Rx  | Tx           | Rx  |
| 1   | W1 52A       |     | W1 52A       |     |
| 2   | W1 52B       |     | W1 52B       |     |
| 3   | W5 52A       |     | W5 52A       |     |
| 4   | W5 52B       |     | W5 52B       |     |
| 5   | W2 LIVE      |     | W2 LIVE      |     |
| 6   | W2 DEAD      |     | W2 DEAD      |     |
| 7   | LOCKOUT      |     | LOCKOUT      |     |
| 8   | AUTO ENABLED |     | AUTO ENABLED |     |
| 9   | OPEN         |     |              |     |
| 10  |              |     |              |     |
| 11  |              |     |              |     |
| 12  |              |     |              |     |
| 13  |              |     |              |     |
| 14  |              |     |              |     |
| 15  |              |     |              |     |
| 16  |              |     |              |     |



## Listed features:
G&W Main-Tie-Main Auto Transfer Package, including:
	▪ SEL 451-5 relay as the platform for the automatic transfer logic (MOT: 045152111B3X1H741412X)
	▪ Visible One-Line display of auto-transfer mechanisms
	▪ Manual override for local operation.
	▪ Selectable time delays for initial transfer and return.
	▪ Programmable return transfer sequence, open before close or close before open
	▪ Test mode operations with push buttons to simulate loss of voltage for source 1 and 2
	▪ DNP 3.0 mapping for serial SCADA interfaces
	▪ Analog voltage sensing inputs from PTs
	▪ Block operations input (one per source)
	▪ SEL sequence of events recorder
	▪ Factory assembled and tested.
	▪ Synchronism Check for Return Transfers

G&W LaZer communicating Main-Tie-Tie-Main automation scheme to prevent source paralleling via electronic 
control interlocks.
• SEL relays to facilitate the communication with Mirrored Bits messaging
• RTAC Configuration and DNP map consolidation of the two (2) SEL 451 relays.
• The exact automation system design will be discussed between G&W Electric and all project representatives 
prior to implementation.
• Transfer trip fault isolation and transfer restoration scheme

Questions:
- Can I ignore adding test mode?
- Do I need to select delta for voltage sensing? Or do I just use VAY, VBY, etc
- Am I ok to just treat one of the tie ways as normally closed?
- Transfer trip fault isolation is referencing fault on the tie cable, right? Then just send a trip to isolate the tie cable
- Any idea why we wired 52A/52B 3 times redundant to the relay for each source/tie way?
	- Quote says:
		- Ways 1 and 5 are equipped with quantity three auxiliary Form C contacts wired to the control cabinet for use by the control.
		- Ways 2, 3 and 4 are equipped with quantity two auxiliary Form C contacts wired to the control cabinet for use by the control.
