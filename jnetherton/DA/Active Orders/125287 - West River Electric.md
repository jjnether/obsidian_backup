
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\125287 - West River Electric>)

Primary Voltage (L-N) - 14400

POD - 108557
- what is settings group 1 vs group 2?

- Disabled 2nd harmonic blocking and removed from TR3P equation - Erich said most customers don't use it, and we see it more when we feed large transformers.
- I know this had a good POD, however when we test please be sure to verify the system operates as intended when SPE is enabled and disabled (during normal operations, LOV, and OC events (including single phase lockout))
- To enter auto, must have good comms, not HLT, one source open and the other closed.
	- This could result in entering auto and it immediately timing for an initial transfer or a return transfer to a preferred source
- A manual recloser operation (close/open) issued locally or remotely from SCADA will kick out of auto
- Note that while the recloser is in the cycle state and is timing for a reclose, the auto transfer timing logic is not active. The recloser will either resume transfer logic timing if the recloser successfully clears the fault, or it will be kicked out of auto mode if the recloser locks out due to a permanent fault.
- ==For LOV tripping, there was extra wording in the programming spec regarding the ATS logic always executing before LOV logic and the LOV will only trip if alternate source not available/stable and reclosers are not in auto
- ==No Sync Check
	- add it if time allows
- ==A dead alternate source does prevent the initial transfer timer from counting
	- we actually want it to time even if alternate source is dead, but it doesn't transfer until it's live 
		- add dropout of a couple cycles to prevent blips
	- Previously, I did: After the initial transfer delay period has expired, the relay will verify voltage is live (voltage on all 3 phases is above the user settable live voltage threshold) on the other utility feed. If the other utility feed is live, the dead utility feed way will open.
- For non-preferred mode, maybe it shouldn't allow any selection of a preferred source?
- 52A3P - If we have the time we might want to update the logic to be more secure and use the status point that also incorporates current readings incase we have issues with the mechanism or wiring making it look like the contacts are open ,but in reality they are not because we see current.
- ==Need to add functionality for Manual return mode to also work in non-preferred source mode
- Maybe 30 cycles for hysteresis for live/dead source?
	- This may only be needed if we stick to the fact that it will time for a transfer regardless of alternate source being live/dead



SV47 := SV62 AND LT27 AND NOT 52A3P AND NOT VB003 AND NOT VB001 # EMERGENCY OBC
- timing for return transfer
- preferred source
- open
- remote source dead
- good comms

SV54 := MV31 = 0.00 AND 52A3P AND (VB002 AND NOT VB001) # RTID

SV57 := SV61T AND VB003 AND NOT VB001 AND NOT 52A3P # CLOSE REMOTE SWITCH
SV58 := SV62T AND (MV31 = 1.00 OR (52A3P AND MV31 = 0.00 AND SV54T)) AND LT27 OR SV47T AND VB002 AND NOT VB001 # TRIP REMOTE SWITCH

SV59 := (SV62T AND (MV31 = 1.00 AND NOT VB002 OR MV31 = 0.00) AND LT27 OR VB006 OR SV47T AND NOT VB002) AND NOT VB001 # ATC CLOSE
SV60 := (SV61T AND VB003 OR VB007) AND NOT VB001 # ATC TRIP

SV61 := (LT27 OR LT32) AND NOT LT28 AND LT29 AND NOT (79CY3P OR 79CYA OR 79CYB OR 79CYC OR SV55T) # INITAL TRANSFER DELAY
SV62 := LT28 AND LT29 AND NOT LT32 # STABLE/HEALTHY SOURCE/ RETURN TRANSFER TIMER

MV31 - 1 = OBC
MV32 - 1 = Y SOURCE

==ADD DEAD LINE VOLTAGE FOR SUPERVISING CLOSING (NOT PARALLELING)
- For parallel blocking, allow closing live line and dead bus, but don't allow live bus dead line (backfeeding substation)

CLOSE AND SV20
- ALLOW MANUAL PARALLELING? (MV05 = 1)
	- if yes, it will let user use PB or remote commands to close a live line and dead bus (sync check optional)
	- if no, it will block any manual closing of live line and dead bus
	- live bus and dead line will always be blocked
- ENABLE SYNC CHECK?
	- applies to both CBO transfer and manual paralleling (if enabled)


Block if load is live OR load and line are live and (no paralleling enabled or sync check enabled and bad sync check)