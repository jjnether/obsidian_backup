
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\117631 - Kennedy Space Center>)

D97FFFFF0L00 - ATS-1
- PN: A13413591JC0
- MOT: 04515211XB3X1H741412X - 2 multimode
- Uniquely Contains:
	- SEL-2407 Clock
	- SEL-3530 RTAC - 2 single mode fibers
	- SEL-2725 Five port Ethernet Switch - 3 RJ45, 1 multi mode, 1 single mode
D97FFFFF0M00 - ATS-2


- Each contains an SEL-2800 serial transceiver - multimode
- Ways 2-4 use Type 3 EZset VI controls
- Ties are:
	- ATS-1 W1
	- ATS-2 W5
- Sources are:
	- ATS-1 W5
	- ATS-2 W1

## MB

|     | ATS-1            |     | ATS-2           |     |
| --- | ---------------- | --- | --------------- | --- |
|     | Tx               | Rx  | Tx              | Rx  |
| 1   | W1 52A           |     | ==W1 52A==      |     |
| 2   | W1 52B           |     | ==W1 52B==      |     |
| 3   | W5 52A           |     | ==W5 52A==      |     |
| 4   | W5 52B           |     | W5 52B          |     |
| 5   | W1 LIVE          |     | ==W1 LIVE==     |     |
| 6   | W1 DEAD          |     | ==W1 DEAD==     |     |
| 7   | LOCKOUT          |     | ==LOCKOUT==     |     |
| 8   | ==AUTO ENABLED== |     | AUTO ENABLED    |     |
| 9   | SET AUTO CMD     |     | ==AUTO TOGGLE== |     |
| 10  | RESET AUTO CMD   |     |                 |     |
| 11  | ==OPEN W1 CMD==  |     | OPEN W1 CMD     |     |
| 12  | ==CLOSE W1 CMD== |     | CLOSE W1 CMD    |     |
| 13  | OPEN W5 CMD      |     | OPEN W5 CMD     |     |
| 14  | CLOSE W5 CMD     |     | CLOSE W5 CMD    |     |
| 15  |                  |     |                 |     |
| 16  |                  |     |                 |     |



## Listed features:
G&W Main-Tie-Main Auto Transfer Package, including:
	▪ SEL 451-5 relay as the platform for the automatic transfer logic (MOT: 045152111B3X1H741412X)
	▪ Visible One-Line display of auto-transfer mechanisms
	▪ Manual override for local operation.
	▪ Selectable time delays for initial transfer and return.
	▪ Programmable return transfer sequence, open before close or close before open
	▪ DNP 3.0 mapping for serial SCADA interfaces
	▪ Analog voltage sensing inputs from PTs
	▪ Block operations input (one per source)
	▪ Synchronism Check for Return Transfers

G&W LaZer communicating Main-Tie-Tie-Main automation scheme to prevent source paralleling via electronic 
control interlocks.
• SEL relays to facilitate the communication with Mirrored Bits messaging
• RTAC Configuration and DNP map consolidation of the two (2) SEL 451 relays.
• Transfer trip fault isolation and transfer restoration scheme

Questions:
- Do I need to select delta for voltage sensing? Or do I just use VAY, VBY, etc


Emergency OBC on return transfer:
- use case is if the ATC threw to generator, utility comes back and the healthy utility source timer starts timing, and the generator then drops out,  it should immediately transfer back to the utility rather than wait the remainder of the healthy source timer.  but it should do an OBC so it doesnt close the utility and parallel into a gen that is spinning down

- Transfer trip fault isolation is referencing fault on the tie cable, right? Then just send a trip to isolate the tie cable
- set fault target that prevents it from closing back in (add to lockout on both relays, asserts latch if either tie trips)
- sync check
	- if not in sync, prevents from closing
	- live line dead bus
	- add sync check default settings to programming spec