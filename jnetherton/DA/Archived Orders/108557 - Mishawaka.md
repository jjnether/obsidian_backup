
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\108557 - Mishawaka>)

-   Don't use the IP that's already there (it's already on their network)

MV32 - 0 = Z, 1 = Y (source side)

SV18 - check voltage

LT15 -

(NOT 52A_A AND NOT 52A_B AND NOT 52A_C) OR (VB001 AND (NOT VB011 OR NOT VB012 OR NOT VB013 OR VB010))

Source z side for both


10.43.28.150 - primary - viper1 - NC

10.43.28.151 - alternate - viper2 - NO

10.43.28.152 - 2411



OUT7 = 52A3P



SV42T needs to reset auto mode - add to reset 29 (added to SV56)

To simulate both line and load sides having voltage when closed (while test set is only attached to line side), use an output contact to connect line and load side VS, then set the output contact equation to 52A3P (close status)

We would like to see some changes to the 2411 programming, however:

-   LEDs to indicate status of breaker 52-A, B, C, UF. LED illuminated when breaker is closed (in the case of 52-A, illuminated means no undervoltage trip). We already did this part in house for testing purposes.
    -   Added 52A breaker status for each LED
-   PB1 used as an indicator and a toggle for auto transfer of Vipers. We want to be able to enable/disable auto transfer for all devices from this relay.
    -   Added with LED to show when enabled
    -   Edited LT29, SV27 in 651
    -   LT01
-   PB2 used for remote control enabled.
    -   Added with LED to show when enabled
    -   LT03
-   PB3 used for push button lockout.
    -   LT02
-   PB4 unused.
-   Need DNP map for this device when work is complete.
    -   On SCADA, I will want to see the status of the 4 breakers (as the relay sees them), remote status, push button lockout status, auto transfer status. Auto transfer should have control capability as well on this unit.


Same test as on clovers (cmc 356)
- time overcurrent looked good
- 30 cycle delay on instantaneous
	- disabled HBL2
	- If they increased HBL, it would also increase
	- says he took out the HBL2DO, and he was still getting the delay
- Injected 120hz, tripped when it shouldn't have due to HBL2
- Timing is setup as pole contact

# Single phase enable and pole open should prevent ground tripping, but not phase tripping
PRIMARY TR3P := ((51PT OR 50P2T OR ((51G1T OR 50G2T) AND NOT (SPE AND SV26T))) AND NOT HBL2T) OR SV14T OR OC3 AND LT03 OR 81D1T # 3-PHASE TRIP CONDITIONS

ALTERNATE TR3P := ((51PT OR 50P2T OR ((51G1T OR 50G2T) AND NOT (SPE AND SV26T))) AND NOT HBL2T) OR SV14T OR OC3 AND LT03 OR 81D1T # 3-PHASE TRIP CONDITIONS


**01-02-2023**
- Updated IP's and customer trip settings
- Updated DNP map list in excel to match the ones in settings files
- Updated architect files with customer IP's
- Added goose message quality supervision where it wasn't present
- Added SV20 as a bad comms timer for 2411
- Didn't change anything in settings group 2
- Made 2411 label file


- in 651R, remove 2411 comm status watchdog

# 4-11-24 CHANGES
- Added NOT IN401 logic to SV03 for 52-A OPEN status
- Updated 52-A LED on 2411 to assert when 52-A is OPEN
- Changed GOOSE  for all 3 devices to account for swapping IN401 with SV03