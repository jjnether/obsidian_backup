
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
	- double check this if we keep LOV logic?
- No Sync Check
	- do we need it?
- MV32? - seems to just be locked to 0 with the template for some reason?
	- I think used to control which side (Y/Z) is considered source side