- Frequency is set to .05, but it won't consistently close unless difference is 0, maybe .01
- For testing ITS, when you lose source you're on, it will still do CBO to alternate even if they are off by phase or angle, because there's no longer voltage on the original source
- As soon as it sees good sync check, it will close, assuming the IT and RT timer has been met

PSV09 := ((25A1BK1 AND PSV49 AND ASV107 AND ASV117) OR (PSV49 AND ASV116) OR PSV48 OR PCT27Q OR (25A1BK1 AND (PLT05 OR ASV068)) OR ASV112 OR ALT01) AND ASV007 OR NOT ASV007 # SOURCE 1 SYNC CHECK CBO CLOSE
- sync check
- S1 rts close
- S1 live
- S2 live
	- or
- S1 rts close
- S2 dead
	- or
- S1 it close
	- or
- close S1 after OBW
	- or
- (sync check
- (local mode
	- or
- remote mode)
	- or
- S2 open
	- or
- test mode)
- sync enabled
	- or
- no sync enabled


S1 RT sync time (time from good sync settings to S1 52A = 1 and S2 52A = 0)

BASE
118.9 ms
119.3 ms
123.3 ms

REV0
204.0 ms
214.9 ms
227.0 ms

May want to test again, looking for only 52A = 1, not also 52A = 0

REV0
205.6 ms
182.6 ms
190.6 ms
