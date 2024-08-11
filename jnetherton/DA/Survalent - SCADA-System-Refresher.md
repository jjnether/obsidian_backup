Setup:

-   Run ScadaFireWall.bat and ScadaAdvFireWall.bat in the ScadaServer folder
-   Exclude Survalent folder from Windows Defender
-   Database folder can be named anything, but make sure STC Explorer is pointing to it
-   Prior to 21.3, folder path is ...ProgramFiles(x86)quindar...
    -   Otherwise, it's ...ProgramFiles(x86)Survalent...

SCADA - Supervisory control and data acquisition

SCADA Server - Hardware where software is stored
-   It stores the data into **[one database]{.underline}**
-   Every machine can have its own graphics
    -   Can use reservation function to synchronize standard folders

OMS - outage management system

Important to have regular database backups

-   ADMS manager can be running for this backup utility
-   Standard folder not backed up with this utility
-   Just select backup in STC Explorer, then select the folder where backup will be located

SmartVU

-   It's the ADMS graphical user interface for Survalent
-   Operates as a client to the ADMS active host
-   Uses local copy of the map on which it overlays dynamic analog and status data
-   Operator actions are forwarded to the host computer for execution
-   Port 23600 between host and smartVU must be open (see in bottom left of smartVU)
-   Can import CAD files (DXF, DWG)
    -   Tools > Import > Import from DXF/DWG > Run
    -   Open file > save as > merge into current map (or save map), then exit the tool
    -   If you can't find map, query a text or find a new map view
-   To open a new map:
    -   Editor > Library > Map
    -   100k is most used

```{=html}
<!-- -->
```
-   Fonts
    -   Library > new font > edit/save
-   Colors
    -   Library > new color
    -   Can select multiple colors for blinking between them
-   Color table
    -   Used to define colors for each state of a point
