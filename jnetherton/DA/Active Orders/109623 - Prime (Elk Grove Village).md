- Why does local ITS latch only reset if it's switch 1 (other than timeout) (PLT25R) - EDITED
	- WAS `PLT25R := (PSV06 AND PSV07 AND (VB001 AND VB003) AND NOT LB01) OR PCT11Q`
- Edited PSV16 for opening S2 also when LB01=1
- After an ITS, local relay goes to manual, but not other relay
	- goose command to set to manual is only asserted on PB press, auto mode blocked, or the command itself (from other relay)
	- EDITED - added falling trigger of ITS and both RTS to trigger this
- Sometimes when killing a source on the switch with tie way closed, it opens tie way then closes again, but not always
	- PLT26 should not be asserting
- BUS 1 LIVE not asserting properly for switch where LB01=1
	- FIXED - PSV38 and T_LED
- Added PB lock to auto/manual mode/set to prefer
- Fixed preferred mode
- Discrete Inputs offset by 2?
- SF6 pressure ok - should be SF6 alarm

Relay IP
- switch 1 - 192.168.1.11
- switch 2 - 192.168.1.12
RTAC IP
- switch 1 - 192.168.1.2
- switch 2 - 192.168.1.3
Ethernet Switch IP
- switch 1 - 192.168.10.1
- switch 2 - 192.168.10.2