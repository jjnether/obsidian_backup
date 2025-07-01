
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\120881 - Bauxite (Bretco)>)

POD - 95975

D94980182AYN
D94980182AYP
- A13413591HX0 - relay
- 045152111C0X1H741412X


IS5 Microraptors:
- username: GWELECTRIC
- PW: GWLazer1!
- customer username: BAUXITE
- customer PW: Bauxite1!


inject:
- 3.984 V (19.918 kV)

iS5 CHANGES:
- SS1 IP: 192.168.10.21
- SS2 IP: 192.168.10.22
- Static VLAN:
	- Ports 1,2
	- 44

CLARIFY in manual that they can manually parallel if they close all the motors then close the manual tie


COMMISSIONING:
- Talked to Zach in person
- Batteries were put in the switches
- Was given SFP's to install
- No comms up yet - will have to advise them on setting up the managed network switches in the future
- Talked to Robert? with capital electric - relay guy
- Additional external CT's on both Way 2 - 100:1 - will program relay with proper CT ratio just for metering
	- low load on each switch, so low CTR shouldn't be a problem
- Will make sure protection elements are disabled in relays - no fault interrupters on source/tie ways

Things for customer to note following commissioning:
- IP addresses (relay and GOOSE) and settings in managed ethernet switches
- Automation timings (initial/return transfer timers)