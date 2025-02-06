
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
- Trips if it sees a forward fault and receives a POTT signal from the other side of the line
	- Will also send a POTT signal forward (permission to trip) to the device across the line
- Should be close to instant (~30ms)
DCB - Directional Comparison Blocking
- Trips if it sees a forward fault and receives no blocking signal, then sends a DCB signal to the device behind it
	- Sends the signal backwards because it knows the fault will either be interrupted downstream or it will interrupt the fault itself if it doesn't receive a DCB signal
- After DCB trip, sends a transfer trip signal forward to the device across the line (this trips it out in the case of a radial fed fault)
- Slower than POTT (~60ms)

- If there's a breaker failure, it will send a transfer trip to all adjacent devices
- Forward current direction is considered into the line
	- Needs voltage to determine current direction - if there is voltage loss at the switch, directional tripping is disabled
- Reverse fault is supervised by bad comms - if there's a reverse fault and comms are down, could be a bus fault, so will trip
- Loop Tie switches have 3 channels of GOOSE comms while the normal loop switches only have 2
- VB010 - bad comms across the line
- VB020 - bad comms from relay in same switch
- VB030 - bad comms from 3rd relay in same switch (for loop tie)

- RelaySimTest is iterative and looks 100ms (adjustable) past the newest event on each iteration
	- So initially, it will send fault current and will see trips within the first 100ms, but won't halt the fault current as they are new trips
	- Next iteration, it will now look for new trips and will look 100ms past the new trips (so it will now account for breaker failure trips which happen at 150ms)


-  FIX LABELS FOR BATTERY TEST

- ATN WAY 3 - WHERE DO WE WANT LBS INDICATION? - IT'S CURRENTLY STILL ON LED, BUT LABEL IS BLANK
	- ADD INDICATION TO DISPLAY POINT?
	- does way 3 source indicate lb?
- 700G - WAY 2&3 - FIX OPEN INDICATOR FOR FI - FIX DISPLAY POINT TO SPECIFY LB
	- Also add "Way 2 *FI* closed and open to label"
- ATN W1 lockout when manually tripping?
- Change banner so Daegu is replaced with Camp Carroll
- Source way on 351's normally indicates FI position, but there's also a source way GND???
- Add back acknowledge battery alarm on 351 non-w1's?
	- delete SV8?
	- add PB7*!IN206 to RST8
- Change source way terminology in DP for w2, w3?

Program Changes:
- ATM 351S
	- Added SV2T to Low SF6 LED (LED4)
	- Removed "Source Way Energized" from display point logic (DP3,DP4)
	- Changed Battery test dropout to 60 cycles (SV7T)
	- Added reverse time overcurrent to match phase time o/c (67G2)
	- Removed OUT107 - some kind of battery alarm output contact, but nothing wired to it
	- ONLY NON-W1 RELAYS
		- Removed Batt Test logic from Non-way 1 relays
		- LT8, LT11, SV4,SV5,SV6,SV7
	- ONLY ON W3 351S
		- Removed OUT101, OUT102, LT6, SV1, CLOSE, LED1, LED2 (no motors)
- 700GW: front panel
	- Change FI PB LED's and added open indication (PB3 and PB4)
	- Edited DP for LB's



CAL
CLARKE
PARTNO
0351S6XHB2E1122
ID



|       | Manual operation | Relay operation |
| ----- | ---------------- | --------------- |
| SD-09 | x                |                 |
| SD-10 | x                |                 |
| SD-11 | x                |                 |
| SD-12 | x                |                 |
| SC-03 | x                |                 |
| SC-04 | x                |                 |
| SC-05 | x                |                 |
| SC-06 | x                |                 |
| SM-2  | x                |                 |
