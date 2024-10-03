
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\Camp Humphreys (KK Interlock) - 111321>)

351 PN: A1341359YM0

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
- 50P1P = 4.9 (2450A)
- 67P1D = 2 cyc
- ==50G1P = .58 (290A)== - inject 300A
- 67G1D = 2 cyc
- ==51P1P = .55 (U4) (275A)== - inject 375A L-L (39.79s)
- 51P1TD = 6
- ==51G1P = .23 (U4) (115A)== - inject 200A (2.84s)
- 51G1TD = 1

- 51 = 600A E SPEED SLOW
- ==51N = 30% E SPEED SLOW (180A)== - inject 300A
- INRUSH = X5
- PHASE INRUSH RESTRAINT TIME ADDER = 1.7 s (asked for 1.75)

Question:
- Inrush timer only allows for 1 decimal, do you want 1.7 or 1.8? (asked for 1.75)

MOVE ELLIE'S TABLES


Notes on improvements for control cabinets:
- Power supply difficult to access due to ethernet switch being mounted on left wall and blocking it
	- Ethernet switch used to be mounted to swing frame, maybe better?
- Heater next to batteries - maybe not ideal as it would heat the batteries
- temperature and fan control are further to the back wall - makes it difficult for technician to see the setting and change it without putting their head inside the control cabinet
- Big concern is technicians putting their heads inside the control cabinets
	- are shallower control cabinets possible?
- OSHA standards??? - NEC70 OSHA