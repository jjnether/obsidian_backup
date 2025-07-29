


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

- For template, read a couple with the template and see if things match (rounding errors and missing settings are ok to see). If they match, we can save time by not sending again at the end, assuming the compare looks good also
- Need to operate all ways (including load breaks)

Things to check:
- How to handle label inconsistency with MB TLED's if I see them?
- Any Standalone switch label or program updates?
- Any 6-way switch label or program updates?
- Check PTX alarms here?
	- Same PTX alarms for MCUPs?
- How to handle As Left file if we decide template push was good and we don't need to send again?


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
		- Don't touch the HMI or DCIM connections when editing IP's
	- IP of RTAC itself
		- check building 1 folder for FDM file for RTAC IP's
			- ![[Pasted image 20250729101218.png]]
		- .192 is /26 for subnet mask