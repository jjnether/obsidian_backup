# Design Template

Created: 2023-10-18 09:30:38 -0500

Modified: 2023-10-19 10:34:06 -0500

---

Global

-   System
    -   System Frequency (Hz) **= NFREQ** # (50 or 60 Hz)
    -   System Phase Rotation **= PHROT** # (ABC OR ACB)
-   Current and Voltage
    -   CT Ratio = **CTR**
    -   PT Ratio - VY Terminal = **PTRY** # PT ratio for the Y-terminal voltage inputs (LEA_PT_ratio * 8/300)
    -   PT Ratio - VZ Terminal = **PTRZ**
-   Recloser Wear Monitor
-   Other

Group 1 Settings

-   Identifier
    -   Control Identifier = **RID** # contains the control installation designation. This identifier is listed at the top of event, history, meter, and status reports.
    -   Circuit Identifier = **TID** # contains the greater circuit or substation designation. This identifier is listed at the top of event, history, meter, and status reports.
-   Overcurrent
    -   Minimum Trip - Phase (A, primary) -> **50P3P** (also 50P6P, 51PKP, 51PJP) # minimum phase current threshold for overcurrent detection
    -   Minimum Trip - Ground (A, primary) -> **50G5P** (also 50G6P, 51G1KP, 51G1JP)
    -   Fast Curve - Phase (curve) = **51PJC**
    -   Fast Curve - Ground (curve) = **51G1JC**
    -   Delay Curve - Phase (curve) = **51PKC**
    -   Delay Curve - Ground (curve) = **51G1KC**
-   Reclosing
    -   Operations - Phase Fast Curve = **MV01** # number of phase *fast* curve trip operations
    -   Operations - Ground Fast Curve = **MV02**
    -   Operations to Lockout - Phase = **MV03** # number of *total* phase curve trip operations
    -   Operations to Lockout - Ground = **MV04**
    -   Reclose Interval 1 (sec) -> **79OI1**
    -   Reclose Interval 2 (sec) -> **79OI2**
    -   Reclose Interval 3 (sec) -> **79OI3**
    -   Reclose Interval 4 (sec) -> **79OI4**
    -   Reset Time for Auto Reclose (sec) = **79RSD** # time required to return to the RESET state if the recloser is closed and in the CYCLE state. If a trip occurs while in the CYCLE state, the reset timer is re-loaded and begins timing when the recloser is closed
    -   Reset time from Lockout (sec) = **79RSLD** # typically, the Reset time from lockout setting is set shorter than the Reset time for auto reclose setting
-   Complex Overcurrent
    -   Constant Time Adder - Phase Fast Curve (cyc) **= 51PJCT** # adds a constant time to the phase fast curve
    -   Vertical Multiplier - Phase Fast Curve = **51PJTD** # shifts the phase fast curve in time, by the entered multiplier (time dial)
    -   Minimum Response Time - Phase Fast Curve (cyc) = **51PJMR** # phase fast curve can trip no faster than this time setting
    -   Electromechanical Reset - Phase Fast Curve = **51PJRS** # enables the electromechanical reset emulation
    -   Constant Time Adder - Ground Fast Curve (cyc) = **51G1JCT**
    -   Vertical Multiplier - Ground Fast Curve = **51G1JTD**
    -   Minimum Response Time - Ground Fast Curve (cyc) = **51G1JMR**
    -   Electromechanical Reset - Ground Fast Curve = **51G1JRS**
    -   Constant Time Adder - Phase Delay Curve (cyc) = **51PKCT**
    -   Vertical Multiplier - Phase Delay Curve = **51PKTD**
    -   Minimum Response Time - Phase Delay Curve (cyc) = **51PKMR**
    -   Electromechanical Reset - Phase Delay Curve = **51PKRS**
    -   Constant Time Adder - Ground Delay Curve (cyc) = **51G1KCT**
    -   Vertical Multiplier - Ground Delay Curve = **51G1KTD**
    -   Minimum Response Time - Ground Delay Curve (cyc) = **51G1KMR**
    -   Electromechanical Reset - Ground Delay Curve = **51G1KRS**
    -   Activate High Current Trip - Phase -> **MV06** # determines which trip operation phase high current tripping is enabled
    -   High Current Trip - Phase (mult. of min. trip phase) -> **50P2P** # phase current threshold for high current tripping
    -   Time Delay - Phase High Current Trip (cyc) = **50P2D** # intentional time delay for the phase high current tripping
    -   Activate High Current Trip - Ground = **MV07**
    -   High Current Trip - Ground (mult. of min. trip ground) -> **50G2P**
    -   Time Delay - Ground High Current Trip (cyc) = **50G2D**
    -   Activate High Current Lockout - Phase = **MV08** # determines which trip operation phase high current lockout is enabled
    -   High Current Lockout - Phase (mult. of min. trip phase) -> **50P1P** # phase current threshold for high current lockout
    -   Activate High Current Lockout - Ground = **MV09**
    -   High Current Lockout - Ground (mult. of min. trip ground) = **50G1P**
