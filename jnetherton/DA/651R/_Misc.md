
![Machine generated alternative text: Reclosing Relay States and General Operation Table 6.5 Relay Word Bit and Front-Panel Correspondence to Reclosing Relay States Reclosing Relay State Reset Reclose Cycle Lockout Corresponding Relay Word Bit 79RS 79CY 79LO Corresponding Front-Panel LED 79 RESET 79 CYCLE 79 LOCKOUT The reclosing relay is in one, and only one, of these states (listed in Table 6.5) at any time. When in a given state, the corresponding Relay Word bit asserts to logical l, thus causing the corresponding LED to illuminate. Automatic reclosing only takes place when the relay is in the Reclose Cycle State. Table 5.3 provides more information about front-panel LED programming. Figure 6.9 explains in general the different states of the reclosing relay and its operation. Reset State The circuit breaker has been closed for a qualifying reset time. The SEL-651R is ready to go through an automatic reclosing sequence in the reclose cycle state if the circuit breaker trips open and reclose initiation is successful. Relay Word bit 79RS = logical 1 Front-panel 79 RESET LED illuminated Maintained Lockout Condition Unsuccessful Reclose Other Reset Lockout Timer Reset Timer Times Out Successful Reclose Initiation Reclose Cycle State Successful Reclose Initiation Initiation Conditions Times Out Lockout State All automatic reclosing attempts are unsuccessful, reclose initiation is unsuccessful, other lockout conditions occur, or the SEL-651R powers up. The relay returns to the reset state after the circuit breaker is closed, the reset timer times out, and there are no maintained lockout conditions. All Automatic Reclosing Attempts Unsuccessful Unsuccessful Reclose Initiation The SEL-651R Relay automatically recloses the circuit breaker after each successful reclose initiation and corresponding set open interval time. Relay Word bit 79CY = logical 1 Front-panel 79 CYCLE LED illuminated Other Lockout Conditions Relay Word bit 7910 = logical 1 Front-panel 79 LOCKOUT LED illuminated Figure 6.9 Reclosing Relay States and General Operation |800](651R-Misc-image1.png)



-   Sequence coordination
    -   Used when you don't have communication, and you need them to move from shot 0 to shot 1 together
        -   Downstream delay curve needs to be slower than upstream fast curve (fast then delay) (fault past downstream)
        -   Upstream moves to shot 1 without opening
        -   Reset timer needs to be greater than the maximum open interval
    -   79SEQ



