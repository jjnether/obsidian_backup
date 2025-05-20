
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\117631 - Kennedy Space Center>)

D97FFFFF0L00
- PN: A13413591JC0
- MOT: 04515211XB3X1H741412X
- Uniquely Contains:
	- SEL-2407 Clock
	- SEL-3530 RTAC
	- SEL-2725 Five port Ethernet Switch
D97FFFFF0M00


- - Each contains an SEL-2800 serial transceiver

## MB

| Switch 1 |     | Switch 2 |     |
| -------- | --- | -------- | --- |
| Tx       | Rx  | Tx       | Rx  |
|          |     | W1 52A   |     |
|          |     | W1 52B   |     |
|          |     | W5 52A   |     |
|          |     | W5 52B   |     |
|          |     |          |     |
|          |     |          |     |
|          |     |          |     |
|          |     |          |     |



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