
787 - differential protection

High impedance fault

-   Typically used as an indication back to SCADA as an indicator, not as protection
-   Might not get enough fault current to recognize it
-   Might not get waveforms you'd expect
-   Loss of voltage would be the most effective way to detect it, but you'd need communication upstream



Types of overcurrent

-   Fuses
-   Relays
    -   Electromechanical
    -   Microprocessor
-   Fuse emulation devices
    -   Manual switch, no communication
    -   Designed to replace a fuse
    -   Usually self-powered
        -   Customers like this, no PT or control cabinet
    -   It's there to trip on a fault when you have a fault
    -   Not relays



CT Accuracy class doesn't matter much for us for protection purposes

-   Matters for metering
-   Rogowski coil
    -   Limited by the relay being able to integrate
-   Relay burden almost negligible for electronic relays
    -   Before, CT needed higher burden rating because they were having to use that power to move pieces in the electromechanical relay



Ensure the relay you're using has the right ANSI number (27, 51, etc)



Time delay manipulates the curve bending the bottom up

Time dial translates the whole curve

Minimum response (minimum trip time)
-   VI won't trip before a specific time
-   Horizontal line cuts through
-   Sometimes used for processing (maybe it needs some number of cycles)



Ground

-   Zero sequence CT (one CT around all the cables)
-   CT per phase - summation of secondary currents through the relay
    -   Won't saturate until higher currents because each phase has it's own CT
-   Phase imbalance calculation



Torque control turns off an element



Cold load pickup - usually seconds or minutes, could be more
-   Positive sequence
-   Real load
-   Should see current

Inrush - cycles
-   Energizing of the transformer
-   2nd harmonic, sometimes 5th harmonic

Sectionalizer
-   Traditionally a loadbreak, couldn't interrupt a fault


