Office Phone: (708) 297-3769
Work Phone: (708) 402-8777

Siemens Siprotec
-   Modular expansion units
-   Flexibility to only get what you need (save money)
-   Numerical keypad (can configure as pushbuttons)
-   Printer cable to connect to relay
-   Relays that end in 5 or higher are modular
-   Utilities moving towards more centralized protection?
    -   Use single relay for protecting many switches
-   Digital twin - Can test up to 20 devices
    -   Visualize and interact with devices using simulation
-   RTU (remote terminal unit) - SICAM A8000
    -   Can connect with browser or software

`U:\_ISO\GWI\523\GWI523-369CD.zip`
- Motor programming cable driver

`X:\SWG_Eng\EE Folder\Product\SEL`
- Part number is relay part number in control BOM


PT L-G Voltage = L-L/sqrt(3)
Internal PT's always have a fuse
System voltage is typically given as L-L
PT ratio applies to L-G - should get 120 VAC
SQRT(3) = 1.732
CT dot should be on the incoming side


LEA PT is typically 10000:1 ratio, but LEA voltage inputs are detected at an 8:300 ratio. So total PT ratio for VS is `266.67 = (10000/1)*(8/300)`
- OR `133.33 = (5000/1)*(8/300)`
- For 751's, it wants the actual PT ratio (10000 or 5000)

![Machine generated alternative text: Capacitive voltage divider Cable SEL-651R VY or VZ-terminal voltage input (8 Vac LEA input) ](DA-Misc-image1.png)



**SEL terminal commands:**
(SELboot) FID - check SELboot and firmware
VER - check version
STA - check relay status
STA S - check execution capacity
MET - see all status
TAR `wordbit` - see bit status

**For 651:**
CON `#` - connect to remote bit
PRB `#` - pulse remote bit

**For 751:**
CON RBnn k - connect to remote bit, where k is S, C, or P for Set, Clear, or Pulse
PUL n t - pulse output contact n for time t


Z = vertical bushing (usually line/source side)
Y = horizontal bushing (usually load side) (ct is always on this side)


SEL 487E (transformer differential relay) (6 breakers/windings)

(2 ways of voltage, 6 ways of current)


Hitachi REC670
-   Spec
-   Development time
-   Testing time
-   GWI's


#Bypass_Mode
This mode is intended to be used when device(s) cannot coordinate with the upstream device. In this mode fault targets will be set, but the overcurrent protection elements will be blocked from tripping the recloser.
-   Basically, if two switches are too close to coordinate, one will be in bypass mode


#Hot_Line_Tag
- When hot line tag is enabled if any phase minimum pick is exceeded all phases will immediately trip. If ground is not block while hot line tag is enabled exceeding the ground minimum pickup will also cause all the phases to trip. Enabling hot line tag automatically puts the control into one shot mode.


**Order Sequence**
- Business development manager (BDM) (Alex and Tia) provides quote with scope
- Plan and release and release to production (AE and PE)
	- Pick date is when order is done
- Program Spec - due 4 weeks after approval - if it's in ENG or customer approval, we wait - if it's in dating in progress, good to go
- Development time (will make system testing smoother)
- Production Program
- FAT Plan
- System Testing
- FAT
	- Could be from a couple hours to a week
- Commissioning
	- Customer has switch installed (varies)
	- Take FAT plan and rework to SAT plan
- GWI Draft
	- First draft done around time of commissioning
	- Ideally done 2-4 weeks after commissioning



Must enable Telnet in the port setting to communicate with a relay through ethernet

Type 1
Type F Version 1.1 - 487 and rtac - 2 switch loops
Type F Version 1.2 - siemens relays in larger loops (4, 8, 10, and 11) - install 2025
-   Also a centralized controller from siemens

HSR - High speed redundancy
-   RSTP - alternative redundancy

RTDS - real time digital simulation

Poor Man's Latch:
-   PSV01:= {ON CONDITION} OR (PSV01 AND NOT 52A AND NOT SV01T) #
-   SV01 := PSV01
-   SV01PU := 6SEC


---

Looking for options/view points on 1 vs multiple (of the same) relays for a multiway pad mount switch.  We have traditionally (in the Lazer group) been of the opinion that a single relay is the better option.
As I see it ..

Pro (single relay):

- Potentially cheaper
- Typically when setting up P2P scheme it makes writing the logic easier as nothing has to be pass between relays.
- Less points of failure
- Less total power consumption by the control cabinet
- Easier for creating interlocking logic (so as not to over load the power supply running to many motors)
- availability of additional protection/automation features (ie. inherent bus protection, logic to determine bus voltage)
- Less/no networking equipment involved
- Less wiring (power supplies, jumpers, etc.)
- Simpler networking and communications
- Fewer devices to maintain and simpler/more comprehensive logic

