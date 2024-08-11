IEC 61850 Communication (alternative to DNP, Modbus) - use SEL Architect
-   Moving from Analog, physical equipment, direct cabling to Ethernet and merging units
-   Multicast - it blasts all the data to everyone, and each device decides if it wants to receive (realtime)
    -   Sampled Values
    -   GOOSE
        -   Generic object oriented substation event
        -   Have a more massive dataset rather than optimized, because it doesn't take much bandwidth
        -   Very fast protocol for Point to Point (PTP)
        -   1 per relay




-   Unicast - each client has an address (destination and source)
    -   Control
    -   Configuration
    -   Supervision (e.g. reports)
    -   SCADA

Client/Server

-   DNP
-   Modbus
-   Slower than PTP



Physical Layer

-   Twisted Pair (RJ 45 Cat5, Cat6, Cat7)
    -   Straight or crossover cables (doesn't matter which if switch has auto-MDIX)
    -   Copper max distance is 100m
    -   Best practice: don't auto-negotiate port speed, best to set port speed

Fiber-Optic Ethernet

- Tx and Rx wavelengths must match
- Yellow = Tx
- White = Rx
- Multi Mode (better)
-   Single Mode
    - Many physical issues; stay away if possible
    - Can get dirty easily
    - Shape remains intact throughout the cable
    - Ideal operating margin >= 3dB (half power)
    - 3 dB/1000m power loss
        - Optical power budget (OPB) = Tx min (dB) - Rx (max) = 8dB
        - Worst OPB (WOPB) = OPB - 1dB
            - Cable loss = cable length x attenuation per unit length (dB)
            - Connector loss = # of connector pairs x 0.5 dB

LAN Topologies

-   Ring
    -   Ideal if ports are limited since it only requires 2 trunk ports
    -   Ideal for long distances
    -   Max 15 switches (if PTP is in use due to 15 hop limitation)
-   Ladder
    -   Best configuration
    -   Where any loss, the switches are only 2 hops away for communication
    -   Only root switch and backup root switch will have more trunk ports than rung switches
    -   Ideal for close to medium distances
-   Full Mesh



Serial is one direction communication (still communicates both ways, but the data is sent from one device straight to another)

-   RS 232

![Machine generated alternative text: RJ45 Connector Pinout for Straight and Crossover T-568a 6 T-568b Pair ' Pair Pair 3, 1, 4 pair 2 Pair3 Pair 1 Pair4 AAA T568A pair 3 Pair2 Pairi Pair4 T568B |1000](DA-LAN-image1.png)

