
Default Database Login:
-   User: admin
-   PW: TAIL

Default Username and Password:
- User: SEL
- PW: SEL
- 172.29.131.1 (USB-B port for RTAC 3505 and axion 2240)
- ETH 1: 192.168.1.2
- ETH 2: 192.168.2.2
- ETH 3: 192.168.4.2
- ETH F: 192.168.3.2

Meta:
- User: GWELECTRIC
- PW: GWLazer1!

**NOTE**: First time boot of RTAC, you have to go to webUI to set first time username and password

- IP in relay port parameters is IP of relay itself
- IP in relay protocol parameters is IP of client port (RTAC)
	- Connect to RTAC web interface and edit port with proper IP
		- Don't set as primary connection
		- use /24 for subnet mask (if using 255.255.255.0)
- DNP address in relay settings is DNP address of the relay (server)
- REPDNP address in relay settings is DNP address relay reports to (RTAC, client)

F6 TO SET
SHIFT + F6 TO RESET

Data within the RTAC are referenced by database points called tags that may be associated with client or server protocols, system values, global variables (including virtual tags), or values created in user-defined logic.



Axion Bay Control
-   Can pick as many as 30 screens through which the display can rotate
-   When Mode is set to CONTROL, the element's control tags are available in the RTAC logic engine and the status tags are available for mapping to Boolean expressions or tags.
-   When Mode is set to MONITOR, only the status tags are available for mapping to Boolean expression or tags.



SPS - single point status
CMV - complex measured value
.stVal.0 - accessing 0th bit of a register
OR_SPS - or 2 bits together
stVal - value
q - quality
t - time

SR has no 52B status while yellow handle active

![|500](DA-RTAC-image2.png)

MODBUS Datatypes
- Discrete Input type SPS - binary value 0/1 (reading)
- Holding registries - 16bits of data for analog values (reading)
- Input registries - 16 bits of data for writing
- Coils are commands to the relay

https://www.calculator.net/ip-subnet-calculator.html
- IP Subnet Calculator

TCP references ethernet
RTU (remote terminal unit) normally references serial

Function - a routine that a program or calling logic block can call to perform repetitive tasks.
Function Block - a routine for which a program or calling logic block can have definitions for multiple instances to perform specific tasks. Each instance is unique and separate.
- Function block instances retain any values they use. This makes function blocks unique from functions. For each use of a function block instance, the instance updates values according to inputs and previous results.

Enable FASTOP in relay port settings to allow the use of Remote Bits from the RTAC