Cons (single relay)

- Potentially more expensive (for smaller number of way switches)
- Single point of failure (ie. single relay goes down operation of the whole switch is lost).  I think this is the probably the biggest point of debate.  I can almost see it both ways.  Single relay = less components to worry about, but if it fails it could disrupt/disable the whole scheme (ie. P2P closed loop depending on how it is programmed).  More relays = more points of potential failure, however they are only taking out "single" ways thus an automation scheme might still be able to isolate a faulted section as desired (or at least not have as big of an outage
-  area (if the automation scheme can accommodate a non communicating relay)
- I agree with the single point of failure argument, though the effect may not be much different depending on the scheme.  If an incoming relay fails, the upstream relay needs to trip for a bus fault.  If the load relay fails and the incoming way is a load break, the upstream relay will still need to trip.  Either way you end up with the whole switch deenergized.  P2P logic can accommodate a relay failure in either case.  


When considering the single relay/way option, I think the level of criticality of the loads needs to be balanced against higher maintenance costs and decreased functionality. It would be interesting/helpful to think through scenarios here.

**Production Overcurrent Testing**
.1 pickup
U3
1 time dial
2 time dial
200 A
300 A
400 A

**CSC Rooms:**
CSC 2
Arrends

We have a couple of "standard" Automation Engineer goals that are project related.  Here are some modified versions you should each plan to use  in Cornerstone:
1. Participate or complete 3 FATs/SATs per quarter.
2. Create 1 or modify 2 programs per quarter.

You would also create Agile goals for each quarter for each goal.  The agile goal for the quarter will list the orders/projects you worked on that quarter.

Next year we'll remove "participate" once you have enough of your own projects for which you own the FAT/SAT.

DESIGN TEMPLATE:
- `UV^******` represents design template variables
	- These can be added and edited from "Manage Design Template Variables"
	- These typically go on the right side in the equation builder
	- e.g. `[S1^51S1TD] = [UV^S1_51S1TD]`
		- `S1^51S1TD` represents the Set 1 51S1TD setting to be defined
		- `UV^S1_51S1TD` represents the variable that will be sent to the setting
- **^****** represents a setting or line of logic that is set to be defined in the template

For editing faceplates:
- `X:\DA\Dept\_Lazer\_SEL EDITABLE FACEPLATES`

For commissioning expense reports:
- Change Expense Type to `Field Svc Billable - SWGR [5195]`
- Change Department to `(000000) Operations`
- Change Sub-Department to `(100700) SWITCHGEAR TEAM`
- Project - Paid Field Service

Symbol Shortcuts:
° = ALT+0176
Ω = ALT+8486
® = ALT + 0174

For DA GWI Creation in ETQ:
- New Doc > GWI - Draft
- ISO Controlled > Yes
- Searchable Departments > GWI
- Product Line > GWI LaZer-DA
- Locations > Bolingbrook
- Owner > Kate Cummings
- Wait to place effective date until you're ready to send it through approval process
- Save to generate GWI number, then under Document Body, select GWI template, then download and edit


TRGTR asserts when TARGET RESET is pushed
RSTTRGT is a command that can be sent to reset targets

TCC Curves:
![[Pasted image 20240223151615.png]]

Wiring Statuses:
SF6 - high when good SF6
AC Status - high when AC is active
Battery Alarm - high when bad batteries

---

If you're working with a customer who has had an event onsite you may need to escalate and include Mike Milon and/or John Pederson.
Include Mike Milon if there's any switch damage or potential liability discussions.  If you're in a call, stop the call and reschedule as a Teams call with Mike.  For email, forward the chain or cc him.
Include John Pederson to review any event or program analysis (wave forms, SERs, etc) before sending to the customer.

Just to clarify, if there is switch damage, cc aftermarket for next steps. Bring Mike into the conversation if the customer believes we're at fault or is doing an investigation surrounding the fault

---

To Connect to Printers:
Hit windows key, then type `\\BK-PRINTSERVER`, right click the printer you want and connect (see printer name on each physical printer)

SF6 Ratings:
![[Pasted image 20240702102126.png]]


IS5 Ethernet Switch Setup
Default IP: 192.168.10.1
Username: admin
PW: admin

Default SEL Relay Port 5 IP: 192.168.1.2
Default FTP User: 2AC (or FTPUSER)
FTP Password: TAIL

[S1^TDUR3D]
[UV^TDURD]