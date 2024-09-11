default username/password is scada/scada

- Must have ADMS open for SmartVU to run
	- Use `localhost` under server setup in ADMS
	- In SmartVU folder (`C:\Program Files (x86)\Survalent\SmartVU`) open `svsetup.exe` to change where SmartVU is looking (use `localhost`)

Control Panel
- To place on map, place any pmacro, then change `Dialog Code` to `(1) Control Panel`, then change `Control Panel File` and `Images`  and `Alarm Images`
	- Also change `Point Id 1` to proper station
- While editing:
	- to change control panel background, go to `Map Properties` (top left) and change `Image`
	- For each element, rather than `Point Id`, use `Control Panel Pt Name` to route proper status (does not specify station, but station will be specified on the map itself)
- To have a pushbutton route to a specific control panel

For Custom Dialogue Boxes:
- Add a command-state strings under point resources in STC explorer
- 

angle symbol:
∠

If having issues with ADMS manager on local PC:
- hold ctrl + shift and left click the time at the top
- Disable OTS, OMS, and QAS, then restart server