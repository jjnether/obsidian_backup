-   T1_LED
    -   (PCT02Q OR PCT03Q OR PCT04Q OR PCT05Q OR PCT06Q) # INST
-   T2_LED
    -   51S1T OR 51S2T OR 51S3T OR 51S4T OR 51S5T OR 51S6T # TIME
-   T3_LED
    -   ASV038 # MECH BLOCK
-   T4_LED
    -   ASV031 # SWITCH LOCKOUT
-   T5_LED
    -   ASV205 # OC MECH FAILURE
-   T6_LED
    -   PLT27 AND ASV165 # W WAY A PH F
-   T7_LED
    -   PLT28 AND ASV165 # W WAY B PH F
-   T8_LED
    -   PLT29 AND ASV165 # W WAY C PH F
-   T9_LED
    -   PLT30 AND ASV165 # X WAY A PH F
-   T10_LED
    -   PLT31 AND ASV165 # X WAY B PH F
-   T11_LED
    -   PLT32 AND ASV165 # X WAY C PH F
-   T12_LED
    -   IN309 # EXTERNAL HANDLES ACTIVE
-   T13_LED
    -   (((VAYM > AMV011) AND NOT ASV006) OR (IN103 AND ASV006)) AND NOT (IN310 AND (ASV001 OR ASV003)) # VAY ON/S1 LIVE (DVS)
-   T14_LED
    -   (VBYM > AMV011) AND NOT ASV006 AND NOT (IN310 AND (ASV001 OR ASV003)) # VBY ON
-   T15_LED
    -   (VCYM > AMV011) AND NOT ASV006 AND NOT (IN310 AND (ASV001 OR ASV003)) # VCY ON
-   T16_LED
    -   (((VAZM > AMV011) AND NOT ASV006) OR (IN106 AND ASV006)) AND NOT (IN310 AND ASV002) # VAZ ON/S2 LIVE (DVS)
-   T17_LED
    -   (VBZM > AMV011) AND NOT ASV006 AND NOT (IN310 AND ASV002) # VBZ ON
-   T18_LED
    -   (VCZM > AMV011) AND NOT ASV006 AND NOT (IN310 AND ASV002) # VCZ ON
-   T19_LED
    -   NOT ASV203 AND ((51S1T AND B1IAFIM > AMV140) OR (51S3T AND B2IAFIM > AMV141) OR (50P1 AND B1IAFIM > AMV117) OR (50P2 AND B2IAFIM > AMV118)) # A PHASE FAULT
-   T20_LED
    -   NOT ASV203 AND ((51S1T AND B1IBFIM > AMV140) OR (51S3T AND B2IBFIM > AMV141) OR (50P1 AND B1IBFIM > AMV117) OR (50P2 AND B2IBFIM > AMV118)) # B PHASE FAULT
-   T21_LED
    -   NOT ASV203 AND ((51S1T AND B1ICFIM > AMV140) OR (51S3T AND B2ICFIM > AMV141) OR (50P1 AND B1ICFIM > AMV117) OR (50P2 AND B2ICFIM > AMV118)) # C PHASE FAULT
-   T22_LED
    -   NOT ASV203 AND ((51S2T OR 51S4T OR PSV38 OR PSV39)) # GROUND FAULT
-   T23_LED
    -   0
-   T24_LED
    -   ASV068 # REMOTE MODE
