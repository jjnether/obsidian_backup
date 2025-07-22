default username/password is scada/scada

- Must have ADMS open for SmartVU to run
	- Use `localhost` under server setup in ADMS
	- In SmartVU folder (`Survalent\SmartVU`) open `svsetup.exe` to change where SmartVU is looking (use `localhost`)
- Must also change database to point to the correct location in server setup of ADMS manager
- Run SrvAdjust in ADMS Manager after replacing server
- When setting up a server (especially redundant), be sure to run the two firewall batch scripts in the ScadaServer folder

Licensing
- Under Server setup, make sure license key is correct
- Under license manager, for USB dongle, you need to generate update request, send to survalent, then process update reply from them

Important Folders:
- `Survalent\SmartVU\Standard`
- `Survalent\ScadaServer\Database`

Use status point viewer application for troubleshooting

DNP setup:
- Set Address under General in RTU to the relay's DNP address
- Set Host Name under Connections in RTU to Relay IP
- Set Master Number under DNP3.0 in Comm Line to the DNP address you want to set for the master device (PC you're on)
- In Relay, set the DNP IP address (address for the client) to your PC IP

Control Panel
- To place on map, place any pmacro, then change `Dialog Code` to `(1) Control Panel`, then change `Control Panel File` and `Images`  and `Alarm Images`
	- Also change `Point Id 1` to proper station
- While editing:
	- to change control panel background, go to `Map Properties` (top left) and change `Image`
	- For each element, rather than `Point Id`, use `Control Panel Pt Name` to route proper status (does not specify station, but station will be specified on the map itself)
- To have a pushbutton route to a specific control panel:
	- In pushbutton PMacro settings, edit `Menu File` and navigate to the proper `.cplt` file (may have to change folders)
- To add multiple stations (up to 4) to a control panel (or template):
	- add each station name to each point id (or control panel pt name for templates)
	- inside the control panel (or template), list the name of the point in the control panel pt name as usual, but now put a prefix referencing which station
		- ie. #2,IN101 - this is for the station listed in point id 2

For Custom Dialogue Boxes:
- Add a command-state strings under point resources in STC explorer
	- Commands are the pushbuttons
- In STC explorer, go to the station for the specific way, locate the proper status and edit
- Select the proper command-state you just made
- Update telemetry as needed

angle symbol:
∠

If having issues with ADMS manager on local PC:
- hold ctrl + shift and left click the time at the top
- Disable OTS, OMS, and QAS, then restart server

Simulating
- Force scanX in ADMS manager to simulate telemetry
- Can use command sequences (STC explorer - automation) to simulate values for analog/digital points
- Can set analog point by selecting analog value and hitting set manual
	- Hit activate to get rid of `M` (in production setting, activate will ask field for the new value)
- For alarms, hit the analog point, then properties and ensure alarms are enabled
	- Can set limits with the limit button after hitting the analog point

IED Wizard
- Need to set template path from STC Explorer>File>Application Preferences
	- templates can be created with the template application (open from inside the template folder)
- Before creating new IED, ensure station structure is made (create all levels of stations except for the specific IED)
	- I.E.
		- Camp_Carroll
			- PMS_SD-10
				- <here's where the new IED will go>
- To create the IED (bare minimum):
	- right click in the comm line you it will reside in, then hit New IED
	- Select Manufacturer, Device, and Version (all should be controlled by the templates)
	- Input the new station name, put AllZones for Zone group, and select the parent station (the station where this new station will reside)
	- Hit next, then put in an address for the DNP for this device
	- Hit next twice, then put the device IP in host name and the DNP port to be used (20000 by default)
	- Hit Save IED

For Survalent Sales support: Anjali Mittal amittal@survalent.com