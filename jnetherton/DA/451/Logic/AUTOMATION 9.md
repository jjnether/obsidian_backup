# DISPLAY POINTS - LOGIC PRIMARLY USED FOR DISPLAY POINTS ON THE ROLLING SCREENS / BAY SCREEN
#
ASV066 := ((ASV058 OR ASV199) AND NOT PSV40) OR ((ASV060 OR ASV208) AND NOT PSV41) AND ALT02 # WAITING FOR SYNCH DISPLAY POINT
ASV020 := ASV106 AND NOT ASV002 AND ASV101 AND ASV101 AND ASV055 AND ASV121 AND NOT ACT14Q AND NOT ASV014 OR (ASV004 AND ACT14Q) # S1-IT INITIAL TRANSFER TIMING
ASV021 := ASV107 AND ASV001 AND NOT ASV101 AND ((ASV011 AND ASV102) OR (NOT ASV011 AND ASV111)) AND ASV055 AND ASV121 AND NOT ACT15Q OR ASV036 # S1-RT RETURN TRANSFER TIMING
ASV022 := ASV116 AND NOT ASV001 AND ASV111 AND ASV111 AND ASV055 AND ASV121 AND NOT ACT16Q AND NOT ASV014 OR (ASV004 AND ACT16Q) # S2-IT INITIAL TRANSFER TIMING F
ASV023 := ASV117 AND ASV002 AND NOT ASV111 AND ((ASV011 AND ASV112) OR (NOT ASV011 AND ASV101)) AND ASV055 AND ASV121 AND NOT ACT17Q OR ASV037 # S2-RT RETURN TRANSFER TIMING
#
# O/C MECHANISM FAILURE LOGIC - SINGLE PHASE / THREE PHASE LOGIC
AMV207 := 0.150000 # W-WAY OPEN FAILURE TIME, SECONDS
AMV209 := 0.150000 # X-WAY OPEN FAILURE TIME, SECONDS
AST21PT := AMV206 # W-WAY, A-PHASE/3PH TRIP DURATION TIMER TIME
AST21R := NOT PLT27 # W-WAY, A-PHASE/3PH TRIP DURATION TIMER RESET
AST21IN := PLT27 # W-WAY, A-PHASE/3PH TRIP DURATION TIMER SET
AST27PT := AMV207 # W-WAY, A-PHASE/3PH OPEN FAILURE TIMER TIME
AST27R := PCT01Q # W-WAY, A-PHASE/3PH OPEN FAILURE TIMER RESET
ASV193 := AST27Q AND ASV165 # A-PHASE MECHANISM FAILURE
ASV194 := AST27Q AND ASV166 # THREE-PHASE MECHANISM FAILURE
AST27IN := AST21Q AND NOT ALT10 # W-WAY, A-PHASE/3PH OPEN FAILURE TIMER SET
AST22PT := AMV206 # W-WAY, B-PHASE TRIP DURATION TIMER TIME
AST22R := NOT PLT28 # W-WAY, B-PHASE TRIP DURATION TIMER RESET
AST22IN := PLT28 # W-WAY, B-PHASE TRIP DURATION TIMER SET
AST28PT := AMV207 # W-WAY, B-PHASE OPEN FAILURE TIMER TIME
AST28R := PCT01Q # W-WAY, B-PHASE OPEN FAILURE TIMER RESET
AST28IN := AST22Q AND NOT ALT10 # W-WAY, B-PHASE OPEN FAILURE TIMER SET
AST23PT := AMV206 # W-WAY, C-PHASE TRIP DURATION TIMER TIME
AST23R := NOT PLT29 # W-WAY, C-PHASE TRIP DURATION TIMER RESET
AST23IN := PLT29 # W-WAY, C-PHASE TRIP DURATION TIMER SET
AST29PT := AMV207 # W-WAY, C-PHASE OPEN FAILURE TIMER TIME
AST29R := PCT01Q # W-WAY, C-PHASE OPEN FAILURE TIMER RESET
AST29IN := AST23Q AND NOT ALT10 # W-WAY, C-PHASE OPEN FAILURE TIMER SET
AST24PT := AMV208 # X-WAY, A-PHASE/3PH TRIP DURATION TIMER TIME
AST24R := NOT PLT30 # X-WAY, A-PHASE/3PH TRIP DURATION TIMER RESET
AST24IN := PLT30 # X-WAY, A-PHASE/3PH TRIP DURATION TIMER SET
AST30PT := AMV209 # X-WAY, A-PHASE/3PH OPEN FAILURE TIMER TIME
AST30R := PCT01Q # X-WAY, A-PHASE/3PH OPEN FAILURE TIMER RESET
ASV195 := AST30Q AND ASV165 # A-PHASE MECHANISM FAILURE
ASV196 := AST30Q AND ASV166 # THREE-PHASE MECHANISM FAILURE
AST30IN := AST24Q AND NOT ALT11 # X-WAY, A-PHASE/3PH OPEN FAILURE TIMER SET
AST25PT := AMV208 # X-WAY, B-PHASE TRIP DURATION TIMER TIME
AST25R := NOT PLT31 # X-WAY, B-PHASE TRIP DURATION TIMER RESET
AST25IN := PLT31 # X-WAY, B-PHASE TRIP DURATION TIMER SET
AST31PT := AMV209 # X-WAY, B-PHASE OPEN FAILURE TIMER TIME
AST31R := PCT01Q # X-WAY, B-PHASE OPEN FAILURE TIMER RESET
AST31IN := PCT01Q AND NOT ALT11 # X-WAY, B-PHASE OPEN FAILURE TIMER SET
AST26PT := AMV208 # X-WAY, C-PHASE TRIP DURATION TIMER TIME
AST26R := NOT PLT32 # X-WAY, C-PHASE TRIP DURATION TIMER RESET
AST26IN := PLT32 # X-WAY, C-PHASE TRIP DURATION TIMER SET
AST32PT := AMV209 # X-WAY, C-PHASE OPEN FAILURE TIMER TIME
AST32R := PCT01Q # X-WAY, C-PHASE OPEN FAILURE TIMER RESET
AST32IN := AST26Q AND NOT ALT11 # X-WAY, C-PHASE OPEN FAILURE TIMER SET
ASV204 := ASV193 OR ASV194 OR AST28Q OR AST29Q OR ASV195 OR ASV196 OR AST31Q OR AST32Q # O/C MECH FAILURE DISPLAY POINT
#
# OSCILLATOR AND FLASHING DISPLAY POINT LOGIC
ASV030 := ACT01Q AND NOT ASV121 # LOW SF6 FLASHING DISPLAY
ASV031 := ACT01Q AND ASV141 # SWITCH LO FLASHING DISPLAY
ASV205 := ACT01Q AND ASV204 # SINGLE/THREE PHASE O/C MECH FAILURE FLASHING DISPLAY POINT
ACT01PU := 0.100000
ACT01DO := 0.100000
ACT01IN := NOT ACT01Q # 100MS OSCILLATOR
#
ASV164 := SG3 OR SG4 # MAINTENANCE MODE SETTINGS GROUPS
ASV165 := SG2 OR SG4 # SINGLE PHASE MODE SETTINGS GROUPS
ASV166 := SG1 OR SG3 # THREE PHASE MODE SETTINGS GROUPS
#
# DISPLAY POINT ALIAS LOGIC
ASV038 := IN201 OR IN202 # MECH BLOCK DISPLAY POINT VAR
ASV012 := NOT ASV011 AND NOT ASV202 # RETURN SEQUENCE CLOSE BEFORE OPEN UNLESS IN NO RETURN MODE
#
# PRIMARY VOLTAGE FOR BAY CONTROL
AMV060 := VAYM * PTRY
AMV061 := VBYM * PTRY
AMV062 := VCYM * PTRY
AMV063 := VAZM * PTRZ
AMV064 := VBZM * PTRZ
AMV065 := VCZM * PTRZ
#























