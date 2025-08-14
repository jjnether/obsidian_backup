


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
		- hit button next to push button
		- go to "upload hmi runtime binary" tab
		- choose file to upload
- open newest rev of diagram builder file (rev 2 currently) and send
- 192.168.3.2 (front port)
- IP setup
	- upstream IP in RTAC program to be pushed
		- use EPMS SERVERS.txt in building 1 folder for these IP's
		- Don't touch the HMI or DCIM connections in the program when editing IP's
	- IP of RTAC itself
		- check building 1 folder for FDM file for RTAC IP's
			- ![[Pasted image 20250729101218.png]]
		- .192 is /26 for subnet mask
- Change HMI timeout to 0 on front page of web HMI
- Assign default page to HMI diagram

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

Secondary Injection
- Voltage 3.38V - 
- Current .03A - 

NOTE:
- Observed that if there's a COMM A failure but COMM B is working and you try to test auto mode, when you send a command to kick it back to manual (either PB or remotely), it will give an auto failure. However, it does not do this if there's a COMM B failure, but COMM A is functioning (so we tested by just swapping A and B)
	- This is a hole in the logic, but talked to Bob, and we'll probably leave it as it's an edge case and not harmful
- MCUP7 and MCUP8 - test set was injecting lower and fluctuating values - couldn't get it working, so just looked for the right phase with voltage, then moved on