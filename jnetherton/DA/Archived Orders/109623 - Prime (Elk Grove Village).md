
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\109623 - Prime (Elk Grove Village)>)

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
- The current auto entry logic actually only requires that the local source is closed and any tie is open (not both sources closed, doesn't check other source status
- added logic for ITS to accommodate for when we are single ended as a starting point (one src dead)
- When there's a preferred source, it won't single end itself if both sources are closed and healthy, but after an ITS due to a lost source, it will return to a single ended state fed from the preferred source
	- alternately, if no source is preferred, RTS behavior after ITS would just have both sources closed with an open tie point
- After changing preferred state, auto, or manual mode, must wait 10 sec before changing again due to timer
- Added a delay timer for entering transfer logic after auto mode or changing pref mode

Relay IP
- switch 1 - 192.168.1.11
- switch 2 - 192.168.1.12
RTAC IP
- switch 1 - 192.168.1.2
- switch 2 - 192.168.1.3
Ethernet Switch IP
- switch 1 - 192.168.10.1
- switch 2 - 192.168.10.2

```
PLT25S := PLT01 AND PCT08Q AND PSV40 AND NOT VB030 AND PSV05 # LOCAL SOURCE ITS LATCH
- auto mode
- loc src dead
- alt src stable
- good comms
- loc src closed

PLT25R := (PSV06 AND PSV07 AND (VB001 AND VB003)) OR PCT11Q #ITS COMPLETE OR EXIT AUTO MODE OR FAILED TRANSFER
- loc src open
- loc tie closed
- adj src closed
- adj tie closed
	- or
- NOT auto mode
	- or
- timeout

PSV16 := (PLT25 AND IN101 AND NOT LB01) OR (PLT25 AND IN301 AND LB01) #OPEN DEAD SOURCE
- ITS
- source closed

PCT17IN := PLT25 AND PSV06 AND PSV08
PSV17 := PCT17Q #CLOSE LOCAL TIE IF OPEN POINT
- ITS
- loc src open
- loc tie open

PCT18IN := PLT25 AND PSV06 AND PSV07 AND VB004
PSV18 := PCT18Q #CLOSE ADJ. SW. TIE IF OPEN POINT
- ITS
- loc src open
- loc tie closed
- adj tie open

PCT19IN := PLT25 AND PSV06 AND PSV07 AND VB003 AND VB002 AND PLT02
PSV54 := PCT19Q #CLOSE ADJ. SOURCE IF LOC. SRC IS PREF SOURCE (SINGLE ENDED)
- ITS
- loc src open
- loc tie closed
- adj tie closed
- adj src open
- pref src

---
PLT26S := PLT01 AND PCT06Q AND VB008 AND NOT PLT02 AND PSV06 # LOCAL SOURCE RTS LATCH
- auto mode
- loc src healthy
- adj src healthy
- NOT pref src
- loc src open

PLT26R := (PSV05 AND PSV08 AND VB001) OR NOT PLT01 OR PCT12Q #LOCAL SOURCE  RTS COMPLETE OR EXIT AUTO MODE OR FAILED TRANSFER
- loc src closed
- loc tie open
- adj src closed
	- or
- NOT auto mode
	- or
- timeout

PSV26 := PLT26 AND PSV06 AND PSV07 # OPEN LOCAL TIE
- RTS
- loc src open
- loc tie closed

PCT27IN := PLT26 AND PSV08 AND PSV06 AND NOT VB030
PSV27 := PCT27Q #CLOSE LOCAL SOURCE
- RTS
- loc tie open
- loc src open
- NOT bad comms

---
PLT27S := PLT01 AND PCT06Q AND VB008 AND PLT02 AND PSV06 # LOCAL SOURCE RTS LATCH
- auto mode
- loc src healthy
- adj src healthy
- pref src
- loc src open

PLT27R := (PSV05 AND PSV07 AND VB002 AND VB003) OR NOT PLT01 OR PCT13Q #LOCAL SOURCE  RTS COMPLETE OR EXIT AUTO MODE OR FAILED TRANSFER
- loc src closed
- loc tie closed
- adj src open
- adj tie closed
	- or
- NOT auto mode
	- or
- timeout

PSV28 := PLT27 AND PSV06 AND VB001 # OPEN ADJ. SOURCE
- preferred RTS
- loc src open
- adj src closed

PCT28IN := PLT27 AND PSV06 AND VB002
PSV29 := PCT28Q #CLOSE LOCAL SOURCE
- preferred RTS
- loc src open
- adj src open

PCT29IN := PLT27 AND PSV05 AND VB002 AND PSV08
PSV30 := PCT29Q #CLOSE LOCAL TIE
- preferred RTS
- loc src closed
- adj src open
- loc tie open

PCT30IN := PLT27 AND PSV05 AND VB002 AND VB004
PSV31 := PCT30Q #CLOSE ADJ. SW. TIE IF OPEN POINT
- preferred RTS
- loc src closed
- adj src open
- adj tie open

```
