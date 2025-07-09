
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\119509 - Elk Grove Village Property>)

Original - SA 109623

Relay IP
- switch 1 - 192.168.1.11
- switch 2 - 192.168.1.12
RTAC IP
- switch 1 - 192.168.1.2
- switch 2 - 192.168.1.3
Ethernet Switch IP
- switch 1 - 192.168.10.1
- switch 2 - 192.168.10.2

RTAC username/pw - GWELECTRIC/GWLazer1!

nominal = 34500/19920

ANALOGS
Voltage (5000:1)
- 3.5 - 17500
- 3.6 - 18000
- 3.7 - 18500
Current (1000:1)
- .10 - 100
- .11 - 110
- .12 - 120

OVERCURRENT
51P - .1 - U3 - 1 time dial
- inject .2/200 - 1.39 s
50P - .97
- inject 1/1000


NOTE:
- double check fault, then manual close, then trying to trip - not tripping?


CHANGES:
- ULTR logic
- disable unused ports on network switch

THINGS TO DO AT COMISSIONING:
- Disable unused ethernet ports on network switch
- RCF's - push new program logic