-   Cold Load
    -   Enable Cold Load Pickup - Phase = **MV10**
    -   Cold Load Pickup - Phase (mult. of min. trip phase) -> **50P3P**
    -   Enable Cold Load Pickup - Ground = **MV11**
    -   Cold Load Pickup - Ground (mult. of min. trip ground -> **50G5P**
    -   Loss of Load Diversity Time (min) -> **SV05PU** (also SV06PU, SV07PU)
        -   The Loss of load diversity timer starts to time if both the following are true:
            -   The recloser is open
            -   The control is in the lockout state or reclosing is defeated
        -   When the Loss of load diversity timer times out, the cold load pickup scheme is activated, causing the following to occur:
            -   Fast curves are disabled
            -   Delay curves are desensitized per cold load pickup settings (the curves are not shifted, so coordination is maintained)
    -   Restore Minimum Trips Time Limit (min) -> **SV31PU** (also SV32PU, SV33PU, SV34PU) # forces current thresholds for overcurrent detection from temporary cold load pickup values back to regular Min. trip levels
    -   Restore Minimum Trips - Phase = **MV12**
    -   Restore Minimum Trips - Ground = **MV13**
-   Underfrequency
    -   Underfrequency Pickup (hz) = **81D1P**
    -   Underfrequency Time Delay (cyc) = **81D1D** # If the power system frequency remains below the Underfrequency pickup setting for the time delay setting, a trip is issued.
    -   Underfrequency Voltage Supervision Pickup (V, secondary) = **27B81P** # When the voltage drops below the pickup setting, underfrequency tripping will be blocked
-   Single Phase Operation
    -   Enable Single Phase Operation = **ESPB**
    -   Lockout Mode = **MV18** # 1 = 1-ph lockout, 2 = 1-ph lockout (3-ph for multi-fault), 3 = 3-ph lockout
    -   Enable 3-phase Trip When Yellow Handle Pulled = **MV17**
    -   Enable Phase Discordance Detection = **MV14**
        -   Phase discordance detection will trip and lockout all phases if the following conditions are present for at least 5 seconds:
            -   One or two phases are detected as open, but not all three (Relay Word Bit SPO = 1)

AND

-   Three phase operation mode active (Enable Single Phase Operation = N) OR Lockout Mode = 3 and one or more phases are in the lockout state.



Group 2 Settings (same as above)

Auto Transfer Settings

-   Voltage Settings
    -   Live Voltage Level (% of primary) -> **59YP2P** # A source will be considered "live" as soon as all three phases on the bushing connected to the "source side" are greater than this setting.
    -   Dead Voltage Level (% of primary) -> **27YP2P** # A source will be considered "dead" as soon as any of the bushing connected to the "source side" are less than this setting.
    -   Nominal Primary Voltage (V)
    -   Source Side = **MV32** # 0 = Z , 1 = Y
    -   Return Transfer Sequence **= MV31** # 0 = CBO (Close before open), 1 = OBC (open before close)
-   Transfer Settings
    -   Stable Source (cyc) **= SV62PU** # Continuous time preferred source must be live for return transfer
    -   Initial Transfer Delay (cyc) = **SV61PU** # continuous time a source must be dead to cause a transfer
    -   Return Transfer Interrupt Delay (cyc) = **SV54PU** # Sources will be paralleled for this time if CBO transfer selected
    -   Communication Fail Timer (cyc) = **SV52PU** # If comms bad for this amount of time, automation will be disabled

Undervoltage Trip

-   Undervoltage Trip Settings
    -   Enable Undervoltage Trip = **SV44**
    -   Undervoltage Trip Threshold (% of primary) -> **27YP1P** (also 27ZP1P)
    -   Undervoltage Trip Timer (cyc) = **SV42PU** # Time delay for issuing 3-ph trip on LOV
    -   Trip for 3-Phase Loss Of Voltage = **SV43** # Y = will trip for both 3-ph and 1-ph LOV, N = will only trip for 1-ph LOV
