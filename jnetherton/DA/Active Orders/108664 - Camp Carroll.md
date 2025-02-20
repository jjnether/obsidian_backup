
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\Camp Carroll - 108664 - 106176>)

1 relay
- D94980182ATP
- B13440083NX0
- SEL 0351S6XHB2E1122
	- A13413539YM0
3 relays
- D94980182ATM
- B13440083NU0
- SEL 0351S6XHB2E1122
	- A13413539YM0
- A13413579ADP - 700G
4 relays
- D94980182ATN
- B13440083NW0
- SEL 0351S6XHB2E1121 - (ends in 22 in drawing)
	- A13413539GT0


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
- If it sees a reverse fault, will send DCB signal forward
	- Will trip if there's a reverse fault and comms are down - could be a bus fault
- Slower than POTT (~60ms)

- If there's a breaker failure, a transfer trip will be sent to all adjacent devices
- Forward current direction is considered into the line
	- Needs voltage to determine current direction - if there is voltage loss at the switch, directional tripping is disabled
- Loop Tie switches have 3 channels of GOOSE comms while the normal loop switches only have 2

- RelaySimTest is iterative and looks 100ms (adjustable) past the newest event on each iteration
	- So initially, it will send fault current and will see trips within the first 100ms, but won't halt the fault current as they are new trips
	- Next iteration, it will now look for new trips and will look 100ms past the new trips (so it will now account for breaker failure trips which happen at 150ms)

- RMB3A - received mirrored bit 3A, breaker failure trip - will never assert as we're using GOOSE - synonymous with VB003
	- Same for RMB6B, but from channel B - synonymous with VB016
- SV9T - automation tripping
	- (previous comment) - Pickup should be set to Value greater than slowest tripping time of fuse on load????  This is to protect against a fault on the switch/bus????

TO DO:
- SM-2
	- scada check RB7 for RSTRGT
	- scada check LT12 for DCB indication

CAL
CLARKE
PARTNO
0351S6XHB2E1122
ID


TRIP:
- `SV9T+RB1*LT3+/PB10*LT4*!LT10+/SV3T+RMB3A+VB003+RMB6B+VB016+VB026`
	- Automation tripping
	- Remote Trip (with remote mode)
	- PB Trip (with no PB lock)
	- LOV trip
	- breaker failure trip - channel A
	- breaker failure trip - channel B
	- breaker failure trip - channel C (only ATN)
PT1 (for POTT):
- `!(67P3+67G3)*(RMB1A+VB001)`
	- no reverse overcurrent pickup and POTT signal received

SV9:
- `(67P2T+67G2T)*(VB010+!VB002)+ECTT+51G1T+51P1T+51G2T+51P2T+VB004`
	- Forward overcurrent (with bad quality or no DCB block)
	- Echo conversion to trip (POTT)
	- 

51P2TC:
- `67P3*(RMB1B+VB011)+67P3T*VB020+67P3*(RMB3B+VB013)+67P3T*!(RMB4B+VB014)`

VB013


![[Pasted image 20250218112700.png]]


![[Pasted image 20250218133150.png]]


TO DO:
- Build out communication screens (both the physical switch ports and the GOOSE lines)
- Add password for every operation? - need to check if customer wants this
- check if we can change bottom left IP to "primary" and "backup"
- Review deadbanding in survalent and relay for analogs
- Review polling times in survalent comm settings
- Keep an eye on target LED's resetting when they shouldn't
	- Might be due to bouncing on IN101, as IN101 is 52A, and 52A inherently resets target LED's

GOOSE Testing:
- Each relay only sends two channels, receives up to three
	- We want to test to make sure that for each channel, the GOOSE is being transmitted properly and the right relays are subscribed
- We're sending RB01-RB08 over, so we have spare 
- We can make a state machine using a counter which goes up to 2, and cycles for sending to Channel A or Channel B
- It can be triggered either via pushbutton (spare blank PB08) or via SCADA by pulsing a remote bit
- While sending the test signal, the PB LED can blink slowly for sending channel A, quickly for sending channel B, and solid if receiving a signal
- Add a watchdog timer to turn off sending in case it's accidentally left on
- Add an alarm in SCADA for receiving the signal, so it's clear which relays are receiving it and it's logged


- Move cable energized to LV1
- Use LT10 and LT16 for states
- Use SV15 and SV16 for timers (30 cyc and 60 cyc)
- Remove LT10 from TR equation
- LB 2 FOR SUPERVISION