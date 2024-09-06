- Must have ADMS open for SmartVU to run
	- Use `localhost` under server setup in ADMS
	- In SmartVU folder (`C:\Program Files (x86)\Survalent\SmartVU`) open `svsetup.exe` to change where SmartVU is looking (use `localhost`)

Control Panel
- To place on map, place any pmacro, then change `Dialog Code` to `(1) Control Panel`, then change `Control Panel File` and `Alarm Images`
	- Also change `Point Id 1` to proper station
- While editing:
	- to change control panel background, go to `Map Properties` (top left) and change `Image`
	- For each status symbol, rather than `Point Id`, use `Control Panel Pt Name` to route proper status (does not specify station, but station will be specified with the PMacro on the map itself)