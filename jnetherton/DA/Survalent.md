default username/password is scada/scada

- Must have ADMS open for SmartVU to run
	- Use `localhost` under server setup in ADMS
	- In SmartVU folder (`C:\Program Files (x86)\Survalent\SmartVU`) open `svsetup.exe` to change where SmartVU is looking (use `localhost`)
- Must also change database to point to the correct location in server setup of ADMS manager

Important Folders:
- `Survalent\SmartVU\Standard`
- `Survalent\ScadaServer\Database`

Control Panel
- To place on map, place any pmacro, then change `Dialog Code` to `(1) Control Panel`, then change `Control Panel File` and `Images`  and `Alarm Images`
	- Also change `Point Id 1` to proper station
- While editing:
	- to change control panel background, go to `Map Properties` (top left) and change `Image`
	- For each element, rather than `Point Id`, use `Control Panel Pt Name` to route proper status (does not specify station, but station will be specified on the map itself)
- To have a pushbutton route to a specific control panel:
	- In pushbutton PMacro settings, edit `Menu File` and navigate to the proper `.cplt` file (may have to change folders)

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