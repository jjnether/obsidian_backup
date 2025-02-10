
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\Camp Carroll - 108664 - 106176>)

1 relay
- D94980182ATP
- B13440083NX0
- SEL 0351S6XHB2E1122
3 relays
- D94980182ATM
- B13440083NU0
- SEL 0351S6XHB2E1122
4 relays
- D94980182ATN
- B13440083NW0
- SEL 0351S6XHB2E1121 - (ends in 22 in drawing)


Workstation:
- username: ADMIN
- PW: Stc%26736
Server:
- username: Administrator
- PW: GW_Electric1905
Survalent:
- username: Lazer3
- PW: 305Crossroads


POTT - Permissive Overreach Transfer Trip
- If it sees a forward fault, sends a POTT signal forward (permission to trip) to the device across the line
	- Trips if it sees a forward fault and receives a POTT signal from the other side of the line
- Should be close to instant (~30ms)
DCB - Directional Comparison Blocking
- Trips if it sees a forward fault and receives no blocking signal, then sends a DCB signal backwards
	- Sends the signal backwards because the fault will either be interrupted downstream or it will interrupt the fault itself if it doesn't receive a DCB signal
	- After DCB trip, sends a transfer trip signal forward to the device across the line (this trips it out in the case of a radial fed fault)
- If it sees a reverse fault, will send DCB signal forward because the fault will either be interrupted downstream or...
	- Will trip if there's a reverse fault and comms are down - could be a bus fault
- Slower than POTT (~60ms)

- If there's a breaker failure, it will send a transfer trip to all adjacent devices
- Forward current direction is considered into the line
	- Needs voltage to determine current direction - if there is voltage loss at the switch, directional tripping is disabled
- Loop Tie switches have 3 channels of GOOSE comms while the normal loop switches only have 2


GOOSE Testing:
- Each relay only sends two channels, receives up to three
	- We want to test to make sure that for each channel, the GOOSE is being transmitted properly and the right relays are subscribed
- We're sending RB01-RB08 over, so we have spare 
- We can make a state machine using a counter which goes up to 2, and cycles for sending to Channel A or Channel B
- It can be triggered either via pushbutton (spare blank PB08) or via SCADA by pulsing a remote bit
- While sending the test signal, the PB LED can blink slowly for sending channel A, quickly for sending channel B, and solid if receiving a signal
- Add a watchdog timer to turn off sending in case it's accidentally left on
- Add an alarm in SCADA for receiving the signal, so it's clear which relays are receiving it and it's logged

- RelaySimTest is iterative and looks 100ms (adjustable) past the newest event on each iteration
	- So initially, it will send fault current and will see trips within the first 100ms, but won't halt the fault current as they are new trips
	- Next iteration, it will now look for new trips and will look 100ms past the new trips (so it will now account for breaker failure trips which happen at 150ms)

- Woody's comments:
	- POTT and DCB scheme sample for customer
	- Top level drawings for dimension checks
	- Production test reports for each type of switch
	- Cybersecurity portion? - see drawing #609 from customer
	- Long term storage method/manual?
-  FIX 351 LABELS
- LT10 was auto mode - removed at some point
- RMB3A - received mirrored bit 3A, breaker failure trip - will never assert as we're using GOOSE - synonymous with VB003
	- Same for RMB6B, but from channel B - synonymous with VB016
	- VB016 is breaker failure from channel C
- SV3T is loss of voltage trip - local bit 1, no permissives, no timer by default
- SV9T

- SD-10 W1 VB strange DNP where VB is minus 1?

CAL
CLARKE
PARTNO
0351S6XHB2E1122
ID



`SV9T`