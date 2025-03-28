Transceiver left to right: hmi, comm a, comm b

---
WEEK OF 03/24

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

Completed L3 testing:
- MCUP1/IWM

Compano S/N : MN539D/102526945

Steve with Qualace


PTX TESTING
- RD01 - flipped way 3 and way 4
- D02 - flipped way 3 and way 4
- H02 - flipped way 3 and way 4
- A10 - flipped
	- Way 4 PTX.A20 HIGH TEMP NEVER SHOWED UP
- c01 - getting W3 PTX alarms, but when clicking on it, doesn't show high temp like it should
- H01, PTX.H07 - no signals seen at all, not being seen at the relay either
- H01, PTX.H05 - showing Way 3, but should be Way 4, also not seeing low oil, high temp, also not se
- B10, PTX.B19 - low pressure held high
- B02, PTX.B03 - high temp held high

INCORRECT COMM LABELS:
1EY2.MVS.RD01
1EY2.MVS.D08
1EY2.MVS.D07
1EY2.MVS.D04
1EY2.MVS.D02
1EY2.MVS.D01
1EY2.MVS.H01
1EY2.MVS.B10

1MCUP2.MVS.01
1MCUP6.MVS.01
1MCUP7.MVS.01
1MCUP8.MVS.01
1MCUP9.MVS.01

(good ones)
B04
B07
B08

A02
A03
A06
A07
A08
H01
C01
C04
C07



Ra01 no port locks
A01 no port locks

Uploaded Updated diagram builder map to HMI at 1EY1

---
67UP2D - delay was off - supposed to be 9.625 cycles - currently set to 9.5
- everything else looks correct