-   Symbols
    -   Drawn objects that can be grouped together to represent a device
    -   Can be hand drawn images or stored images (but saved as a symbol
    -   Can be used with a p-macro





STC Explorer (Survalent SCADA explorer)

-   Default login is (scada, scada)
    -   Permissions based on your login credentials
    -   Built-in users (guest, admin, scada)
    -   If you lose access to the system, tech support can help change back to scada, scada
-   Used to create, edit, and maintain the database
-   Run multiple instances at once
-   Access control
    -   Can add/edit users and user rights
        -   Privilege Mode
            -   Can check for user, and these users are the only ones that can use operations marked as privilege
        -   Control password - if active, user can't enter control without this password
    -   Access settings - Edit password and login requirements
    -   Zones
        -   Intended to represent areas of responsibility
        -   128 individual zones
        -   Organized into groups
            -   Groups can contain 1 or more zones
            -   A zone can be a member of one or more zones
        -   Users can be assigned to zone groups
-   Point Resources
    -   User Point Types
        -   Intended for grouping status and analog points by function or data type
        -   Useful for reporting
        -   Related to the way you want to pull data from SCADA for reporting
    -   Command -State Strings
        -   Text strings that represent the commands that can be sent out to a controllable device , and feedback states
        -   All Status Points use command/state strings to define strings to display their state and identify the commands that can be issued
        -   Commanding out, you can only have 2 states
        -   For the feedback state strings, you can have up to 4
-   RTU - Remote Terminal Unit
    -   Device that's designed to accept status and analog data
    -   An element in the database that represents a physical RTU/IED that is connected directly to the communication line.
    -   Has an associated link status point that the scan task uses to tell you it's communicating with the physical device.
-   IED (intelligent electronic device) Wizard
    -   A tool that automates the creation of the database for an IED
    -   Master - attached directly to the communication line (has IP address to talk to other devices)
    -   Slave - attached off an RTU (no IP address, RTU handles IP address info)
    -   Be sure that STC Explorer has the proper template path for IED templates folder
    -   If device has no ip address and only DNP, RTU should be able to handle it (it will have the DNP memory map and an ip address to connect to the host)
    -   Default DNP port is 20000
    -   When editing IED points, be sure the command-state string you use exists in database
-   Station
    -   Logical grouping of points for the operator
    -   Link Status Points
        -   Pseudo point type for health monitoring
        -   Allows you to monitor connection status
        -   Required for the creation of communication lines/RTU's/DE servers
        -   Good practice to have all pseudo points in one station

    ```{=html}
    <!-- -->
    ```
    -   Analog Points
        -   Support alarm limits
        -   Optional limits:
            -   Pre-emergency
            -   Emergency
            -   Unreasonable
        -   Deadband - absorbs chatter in a band

```{=html}
<!-- -->
```
-   Automation
    -   Calculations - be sure to update and commit
    -   Templates
        -   Controls can be blocked at a point level, if certain user defined conditions match
        -   To use a template, select it in permissions under telemetry, then fill out the proper fields
    -   Command Sequences
        -   Uses a programming language that is specifically designed to be used with SCADA systems.
        -   The programming environment allows you to define and execute programs that use database points as variables.
        -   Can be used for calculations, open-loop control or closed-loop control.
        -   ! Is a comment
        -   Good idea to add at least 1 delay (or wait?), sometimes more for troubleshooting
    -   Group Controls
        -   Mix analog and status points in one view
            -   Open group control in SmartVU - Operations Menu
-   Communication Lines
    -   An element in the database that represents the medium used to communicate with RTU(s) or Master IEDs
    -   SCADA Host runs a separate scan task for each communication Line
    -   Use Scanx for telemetry when doing simulation (not DNP)
    -   Be sure to stop/start scan task to restart comms when editing
-   Reports
    -   Generic - reports use a database to feed the information into a report
    -   Historical
    -   To do reports from a shared drive, must edit Survalent SCADA service so that it is run as a specific user rather than LocalHost
    -   Operation Log
        -   Annotate logs and add them to summary
        -   You can print only logs added to summary with "print only selected records"
    -   Events - statuses where you checked "Event Data Recording"
    -   SOE (Sequence of events) (separate application)





Status Point Viewer

-   Set manual - right click and hit this for manual operation of a point
    -   Can set permissions for each point to specific zone groups

Analog Point Viewer



Alarms

-   Alarm format
    -   Format strings that specify what an alarm should look like
    -   Controls the way alarms are being displayed in SmartVU
    -   Priority is from 0-10, with 10 being highest priority (will show first in alarm review)
    -   Format01 is the most common alarm format used
    -   Remote alarms (for SMS and email)



P-Macros

-   Utilizes fonts, colors, and symbols to dynamically enhance the map
    -   Link Point ID 1 to device property
    -   Status symbol - simulating a device such as a Circuit breaker
        -   Symbol (or alarm) 00 - open state
        -   Symbol (or alarm) 01 - close state
        -   Reduced flag scale factor to 0.1
        -   Flags
            -   Alarm
            -   Condition
            -   Tag
    -   Pushbutton - can produce a report, graph, run/stop an application, etc..
    -   Analog Value - display colors, values, and more....
        -   Use precision for number of decimal places
    -   Image - needs jpeg file
    -   Pushbutton Symbol
        -   Data name 1
            -   Must exactly match name of what it's being linked to (map view name for view)
        -   Data Type (view, graph, reports, etc.)
        -   Dialog Code
        -   Menu File (for reports)
            -   Points to file (.csv)
    -   Time Value

Control Panels

-   It's a tool that allows you to populate a substation drawing with all of the IED's points in just a few keystrokes
-   P-macro > Station Image
    -   Alarm Images
    -   Control Panel File (ZIP file)
    -   Dialog Code (control panel)
    -   Images (00 is the first you see)
    -   Scale Factor x,y (see width and height of BMP file

**Comm lines**

![Machine generated alternative text: scan task performs regular round-robin polling time to wait between each poll time to wait for each valid frame of the response from the RTU Time to wait for a socket connection on TCP/IP n orks how often the scan task is to interrupt its round robin polling to perform a fast-scan poll Communication Line General Connections DNP Statistics Name LinkStatus COMMUNICATION.COM STATUS 1 1 Protocol Connection Mode Poll Time Between Scans, msec Short Response Timeout, msec Long Response Timeout, msec 011 Short Response Ti ok;d DNP 3.0 Use RTLI Settings All Data, sec Accumulator, sec Hourly Offset, sec x ok;d Oil esponse Timeout, msec Poll Retry Count Interleave Factor Idle Time, msec Error Recovery Time, sec Apply Defaults Demand Average Interval, sec Time Sync Interval, sec o start automatically when the SCADA system starts up How frequently you want integrity polls on this communication line. minimum time to wait, in milliseconds, between consecutive polls Confidential & Proprietary Display Extra Configuration Switches ](DA-SCADA-System-Refresher-image1.png){width="17.635416666666668in" height="5.333333333333333in"}



**Status points**

![Machine generated alternative text: used to prevent normal operators from manipulating the It shows that this point is used by a line section. When an anti-chatter filter goes into effect, an alarm is raised St Rus Text RTU_I Status Point Telemetry Aams Stafon user Tyr Device Class Zone ro Command-%te Anti-Chatter Filter Bay Lockout Point Lockout Timer. sec SUB_I Tie Swich Switch Mon-a-lary OpenCJose <None> <None> Name Tie Switch C) Privilege Mode Disturbance O Utöge e scs Enabled C) NO Manual Set Flag Event Data Recording O SOE Event C) No Redundant Controls C) Control Password Required Anti-Chatter Filter Type Lint Of In se TEST Tun Tun Ch ctkw> [S •ave OER OER OER Save JED, Pod C) Can be controlled by Bay CJ Auto Select IJn-Commanded Changes for Summary Reports C) Do not alarm states 2 and 3 on control operations OK 2 Existin Point The SCADA system contains a breaker lockout detection function Setting this flag will enable Event Data Recording for this point. Each change of state will be stored in the event data file If flag is set, the SCADA system will be illing to receive and store timestamped sequence-of-events data for this point you will not be able to issue redundant controls to this point (i.e. send an Open command to a point that is already open). Confidential & Proprietary ](DA-SCADA-System-Refresher-image2.png){width="15.927083333333334in" height="7.114583333333333in"}



**Time Format**

![Machine generated alternative text: ode a b B c d H m 0M w w x x ut ut Current 10 ed-in SCADA user name bbreviated weekda name Full weekda name bbreviated month name Full month name Date and time re resentationa ro riate for locale Da of month as decimal number 01---31 Hour in 24-hour format 00--- 23 Hour in 12-hour format 01 --- 12 Da of ear as decimal number 001 --- 366 Month as decimal number 01 --- 12 Minute as decimal number 00---59 Current locale's A.M. P.M. indicator for 12-hour clock econd as decimal number 00 --- 59 eek of year as decimal number, with Sunday as first day of eek 00-53 eekda as decimal number 0---6' Sunda is O eek of year as decimal number, with Monday as first day of eek 00 --- 53 Date re resentation for current locale ime re resentation for current locale ear without centu as decimal number 00 --- 99 ear with centu as decimal number ime-zone name or abbreviation; no characters if time zone is unknown Percent si n ](DA-SCADA-System-Refresher-image3.png){width="8.229166666666666in" height="8.59375in"}



