Multizone feeder differential protection

-   Protection zones in general
    -   Protection tripping zone defined by current interrupting devices
    -   Fault detection zone defined by current measurement points
    -   Ideally, the two zones overlap to maximize return on investment
-   Currents measured throughout the feeder
-   Enabling technologies
    -   Distributed electrical sensing (DES)
        -   Can measure 30 sensors per fiber core (daisy chained)
        -   Fiber Bragg grating principle
            -   Measurement recorded in wavelength
            -   Permits serial multiplexing
        -   Piezoelectric device converts voltage to strain, measurable by FBG
            -   Expansion or compression of the FBG causes a detectable shift in the reflected wavelength
    -   All dielectric self-supporting fiber cables
-   Benefits
    -   Scalable
    -   Ultra-sensitive
    -   Instantaneous
    -   Dependable
    -   Future-ready







Marginalia - Ralph Barone
-   Margins
    -   Coordinating margins exist to prevent multiple relays from operating simultaneously, and to let the intended ones clear the fault first
    -   Margins are a statistical combination of numerous error factors
        -   If you choose to sum all the error factors, you leave too much performance on the floor
    -   The effect of a too small margin is obvious, the effect of one which is too large is much more subtle
    -   The impact of a given margin number needs to be proven by the passage of time



Symmetrical Components

-   Symmetrical (balanced) system
    -   All current and voltage phasors have equal amplitude and 120 degree phase shifts
