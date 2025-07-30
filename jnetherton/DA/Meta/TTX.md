


---
WEEK OF 3/31

DONE:
- local/remote labels at C02/C03 (C03 already was fine)
- standalone labels fix at E01 (not TLED), ADM, and MCUP1
- pushed new settings to MCUP1
- checked C06 for short, verified it's on the customer side
- checked all comms:
	- D02/03 comm A fail
	- MCUP4/5 comm B fail
	- B08/09 comm b fail
- L3 Cx
	- ADM
	- D08/RD01
		- full L3
	- D02/D03
		- full L3
- Uploaded updated RTAC configuration and graphic settings for both yards
	- Did not change the processing cycle intervals

---
WEEK OF 8/4

Rosendin (REI)
BVPI

On patch panel in MVS:
- 1 - HMI
- 2 - COMMA
- 3 - COMMB

VS - VACUUM SWITCH (PRESSURE)
LL - LIQUID LEVEL (LOW OIL)
LT - LIQUID TEMP (HIGH TEMP)

- For template, read a couple with the template and see if things match (rounding errors and missing settings are ok to see). If they match, we can save time by not sending again at the end, assuming the compare looks good also
- Need to operate all ways (including load breaks)
	- issue is always close to open and when it's hot (we'll still test at normal)
	- moto
	- lots of resistance - when you think it should flip over, it doesn't
		- about halfway, you'll hear a click if it's gonna have issues
	- it's not the purpose of my visit, and I'm not the subject matter expert
	- If everything is good, don't mark on the check sheet
	- If something is hard to operate, make a note
	- If something isn't operating, make a note and we'll send to quality

- Change labels for standalone switch

RTAC
- 1.1\program developemnt\RTAC and HMI\...
	- update firmware like normal
	- update runtime
		- hit button next ot push button
		- go to "upload hmi runtime binary" tab
		- choose file to upload
- open newest rev of diagram builder file (rev 2 currently) and send
- 192.68.3.2 (front port)
- IP setup
	- upstream IP in RTAC program to be pushed
		- use EPMS SERVERS.txt in building 1 folder for these IP's
		- Don't touch the HMI or DCIM connections in the program when editing IP's
	- IP of RTAC itself
		- check building 1 folder for FDM file for RTAC IP's
			- ![[Pasted image 20250729101218.png]]
		- .192 is /26 for subnet mask
- Change HMI timeout to 0 on front page of web HMI
- Assigned default page to HMI diagram

SETTINGS READ:
- For each data hall for the first couple or so, read with the template and see if there are any differences
	- There may be rounding differences, but those are ok. It should be obvious if there are differences we don't want


To edit PTX or source breaker names:
- right click tag button
- property substitution window
- collapse them all to make it more readable
- open the Name: label
- edit text as needed
- for which loop column you need, reference ComPort to FieldDevice excel sheet in the TTX folder


- Maybe have techs start going through
- Needs tech names and contact info to enter into orientation spreadsheet
- 2EY1.MVS.H01 - potentially do L2 as it was RMA'd and will be set in place maybe 8/13