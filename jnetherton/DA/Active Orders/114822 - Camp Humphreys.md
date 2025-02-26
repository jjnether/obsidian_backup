
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\Camp Humphreys (AEI) 202412 - 114822>)

Switch PN - D94980182AWG
Wiring PN - B13440087CS0
Control PN - B54010U30BX0
Relay PN - A13413539YM0
Relay MOT - 0351S6XHB2E1122

8 hour timer for battery
system voltage = 13321V (inject 120.8V)
WAY 1/4 CT RATIO - 1000:1
WAY 2/3 CT RATIO - 500:1
PT RATIO - 110.2:1


51P U3 - pickup 225A, TD = 1
- inject 300 - trip in ~5.08s
- inrush x5 1s
51G U3 - pickup 90A, TD = 1
- inject 125 - trip in ~4.27s

51P U4 - pickup 540, TD = 1.34
- inject 1080 - trip in ~2.58s
51G U4 - pickup 100, TD = 0.68
- inject 200 - trip in ~1.31s

WAY 1 - 192.168.101.225
WAY 4 - 192.168.101.226


172.26.1.160


ADD DISPLAY POINTS FOR W2/W3 POSITIONS?


- 1) FAT contents

1-1) According to the FAT report, section 5 - Overcurrent Protection, Additional note, “the VI control settings for way 2 and 3 were invalid and should be updated.”
- I think Woody provided updated settings, but we didn't see them before the FAT? We didn't test against them, but I don't remember if I updated them before shipping or not. I can create a .VI file for them to upload proper settings themselves.


    What is indicates this information?

- 2) General

2-1) Burden impedance synch; Provide information to ensure the SEL-351S input impedance (included tested input impedance value on the report) matches the secondary load of CT.  
- Provide production reports

2-2) Magnetization curve; Have been verify the CT saturation point which does not exceed the SEL-351S protection range?
- Provide ratings for CT's we provided

2-3) Open circuit risk (2, 3 connection); Provide information if secondary terminals are left unloaded, potential high voltage risks.
- check top level drawing/generic

2-4) CT ratio setting; Provide information 1000:1 ratio is correctly programmed in the SEL351S.
- show screenshot of setting

2-5) Fault detection logic (51, overcurrent); Provide test trip operation and what multiple value applied from the rated current?
- Simulate in lab

2-6) Fault detection logic (50G & 51G); Validate minimum trip current and time delay settings.
- Simulate in lab

2-7) Circuit breaker response; Provide and confirm the trip signal to breaker response time deviation. (Recommend 20ms below)
- Simulate in lab

2-8) Communication restoration – During DNP error and fixing occurred, whether the protocol session auto reset and DNP data transferring stably synchronized. (Have you generated the report by event log?)

2-9) DNP Data mapping – Given set value (AI/AO, BI/BO) information for transferred DNP data is not verified to be properly loaded during FAT.
- Show DNP map in as shipped program?