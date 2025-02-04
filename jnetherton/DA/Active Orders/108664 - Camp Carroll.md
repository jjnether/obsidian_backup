
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
- a
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
- Trips if it sees a forward fault and receives a POTT signal from the other side of the line
	- Will also send a POTT signal forward (permission to trip) to the device across the line
- Should be close to instant
DCB - Directional Comparison Blocking
- Trips if it sees a forward fault and receives no blocking signal, then sends a DCB signal to the device behind it
	- Sends the signal backwards because it knows the fault will either be interrupted downstream or it will interrupt the fault itself if it doesn't receive a DCB signal
- After DCB trip, sends a transfer trip signal forward to the device across the line (this trips it out in the case of a radial fed fault)
- Slower than POTT

- Forward current direction is considered into the line
	- Needs voltage to determine current direction - if there is voltage loss at the switch, directional tripping is disabled
- Reverse fault is supervised by bad comms - if there's a reverse fault and comms are down, could be a bus fault, so will trip
- Loop Tie switches have 3 channels of GOOSE comms while the normal loop switches only have 2
- VB010 - bad comms across the line
- VB020 - bad comms from relay in same switch
- VB030 - bad comms from 3rd relay in same switch (for loop tie)