-   Normal condition power system is symmetric
-   Common fault types
    -   Shunt
        -   Phase to ground
            -   Most common
            -   Faulted phase is very large
            -   Unfaulted phases are small, almost zero
            -   Connect sequence networks in series (
        -   Phase to phase
            -   Connected positive and negative sequence networks in parallel (zero sequence is 0)
        -   Phase to phase to ground
            -   Connect all 3 sequence networks in parallel
        -   Three phase
            -   All phases have a large current and they're all equal
            -   Only see positive sequence network (negative and zero are 0)
    -   Open - single phase
    -   Cross country
-   Sequence networks
    -   Combine positive, negative, and zero sequence networks






-   a = 120 degrees
-   a2 = 240 degrees
-   Positive sequence
    -   A-B-C phase counter clockwise sequence
    -   120 degree phase separation
    -   V1 = 1/3*(Va + a*Vb + a2 *Vc)
-   Negative sequence
    -   A-C-B phase counter clockwise sequence
    -   120 degree phase separation
    -   V2 = 1/3*(Va + a2*Vb + a*Vc)
-   Zero Sequence
    -   No sequence
    -   All phasors in phase
    -   I and V = sum of phasors divided by 3
        -   V0 = 1/3*(Va + Vb + Vc)
-   Ia = I0 + I1 + I2






-   Transformer interconnections
    -   Z0 = Z1 = Z2
    -   Z0 = infinity, depending on grounding connection
-   Transmission and distribution lines
    -   Z1 = Z2
    -   Z0 is always different from Z1 because it is loop impedance (conductor plus ground)
    -   For transmission lines, Z0 usually 3 times Z1





Methods of interrupting faults

-   Fuses
    -   Continuous ratings of 100A - 200A
-   Recloser
    -   Continuous ratings up to 800A
-   Circuit Breaker
    -   Capable of making, carrying, and breaking current
    -   Continuous ratings of 600A - 3000A



Instantaneous Overcurrent (50)

-   Three main IOC practices:
    -   Set pickup 25% greater than maximum current for three-phase fault at end of line
    -   Use high-set instantaneous element for catastrophic overcurrent backup
    -   Employ low-set instantaneous elements for current detection supervision for other elements
-   Block reclosing when high-set IOC operates
-   Add short delay of 200 ms to blow downstream fuses (fuse-blowing scheme)

Timed-Overcurrent (51)

-   Multiplier or time dial shifts curve up and down
-   Pickup shifts left or right

Directional Overcurrent (67)

-   Sense power-flow direction
-   Enable OC on power flowing in tripping direction
-   Establishes forward via polarizing quantity or with shaped regions
    -   Shaped regions
        -   Choose polarizing: zero-sequence voltage, -3V_0 line
        -   Ground fault is on 3I_0 line
        -   Settings
            -   ECA = 90
            -   FWD LA = 80 - forward limit angle,
            -   REV LA = 80 - reverse limit angle, +- angular limit from ECA for operation

Ground-fault detection

-   Balanced load has near-zero ground current
-   Fault increases circulating ground current
-   Set ground overcurrent element to 25-40% of load current
-   Residual ground fault detection
    -   Larger conductors, less sensitivity
-   Zero sequence CT connection
    -   Pass conductors through CT window

High-impedance faults

-   Major safety and public hazard
-   Conventional overcurrent schemes cannot detect Hi-Z faults (small, intermittent currents)
-   Modern relays incorporate algorithms to detect Hi-Z faults quickly and reliably
    -   Pattern recognition
    -   Load learning and subtraction



No curve crossovers

-   Use discrimination





Pilot Protection

-   Aka teleprotection
-   Closely connected to an evolution of communication channel technologies
-   Overcurrent protection alternative
    -   Least expensive
-   Distance protection alternative
    -   Requires both voltage and current inputs to determine fault locations
-   Zone 1 set for 80-90% of line impedance, no intentional delay
-   Zone 2 set for 100% of line plus 25-50% of shortest adjacent line from remote bus. Zone 1 delay is set to allow remote terminal zone 1 and its breaker to operate first
-   Zone 3 set for 100% of (local + longest adjacent line) plsu 25% margin. Zone 3 delay is set to allow zone 2 and the breaker at the remote...
-   Distance protection
-   Permissive:
    -   High speed tripping for the entire line can only take place if a permissive signal is received and the local protection relay detcts the fault
    -   Most frequently applied
    -   More secure than blocking schemes in general
    -   Permissive overreaching (POTT)
        -   Most secure - must receive permissive to trip
        -   Only operates with communication
    -   Permissive Underreaching Transfer Trip (PUTT)
        -   More secure than DUTT
-   Direct transfer trip (DTT)
-   Direct Underreaching Transfer Trip (DUTT)
-   Blocking:
    -   Blocking scheme is very dependable in that it will operate even when communication channel is out of service, and thus less secure due to potentials of over-tripping
    -   Directional Comparison Blocking (DCB)
        -   Very dependable (does not require channel for tripping)
        -   Less secure - tends to over-trip
        -   Can use distance or ground OC relays (overreach keying)
        -   Best suited with simple on-of power line carrier historically
    -   Directional Comparison Unblocking (DCUB)
        -   Tripos only when unblock is received - secure
        -   Combination of blocking scheme and permissive scheme
-   All sections of a line must be completely covered by zone 1 (it needs faster tripping, delayed zone 2 coverage isn't enough)
-   Communication channel types:
    -   Direct
    -   Multiplexed
        -   Provides shared (multiplexed) media for multiple connections
        -   Channels use different:
            -   Frequency, in analog carrier
            -   Time in digital carrier
            -   Wavelength in optical carrier
        -   Operates as an always running train with spaces for different carriages
        -   Typically fiber optic cables are used, but digital microwave is also an option
    -   Switched
        -   Requires knowledge of where to connect an input to and resource availability (output channels, internal buffers)
        -   Carrier ethernet and Multi protocol label switching (MPLS)
-   Modern Line Current differential protection
    -   Protect multiple transmission line terminals
    -   Direct fiber
        -   Short - 1-3 km
        -   Medium - 3-50 km
        -   Long - 51-160 km
-   Sampling synchronization
    -   Internal - Echo (calculates time difference between clocks)
    -   External - GNSS (clocks are synchronized within 1 us accuracy
-   Charging current compensation
    -   Calculated
    -   Measured
-   Stub Bus Protection
    -   On a breaker-and-half or ring type multi-terminal lines, an out-of-service terminal would leave a short stub bus section that still needs high speed protection while the remaining line terminals must be kept in service undisturbed
-   Multi terminal application
    -   Master-master scheme
    -   Master-slave scheme
        -   Only master IED performs the calculation and sends trip signals to the slaves
        -   Slave IEDs only require one communication module and channel to Master
-   Redundant channels should be geographically diverse
-   Protection engineer protection channel expectations
    -   Digital circuit Bit Error Rate (BER)
    -   Variable Channel Delays
    -   SONET switching - 50 ms hits (digital circuits)
    -   Channel Asymmetry
    -   Channel Bank failures







Duke Distribution Substation

-   CPC - centralized protection and control
-   Direct CPC - small systems
    -   Full copper
-   P2P CPC - medium
    -   Fiber from CPC to merging units, then copper
-   IEC 61850 - large


