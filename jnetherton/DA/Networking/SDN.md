Software-defined networking methodology and tools
SEL-5056
Jason
OT

Ethernet overview
- ethernet packetizes messages to improve delivery flexibility
- replaces serial
- store and forward of packets eliminates collisions
- device MAC learning optimizes traffic flows

Packetization
- grouping of information into packet that includes overhead and data according to specific protocol, such as ethernet

address----data----checksum

transmissions
- unicast
	- destination address specifies single interface
- broadcast
	- destination address specifies all interfaces within broadcast domain
- multicast
	- broadcast message is selectively received (transmitted to group)

Supported physical switch configuration (topologies)
- These matter, but matter less with SDN
- star
- mesh
- ring

OSI reference model has 7 layers
- top 3 are data side
	- 7 - application
	- 6 - presentation
	- 5 - session
- lower 4
	- 4 - TCP/UDP
	- 3 - IP addressing
	- 2 - MAC, Ethertype, VLAN
	- 1 - physical (copper and fiber)

MAC address
Ethertype
- Controlled by IEEE
- two octet field indicating what protocol is carried in payload

Insertion of IEEE 802.1Q header
- VLAN
- Between source MAC and Ethertype/length
- Class of service
	- "I will try"
	- 
- Quality of service
	- "I will do"
- VLANS are configured and applied differently in OT networks vs IT networks

Layer 3 - IP addressing
- allows ethernet frames to be routed

Directionality
- unidirectional
	- no indication that it ever got to its destination
- Bidirectional
	- there's a handshake

Goose - L2, multicast, unidirectional
MMS - L4, TCP, unicast, bidirectional

When you get to SDN, you have to understand this stuff about the protocols


Traditional networking switches move packets based on MAC addresses of devices
- They learn where people exist on the network based on MAC addresses

ARP - address resolution protocol
- when source and destination are on the same network
- two devices learn who to talk to completely based on trust
- one device receives a packet and says, "who has this MAC address", then another device says "that's me!"
	- Switch learning
		- Mac addresses are used to route frames when source and destination are on same network, as determined by protocol used

Challenges with traditional Ethernet networking
- easy to spoof a MAC address and get in a conversation
- determinism
- redundancy
- resiliency
- modeling/characterization
- control
- performance
- security vulnerabilities

Best effort switch behaviors
- learn by trusting traffic
- flood on unknowns
- broadcast and multicast

Slow Network healing - RSTA
Dropped packets
Challenges of ethernet in OT applications



# OT SDN overview

Remove decade-old security vulnerabilities
- MAC spoofing
- ARP cache poisoning
- Network reconnaissance
- DDoS
- Vulnerable control plane
- MAC flood
- Cloudy data path

Benefits
- Purpose-engineered connectivity
- deny-by-default access controls
- protection speed network healing
- focus on application and service
- staged, tested, and shared network settings
- proactive traffic engineering
- increased situational awareness
- zero trust
- blocked bad packets - in advance rather than hunt them after

# Managing SDN
Commissioning SEL-5056
 - windows or blueframe
 - initial admin account
 - option to lock to network interface

SDN flow match rule
- layers 1-4
- other layers are payload

OT SDN
- match fields
	- match rule based on portion of ethernet packet
- Instructions
	- perform one or more programmed actions
- counters

- Packet enters switch
- switch compares packet to rules
- match found?
	- no -> drop packet
	- yes -> apply actions (add or remove VLAN, etc.) then execute instructions and exit switch

The deeper you match into the packet, the better security you have
- If you have the space, be as detailed as you can

Rate limiting (meters)
- throttle traffic
- might use to watch unplanned traffic on the network
- Not used often

CST - communication service type
- cast type
	- unicast, bidirectional unicast, multicast
- proactive failover
	- enabled or disabled
- setQueue
	- 1-4 (2 by default)
	- This is what SDN is looking for, ignores VLAN priority
- time out
Logic Connections = flows
- Have to have a source and destination device


# DAY 2

Benefits of knowing everything:
- Security breaches
- Reports
- Audits
- Misconfiguration
- Troubleshooting

### Designing network configuration
Hosts
- unique host names
- unique IP addresses
- physical ports and connection style
- host profile name
Topology
- VMs
- How is everything connected?
- Remote networks
Applications
- Which devices are communicating with which devices
- Which protocols are they using?
- How critical are these conversations?
Protocols
- define packet match criteria
	- TCP/UDP ports
	- Multicast/unicast
- Are used to build specific rules
Host profiles
- Explanation of why device exists
- Generic definitions of applications
- Easier expansion of system

### Engineering documentation
Architectural Drawing
DFD - Data Flow Diagram

Network Builder
- Will be absorbed into 5056 in 3.0

Force Host Discovery - Sends out an ARP to resolve a host IP to a MAC address