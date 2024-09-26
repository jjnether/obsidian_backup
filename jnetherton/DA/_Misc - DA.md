Office Phone: (708) 297-3769
Work Phone: (708) 402-8777

`U:\_ISO\GWI\523\GWI523-369CD.zip`
- Motor programming cable driver

`X:\SWG_Eng\EE Folder\Product\SEL`
- Part number is relay part number in control BOM

`X:\DA\Dept\_Lazer\_SEL EDITABLE FACEPLATES`
- SEL Editable Faceplates (labels)

$V_{L-G} = \frac{V_{L-L}}{\sqrt{3}}$
$\sqrt{3}=1.732$
Internal PT's always have a fuse
System voltage is typically given as L-L
PT ratio applies to L-G - should get 120 VAC
CT dot should be on the incoming side

LEA PT is typically 10000:1 ratio, but LEA voltage inputs are detected at an 8:300 ratio. So total PT ratio for VS is     $266.66 = (\frac{10000}{1})(\frac{8}{300})$    OR      $133.33 = (\frac{5000}{1})(\frac{8}{300})$
- For 751's, it wants the actual PT ratio (10000 or 5000)

![Machine generated alternative text: Capacitive voltage divider Cable SEL-651R VY or VZ-terminal voltage input (8 Vac LEA input) ](DA-Misc-image1.png)

**SEL terminal commands:**
(SELboot) `FID` - check SELboot and firmware
`VER` - check version
`STA` - check relay status
`STA S` - check execution capacity
`MET` - see all status
`TAR <wordbit>` - see bit status

**For 651:**
`CON <#>` - connect to remote bit
`PRB <#>` - pulse remote bit

**For 751:**
`CON RB<nn> <k>` - connect to remote bit, where k is S, C, or P for Set, Clear, or Pulse
`PUL <n> <t>` - pulse output contact n for time t

Z = vertical bushing (usually line/source side)
Y = horizontal bushing (usually load side) (ct is always on this side)

**Bypass Mode**
- This mode is intended to be used when device(s) cannot coordinate with the upstream device. In this mode fault targets will be set, but the overcurrent protection elements will be blocked from tripping the recloser.
	- Basically, if two switches are too close to coordinate, one may be in bypass mode

**Hot Line Tag**
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

RTDS - real time digital simulation

Poor Man's Latch:
-   SVXX := {SET CONDITIONS} OR {SVXX} AND NOT {RESET CONDITIONS}

Can use a sequencing timer (AST) as a conditioning timer (ACT) by notting the IN value in the reset equation

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

DESIGN TEMPLATE:
- `UV^******` represents design template variables
	- These can be added and edited from "Manage Design Template Variables"
	- These typically go on the right side in the equation builder
	- e.g. `[S1^51S1TD] = [UV^S1_51S1TD]`
		- `S1^51S1TD` represents the Set 1 51S1TD setting to be defined
		- `UV^S1_51S1TD` represents the variable that will be sent to the setting
- **^****** represents a setting or line of logic that is set to be defined in the template

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

`TRGTR` asserts when TARGET RESET is pushed
`RSTTRGT` is a command that can be sent to reset targets

TCC Curves:
![[Pasted image 20240223151615.png]]

Wiring Statuses:
- SF6 - high when good SF6
- AC Status - high when AC is active
- Battery Alarm - high when bad batteries or no good test yet

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


**IS5 Ethernet Switch Setup**
Default IP: `192.168.10.1`
Username: `admin`
PW: `admin`

Default SEL Relay Port 5 IP: `192.168.1.2`
Default FTP User: `2AC` (or `FTPUSER`)
FTP Password: `TAIL`


Additional Non Communicating Logic To Help Prevent Closing Into A Fault.  It will not preventing closing into all faults (3 phases faults will have to be closed into).
This logic will apply to any device that auto closes.

---
`SET LT01 := SV02T`
`RESET LT01 := SV01T`
`SV01IN := 3P59Y`
`SV01PU := 30 seconds`
- To be 75% of auto close delay time, or potentially 95%.
- Example:  Alternate source is faulted, but line is restored at the same time as the primary is lost.  We do not want the tie auto close to be delayed even further waiting for the lockout from the previous fault to be cleared, or does it not matter?
`SV02IN := (27YA1 or 27YB1 or 27YC1) and not 3P27Y`
- Should the individual phases be under voltage and the 3 phase check be dead?
`SV02PU := 5 cycles`
- Can this be lowered?  It is here to try and account for variation in upstream mechanism not opening all phases/extinguishing the Arc at the same time, but has to be short enough to not be over ridden by a three phase trip operation
---

- If 651 is powered but doesn't seem to be turning on, hit `TARGET RESET` and it should wake from sleep

POTT = Permissive overreach transfer trip
DCB = directional comparison blocking