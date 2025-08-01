
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\125287 - West River Electric>)

POD - 108557
- what is settings group 1 vs group 2?

- I know this had a good POD, however when we test please be sure to verify the system operates as intended when SPE is enabled and disabled (during normal operations, LOV, and OC events (including single phase lockout))
- To enter auto, must have good comms, not HLT, one source open and the other closed.
	- This could result in entering auto and it immediately timing for an initial transfer or a return transfer to a preferred source
- A manual recloser operation (close/open) issued remotely from SCADA will kick out of auto
	- should it?
	- should local commands also kick out of auto? - or maybe I think local commands won't go through as pushbuttons may not work while in auto?
- Note that while the recloser is in the cycle state and is timing for a reclose, the auto transfer timing logic is not active. The recloser will either resume transfer logic timing if the recloser successfully clears the fault, or it will be kicked out of auto mode if the recloser locks out due to a permanent fault.
	- check this
- For LOV tripping, there was extra wording in the programming spec regarding the ATS logic always executing before LOV logic and the LOV will only trip if alternate source not available/stable and reclosers are not in auto
- ==No Sync Check
	- add it if time allows
- ==A dead alternate source does prevent the initial transfer timer from counting
	- we actually want it to time even if alternate source is dead, but it doesn't transfer until it's live 
		- add dropout of a couple cycles to prevent blips
	- Previously, I did: After the initial transfer delay period has expired, the relay will verify voltage is live (voltage on all 3 phases is above the user settable live voltage threshold) on the other utility feed. If the other utility feed is live, the dead utility feed way will open.
- LT30/LB04 - auto return
- LT31/LB05 - Manual return
- LT32/LB06 - no pref. source mode selected
	- should move these local bits instead to template?
- re-enable reclosing
- re-enable fast curve
- For non-preferred mode, maybe it shouldn't allow any selection of a preferred source?
- ensure lockout kicking out of auto is rising edge of lockout
- Will system still work if one control is in group 1 and another is in group 2?
	- add some kind of check for this
	- same check for auto/manual return and preferred/non-preferred, both are preferred?
- 52A3P - If we have the time we might want to update the logic to be more secure and use the status point that also incorporates current readings incase we have issues with the mechanism or wiring making it look like the contacts are open ,but in reality they are not because we see current.
- Need to add functionality for Manual return mode to also work in non-preferred source mode
- Make sure to add logic for emergency OBC
- ==When in no pref. mode (LT32 = 1), if both sources are lost, it will not restore
	- Shouldn't it restore once a healthy source comes online?
- Maybe 30 cycles for hysteresis for live/dead source?
	- This may only be needed if we stick to the fact that it will time for a transfer regardless of alternate source being live/dead