
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\Camp Humphreys (KK Interlock) - 111321>)

351 PN: A1341539YM0

Kirk Keys:
- TNI
	- Way 1
		- 2 cylinders
		- 1 key can be withdrawn when locked in open position
	- Way 2
		- 1 cylinder
		- key can be withdrawn when locked in open position
- GNI
	- Way 2/3/4
		- 1 cylinder
		- key can be withdrawn when locked in open position

![[Pasted image 20240823151508.png|700]]

8 hour timer for battery
system voltage = 13321V (inject 120.8V)

Protection Settings:
- TNI:
	- 50P1P = 4.9 (2450A)
	- 67P1D = 2 cyc
	- ==50G1P = .58 (290A)== - inject 300A
	- 67G1D = 2 cyc
	- ==51P1P = .55 (U4) (275A)== - inject 375A L-L (39.79s)
	- 51P1TD = 6
	- ==51G1P = .23 (U4) (115A)== - inject 200A (2.84s)
	- 51G1TD = 1

- GNI
	- ==51 = 600A E SPEED SLOW== - reduce to 180A and inject 300A L-L
	- ==51N = 30% E SPEED SLOW (180A)== - inject 300A
	- INRUSH = X5
	- PHASE INRUSH RESTRAINT TIME ADDER = 1.7 s (asked for 1.75)

Notes on improvements for control cabinets:
- Power supply difficult to access due to ethernet switch being mounted on left wall and blocking it
	- Ethernet switch used to be mounted to swing frame, maybe better?
- Heater next to batteries - maybe not ideal as it would heat the batteries
- temperature and fan control are further to the back wall - makes it difficult for technician to see the setting and change it without putting their head inside the control cabinet
- Big concern is technicians putting their heads inside the control cabinets
	- are shallower control cabinets possible?
- OSHA standards??? - NEC70 OSHA


**Punch-list Items:**
- External LED label's that say "Fault Indicator" above lamp for all TNI switches
    
- Low SF6 Pushbutton indicator for all TNI switches
    
- Enclosure spec sheet in each production packet for all switches which show NEMA 3R rating

- Can of touch-up paint for Durham with exact color to ship with switches
    
- T-handles for GNI switches - also includes mounting on swing doors for T-handles
    
- Low pressure warning device added to GNI switches
    
- Scanned FAT report along with overcurrent test reports

- 351 dry contacts for tripping on TNI switches

- Dry contacts for the GNI switches - investigating the spec - will follow up

- Add to the FAT document statement regarding adhering to IEEE standards