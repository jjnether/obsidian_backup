Transceiver left to right: hmi, comm a, comm b


Questions:
- pulled MIB 2 from 2EY1.MVS.B02 for MIB replacement
- replaced MIB 2 on 1EY1.MVS.A01 and test way 2 is operating properly
- verified motor operation on ways 1 and 2 for MCUP5 - can close this issue in their system
- checked comms on MCUP 2/3
    - peer to peer comms were good
    - MCUP2 had bad comms to the hmi, but wiring looked fine at the MVS - fixed by unplugging and replugging fiber into transceiver at the HMI

Peer to peer comms testing:
- MCUP 6/7
- MCUP 4/5
- MCUP 2/3
- MCUP 1/IWM

HMI comm testing:
- MCUP7
- MCUP6
- MCUP5
- MCUP4
- MCUP3
- MCUP2
- MCUP1
- IWM




PTX testing:
- All MCUPs already completed TX testing:
- All MCUPs already conp


Compano S/N : MN539D/102526945

HMI Testing:
- IWM - Way 1 voltage values seem off, but what the relay sees matches what the HMI sees. Must be something switch side?