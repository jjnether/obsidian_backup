OSI Model
- 7 layers of networking
	- 1. Physical
	- 2. Datalink Layer
		- Introduces MAC (Medium Access Control) Address
			- 48 bit address given to each physical network interface
				- first 24 bits define the device's manufacturer (OUI)
				- last 24 bits are specific to the physical network interface
			- There are special MAC addresses reserved for specific applications:
				- True source is almost always true source, but you'll see GOOSE group as destination
				- GOOSE multicast
				- RSTP
		- Devices that read MAC addresses and facilitate communications within the same subnet are "switches"
			- managed and unmanaged
		- GOOSE never gets to layer 3, just sees every device on a big network
			- Unless you have routable GOOSE, if you want it to go between networks, you have to wrap it (maybe a tunnel)
				- GRE - tunnel protocol, really good for layer 2 stuff
	- 3. Network Layer
		- This layer deals with inter network communication or end-to-end
		- Internet Protocol (IP) addresses
			- four octets
			- private addresses can range from:
				- Class A: 10.0.0.0 - 10.255.255.255
				- Class B: 172.16.0.0 - 172.31.255.255
				- Class C: 192.168.0.0 - 192.168.255.255
		- Subnet Mask
			- four octets
			- ranges from 255.0.0.0 - 255.255.255.255 (CIDR = /8 - /32)
		- Default Gateway
			- device responsible for connecting two networks
			- a local host trying to communicate to a different network will send it's traffic to its default gateway
				- (if I don't know where to go)
			- best practice is first or last number in range (.1 or .255)
	- 4. Transport Layer
		- Deals with service-to-service network communication
		- oversees the session requirements of a communication link and determines what services are being requested
		- devices that read port numbers and direct communications to different services are called "hosts"
		- by using a source and destination port, the session is directed to the appropriate service within the host
		- services use ports by one of two protocols
			- Transmission Control Protocol (TCP)
				- establishes connections via handshakes and acknowledgments
				- more reliable, but slower
				- HTTP/HTTPS/MODBUS: 80/443/502
			- User Datagram Protocol (UDP)
				- rapid fire information, doesn't wait for acknowledgement
				- quicker, but relatively less reliable

IT - enterprise
- sometimes administrates/has responsibility of OT networks
- networks don't necessarily need 100% uptime
- firmware updates tends to be prioritized
OT - where the equipment goes
- less PC, and more stuff
- something that has a physical job (not a laptop/server/printer)
- focuses on reliability/uptime
- factory setting

Layer 2 Features
- VLANs
	- 2 byte tag inserted into packet and EthType adjusted
		- tag defines VLAN ID & quality of Service traffic priority
			- QoS relevant when netowrk very congested
			- "Fast pass" to cut to front of buffer / queue
		- End devices don't "process VLAN tags"
			- switches do and forward packets to member ports as needed
		- ports can be members of multiple VLANs, but their traffic gets tagged by only one when entering switch
	- useful for:
		- organize end devices
		- segment your network (when used in L3 device)
		- manage traffic / broadcast/ multicast
		- Implement QoS / traffic prioritization
	- never designed as a security tool
	- not great in OT unless you understand them and know what they are NOT
		- good in IT
	- (at layer 2)
		- logically groups ports on the switch into separate LANs
		- communication between VLANs is not possible unless a router is present
		- extremely important to have a well thought out VLAN plan in electric power applications
			- EP7400 has VLAN as a core configuration component
	- (at layer 3)
		- VLANs part of layer 2 portion of packet, but used for layer 3 applications
		- on routers, interfaces are assigned VLANs
		- VLAN routing then setup
		- easy way to group ports in order to:
			- assign DHCP addresses
			- setup routing tables
			- access security features
			- implement firewall access control lists

Redundancy mechanisms
- RSTP
	- IT friendly, widely adopted, very interoperable
	- lower priority is stronger
		- physical port number is considered as a fallback when looking at where to break at the device itself
	- good for SCADA
	- maybe not good for blocking
- MRP
- DLR
- PRP
- HSR
	- 0 down time
- VRRP

Layer 3 Features


Naming:
- 6xxx = din mounted
- 7xxx = rack mounted
- x4xx = standard
- x5xx = extra firewall features