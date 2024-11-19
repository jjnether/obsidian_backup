Original - SA# 112388

RTAC - GWELECTRIC/GWLazer1!
Moxa - admin/moxa
- 192.168.127.254

Protocol Settings - Protocol conversion
- Bacnet/IP client --> Agent --> Modbus TCP Server

Modbus TCP Client Settings
- Choose file and import

I/O Data Mapping
- Should show modbus register converted to bacnet - just use to confirm settings

Protocol Status
 - For troubleshooting
 - Go into Modbus TCP traffic
	 - prove modbus is talking to the Mgate

Mike

Switch 1 - 10.31.8.61 - retrofit on 11-19-24
Switch 2 - 10.31.8.62
Switch 3 - 10.31.8.63
subnet (all) - 255.255.254.0
gateway (all) - 10.31.8.1

Relay IP - 192.168.1.2
RTAC IP (switch 1)
	port 2, incoming - 192.168.1.101
	port 1, outgoing - 10.31.8.183

