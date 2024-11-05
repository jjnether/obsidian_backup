
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\103220 - Leconte (CED)>)



FAT:
- visual inspection
- general operation
- automation demonstration
- communications test

Follow-up:
- Top level drawing - says motors on all ways, but way 4 doesn't have one

Normal Start-up and Restart after Emergency:
- Open all breakers
- Close substation breaker (W6)
- After 3m close T1 (W3)
- After 30s close T2 (W2)
- After 30s close T1 (W1)

Emergency Start-up
- Connect Gen to camlock set
- Open all breakers
- Close T4 gen (W5)
- After 3m close T1 (W3)
- After 30s close T2 (W2)
- After 30s close T1 (W1)

**Notes:**

LR_MODE
- Local mode blocks all remote commands from SCADA, but not commands between relays and RTAC 
- When L/R Sync is activated, all relays move to the state of W1, and toggling any of the relays changes all to that state
- When sync is active, LR state of relays will change based on PB press from any way
- "L/R SYNC" PB's don't do anything, it's only for indication

ARM
- PB LED will blink while held
- Changed armed timeout to 5 min
	- Will timeout if no sequence started within 5 min of arming
- When sequence exits, all relays will exit armed mode
- Will not arm if any conditions to exit sequence are true
- All motorized ways must be in remote mode to Arm from SCADA
	- To arm manually via PB, only W1 must be in local mode
- Can exit out of armed mode (and a sequence) by hitting/sending a disarm command
	- To disarm, hold ARM again for 5s

SEQ
- All motorized ways must be in local mode to start sequence from dedicated pushbuttons
- All motorized ways must be in remote mode to start sequence from SCADA
- Sequence will not close way if there's a trip indication on that way
	- If a trip indication on W5 or W6, will disarm
- If a way is skipped, timing still remains the same (so W1 will always close 1 min after W3, no matter if W2 was skipped due to Trip target)
- TRIP LED's for W5 and W6 must be acknowledged before entering a sequence
- 3 minute delay from closing substation (or gen) to closing other transformers (to give time for GEMS to power up)
- 5 sec wait between command and starting sequence
- 5 sec wait between opening sequence and closing sequence
- Conditions to exit sequence:
	- Sequence completes
	- Close sequence time out (4m 5s) (same time it would take for sequence to finish)
	- Open sequence time out (20 sec)
	- Way 4 is open
	- Trip LED's not acknowledged on W5 or 6 (source ways)
	- ==Loss of comms on any relay
	- Disarm command sent (not in exit seq logic, but in reset of seq in progress)
	- W5 or W6 are not closed 10 sec after starting close seq portion
- No manual open/close commands on any ways will work while sequence is active (trip still functions)

BATT TEST
- Manual battery test via PB will start a test on both relays
	- Remote command for battery test will be blocked if both relays are in local mode

COMMS
- If loss of comms on a relay >= 5 sec
	- Relay will disarm
	- L/R sync mode will disable
	- Sequence in progress will disable

- Motor timeout and actuator malfunction doesn't block open/close, they're only alarms reset with target reset

Questions:
- Should I ask any questions regarding commissioning?
- Is there a certain sequence they want to open all ways?
	- Currently it's just 1-6
- LOOK OVER LOGGING ON RTAC
- What to add for logging/alarms in RTAC?
- HOW TO MULTIPLY ANALOG INPUTS BY 10
	- IS THIS NEEDED?
- What if I arm locally, but there's a condition to block arming?

Heartbeat permissive: SV05T
Remote mode permissive: NOT LT02

REMOTE BITS:
- RB01 - HEARTBEAT
- RB02 - BATT TEST
- RB03 - TARGET RESET
- RB04 - SET LOCAL
- RB05 - SET REMOTE
- RB06 - TRIP/OPEN
- RB07 - CLOSE
- RB08 - ARM RELAY
- RB09 - DISARM RELAY
- RB10 - SEQ IN PROGRESS
- RB11 - EXIT SEQ
- RB12 - L/R SYNC
- RB13 - L/R DESYNC
- RB14 - ARM BLOCK (W1)

DNP MAP BINARY OUTPUTS:
- 00 - BATT TEST
- 01 - ARM SYSTEM
- 02 - DISARM SYSTEM
- 03 - NORMAL SEQ START
- 04 - E SEQ START

NETWORK:
RTAC ETH1 - 192.168.1.2
Way 1 - 192.168.1.11
Way 2 - 192.168.1.12
Way 3 - 192.168.1.13
Way 4 - 192.168.1.14
Way 5 - 192.168.1.15
Way 6 - 192.168.1.16
Relay Default Gateway - 192.168.1.1
Port F Baud rate - 38400

TESTING:
Current sensing - 40/50/60 (.08, .1, .12)

Settings:
50P - 1
50G - .5
51P - .25 , TD = 1
51G - .1 , TD = 1

Test:
50P - 1.1   (550)
50G - .6     (300)
51P - .3 (2.87s)  (150)
51G - .15 (1.3s)   (75)

RTAC_TESTING:
ETH1 - 192.168.1.3


PUNCHLIST ITEMS
- Sync relays/system with GPS clock they have on network
	- NTP
	- WE NEED IP OF SATELLITE CLOCK

Updated firmware from **R400-V0** to **R400-V2**

==NOTE
- Added local mode check to start sequence with dedicated pushbuttons (added to RTAC program, need to upload)

Brian Pizzi - Wartsila
Travis Kahel - Baker Electric

10.0.0/24 network

RTAC Customer Login:
- LECONTE/LECONTE

DA commissioning -  Oct 31
AMS  on site support - Nov 18 --- 21?

ON-SITE NOTES:
- 50G1D set to 0 instead of .001 for Way 6
- TS1 PDF not consistent with other PDF's regarding 51G1P

