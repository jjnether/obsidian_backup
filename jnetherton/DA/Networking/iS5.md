Default IP: `192.168.10.1`
Username: `admin`
PW: `admin`

MicroRaptor iMR320
- To change device IP: Layer 3 Management -> IP -> IPV4AddrConf
	- Put in new IP and subnet, then hit modify
- To add static VLAN: Layer 2 Management -> VLAN -> Static VLANs
	- VLAN ID is the VLAN tag number
	- Add a name for the VLAN
	- Add necessary member ports
- To save config settings: System -> Save & Restore -> Save
	- Use Flash save and hit apply