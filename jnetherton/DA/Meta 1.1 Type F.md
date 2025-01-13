Number in pair - number 1 in pair will be fed from lower number or letter (MSG-1 vs MSG-2) - other switch will be number 2

OFCI - owner furnished contractor installed
- because this is what our switches are, we shouldn't need a drug test
There will be some changes in compares
- check for protection set point changes
Site should provide IP's for RTAC and modbus servers
Send port 5 settings to enable telnet/FTP, then push file using FTP
- push final port 5 settings with serial at the end?

- Check that feeding breakers and PT names are correct in HMI (labels should be on switch itself)
- Test PT alarms (5) - Normally open - need to jumper to test
timers should be correct values due to relay settings
verify RCF's
Make sure switch 2 is preferred open point

1. Open prepared settings and save updated RCF's
2. Change port 5 to enable FTP
3. Read as found and compare what you're going to send
4. Verify nothing in Set 1 has changed
	1. there will be differences in logic, but Set 1 is the important one to not change
5. Send settings through template (this will disable port 5)
6. Read as left
7. change port 5 back to normal (through template)

A03