![Machine generated alternative text: NOTE: This example portrayed in Figure 6.15 and Figure 6.16 only shows operation with phase overcurrent elements. Sequence coordination can also work with ground overcurrent elements (e.g., add a ground time-overcurrent element pickup to the sequence- coordination setting: 79SEQ3P 79RS3P AND (SIP OR 515). Assume that the downstream recloser is set to operate twice on the fast curve and then twice on the delay curve. The delay curve is allowed to operate after two fast-curve operations because the fast curves are then inoperative for tripping. The SEL-65 IR-2 fast curve is coordinated with the downstream recloser fast curve. The SEL-65 IR-2 delay curve is coordinated with the downstream recloser delay curve. How phase time-overcurrent element 5 1 PT converts between fast and delay curve operation is covered in Time Overcurrent Elements on page 4.13. SEL-651R Delay-Curve Phase (Downstream Recloser) Fast-Curve Phase (Downstream Recloser) Downstream Recloser Delay-Curve Phase (SEL-651R) Fast-Curve Phase (SEL-651R) Figure 6.15 Sequence Coordination Between the SEL-651R-2 Recloser Control and a Downstream Recloser O Fault occurs beyond downstream recloser. @ Fault cleared by downstream recloser fast curve. 79SE03P 79RS3P AND 51P Shot Counter 0 Figure 6.16 Operation of SEL-651R- 2 @ Downstream recloser recloses into fault. @ Fault cleared by downstream recloser delay curve. 13 2 Shot Counter for Sequence Coordination With Downstream Recloser (Additional 79SEQ Settings Example 1) |500](651R-Misc-image2.png)



NOTE:

For ULCL3P (unlatch close - will refuse to close when held high), you must add any automation to this equation to allow the automation to take place when pushbuttons are locked



TRIP3P OR NOT (LT06 AND SV38 OR CLOSE3P) OR NOT (LT05 OR CLOSE3P OR CC3 AND LT03 OR 79CY3P [OR LT15 OR SV59T]{.mark}) OR SV22T AND MV17 <> 0.00 # 3-PH CLOSE UNLATCH

**Sectionalizers**
Sectionalizers are pole-mounted devices that count overcurrent faults and subsequent trip
operations. They open the circuit during the open interval of an upstream reclosing breaker to
isolate a faulted line section. The upstream recloser can reclose and reset before reaching lockout
when the sectionalizer disconnects the faulted line section. Sectionalizers are not intended to
interrupt fault current when isolating a faulted line section.

**Timers**
n = 01-64
The SELOGIC control equation variables/timers are reset to logical 0 if any of
the following occur: power to the relay is lost, settings are changed for the
active settings group, or the active settings group is changed.
SVn = Activate timer
SVnT = Timer trigger
SVnPU = how long SVn must be held high for SVnT to assert (SVn = 1, SVnT = 0 while timer timing on pickup time)
SVnDO = delay for when SVnT deasserts (SVn = 0, timer timed out on pickup time, SVnT = 1 while timer timing on dropout time)


![Machine generated alternative text: SELOGIC Variable/ Timer Input Settings SVn SVnPU SVnDO Relay Word Bits SVn SVnT |300](651R-Misc-image3.png)
![Machine generated alternative text: T d SELOGIC control equation varia ble timer input SVnn asserted; timer timing on pickup time; timer output SVnnT not asserted. SELOGIC control equation varia ble timer input SVnn asserted; timer timed out on pickup time; timer output SVnnT asserted. SELOGIC control equation variable timer input SVnn not asserted; timer previ- ously timed out on pickup time; timer output SVnnT remains asserted while timer timing on dropout time. |300](651R-Misc-image4.png)
![Machine generated alternative text: SV19PU SV19DO SV19 svos SV05PU SV05DO TR3P sc02PV SC02R sc02CU 0.00 600.00 R_TRIG 50PIT OR R_TRIG 50GIT OR R_TRIG 50QIT F_TRIG 50P1 T OR F_TRIG 50GIT OR F_TRIG 50QIT 2 SC02QU AND SV19T AND NOT 501- 2 NOT(SV19T) NOT SOL AND SV05T ](651R-Misc-image5.png)

SV19T immediately asserted for overcurrent

SV19T asserted for 5 seconds after overcurrent starts

Rising trigger phase, ground, and negative sequence overcurrent

Falling trigger " "

SV05T immediately asserted when overcurrent drops out

SV05T asserted for 5 seconds after overcurrent drops out

Trips when counter = 2, there is an overcurrent, and there is no load current

Counter counts twice

Counter resets after 5 seconds of seeing overcurrent

Counter counts up when there is no load current detected and overcurrent drops out

![Machine generated alternative text: E79 ](651R-Misc-image6.png){width="1.5416666666666667in" height="0.75in"}

Reclosing logic deactivated

Disable single-phase settings/operation



**Counters**

n = 01-16

Counters are reset to a count value of zero after power is lost and then restored.

Counters are retained through settings changes and active group changes.

Typical enable auto transfer for preferred:

-   Comms between controls must be ok
-   Preferred source must be closed
-   Preferred source must be live
-   Alternate source must be open
-   HLT is not active on either control



Typical enable auto transfer for non-preferred:

-   Comms between controls must be ok
-   One source closed and live
-   Other source open
-   HLT not active on either control
-   (There's no return transfers because there's no preference, it's all initial transfers)



Typical disable auto transfer:

-   Comms failure between controls
-   Manual command through pushbuttons
-   Disable auto mode issued through SCADA
-   Manual recloser operation issued from SCADA





Faults (on load side, source side fault will just look like a loss of voltage)

-   When there's a loss of voltage, check that you don't have fault current present and that there's no reclose cycle happening
-   It won't drop out of auto on a temporary fault (if it does 2 shots and fault clears, then it closes, it should still be in auto)





Undervoltage

-   Regardless of if auto is on
-   Basically happens if alternate source is dead, and they lose voltage on the preferred





If close before open return, might do sync checks for paralleling issues

![Machine generated alternative text: Name SCnLD SCnPV SCnCU SCnCD SCnR SCnQU SCnQD SCn Type Active High Input Input V alue Rising-Edge Input Rising-Edge Input Active High Input Active High Output Active High Output Output Value Description Load counter with the preset value (follows SELOGIC setting) This Preset Value is loaded when SCnLD pulsed. This Preset Value is used as a maximum count in the SCnQU comparison (follows SELOGIC setting) Count Up increments the counter (follows SELOGIC setting) Count Down decrements the counter (follows SELOGIC setting). The counter freezes if set to NA. See NOTE under SELOGIC Counter Settings on page SET.49. Reset counter to zero (follows SELOGIC setting). This Q Up output asserts when the Preset Value (maxi- mum count) is reached (SCn = SCnPV, n = 01 to 16). This Q Down output asserts when the counter is equal to zero (SCn = 0, n = 01 to 16). This counter output is an analog value that may be used with analog comparison operators in a SELOGIC control equation, or viewed with the COUNTER command. |400](651R-Misc-image7.png)



**Latches**

n = 01-32

If both settings

SETn and RSTn assert to logical 1, setting RSTn has priority and latch bit LTn deasserts to logical 0.

The states of the latch bits are retained if power to the relay is lost and then restored, if individual settings are changed, or the active settings group is changed.

![Machine generated alternative text: setting sqn word Bits Lin (set) ](651R-Misc-image9.png){width="12.104166666666666in" height="4.020833333333333in"}









