# TRIP LATCH LOGIC
PLT27S := IN205 AND RLY_EN AND (PCT02Q OR 51S1T) # W-WAY, A-PHASE TRIP LATCH SET
PLT27R := NOT (51S1 OR PCT02Q) OR F_TRIG IN205 # W-WAY, A-PHASE TRIP LATCH RESET
PLT28S := IN206 AND RLY_EN AND (PCT03Q OR 51S2T) # W-WAY, B-PHASE TRIP LATCH SET
PLT28R := NOT (51S2 OR PCT03Q) OR F_TRIG IN206 # W-WAY, B-PHASE TRIP LATCH RESET
PLT29S := IN207 AND RLY_EN AND (PCT04Q OR 51S3T) # W-WAY, C-PHASE TRIP LATCH SET
PLT29R := NOT (51S3 OR PCT04Q) OR F_TRIG IN207 # W-WAY, C-PHASE TRIP LATCH RESET
PLT30S := IN208 AND RLY_EN AND (PCT05Q OR 51S4T) # X-WAY, A-PHASE TRIP LATCH SET
PLT30R := NOT (51S4 OR PCT05Q) OR F_TRIG IN208 # X-WAY, A-PHASE TRIP LATCH RESET
PLT31S := IN209 AND RLY_EN AND (PCT06Q OR 51S5T) # X-WAY, B-PHASE TRIP LATCH SET
PLT31R := NOT (51S5 OR PCT06Q) OR F_TRIG IN209 # X-WAY, B-PHASE TRIP LATCH RESET
PLT32S := IN210 AND RLY_EN AND (PCT07Q OR 51S6T) # X-WAY, C-PHASE TRIP LATCH SET
PLT32R := NOT (51S6 OR PCT07Q) OR F_TRIG IN210 # X-WAY, C-PHASE TRIP LATCH RESET
#
# OC DETECTION AND TRIP
PSV33 := PLT27 OR PLT28 OR PLT29 # W-WAY PHASE FAULT (USED FOR TRIP TARGET)
PSV34 := PLT30 OR PLT31 OR PLT32 # X-WAY PHASE FAULT (USED FOR TRIP TARGET)
PSV35 := PSV33 OR PSV34 OR 50P1 OR 50P2 OR PSV38 OR PSV39 # ANY OVERCURRENT TRIP
#
#
# SYNC CHECKS
PSV40 := ((25A1BK1 AND ASV198 AND ASV107 AND ASV117) OR (ASV198 AND ASV116) OR ASV197 OR ACT23Q OR (25A1BK1 AND (ALT03 OR ASV068)) OR ASV112 OR ALT01) AND ASV007 OR NOT ASV007 # SOURCE 1 SYNC CHECK CBO CLOSE
PSV41 := ((25A1BK1 AND ASV207 AND ASV107 AND ASV117) OR (ASV207 AND ASV106) OR ASV206 OR ACT24Q OR (25A1BK1 AND (ALT03 OR ASV068)) OR ASV102 OR ALT01) AND ASV007 OR NOT ASV007 # SOURCE 2 SYNC CHECK CBO CLOSE
#
# 50P & 50G (W-WAY)
PCT02PU := AMV222 # W-WAY APH 50P OC DELAY
PCT02DO := NOT IN205 # TRIP UNLATCH
PCT02IN := B1IAFIM > AMV100 # W-WAY APH 50P OC
PCT03PU := AMV223 # W-WAY BPH 50P OC DELAY
PCT03DO := NOT IN206 # TRIP UNLATCH
PCT03IN := B1IBFIM > AMV101 # W-WAY BPH 50P OC
PCT04PU := AMV224 # W-WAY CPH 50P OC DELAY
PCT04DO := NOT IN207 # TRIP UNLATCH
PCT04IN := B1ICFIM > AMV102 # W-WAY CPH 50P OC
PSV36 := (B1IAFIM > AMV100) OR (B1IBFIM > AMV101) OR (B1ICFIM > AMV102) # W-WAY 50P OC TRIP
#
#
#
#
# 50P & 50G (X-WAY)
PCT05PU := AMV225 # X-WAY APH 50P OC DELAY
PCT05DO := NOT IN208 # TRIP UNLATCH
PCT05IN := B2IAFIM > AMV103 # X-WAY APH 50P OC
PCT06PU := AMV226 # X-WAY BPH 50P OC DELAY
PCT06DO := NOT IN209 # TRIP UNLATCH
PCT06IN := B2IBFIM > AMV104 # X-WAY BPH 50P OC
PCT07PU := AMV227 # X-WAY CPH 50P OC DELAY
PCT07DO := NOT IN210 # TRIP UNLATCH
PCT07IN := B2ICFIM > AMV105 # X-WAY CPH 50P OC
PSV37 := (B2IAFIM > AMV103) OR (B2IBFIM > AMV104) OR (B2ICFIM > AMV105) # X-WAY 50P OC TRIP
#
#
#
PSV39 := (B2IGFIM > AMV120) # X-WAY 50G OC TRIP
#
#
#
# BREAKER CONTACT EMULATOR IN TEST LOGIC
PLT20S := R_TRIG ASV199 OR (R_TRIG ALT01 AND ASV001) OR (ASV003 AND R_TRIG ALT01 AND NOT PLT20 AND NOT PLT22) # SOURCE 1 52A EMULATOR SET
PLT20R := R_TRIG ASV212 OR R_TRIG PCT12Q OR (R_TRIG ALT01 AND ASV002) # SOURCE 1 52A EMULATOR RESET
PLT21S := R_TRIG ASV212 OR R_TRIG PCT12Q OR (R_TRIG ALT01 AND ASV002) # SOURCE 1 52B EMULATOR SET
PLT21R := R_TRIG ASV199 OR (R_TRIG ALT01 AND ASV001) # SOURCE 1 52B EMULATOR RESET
PLT22S := R_TRIG ASV208 OR (R_TRIG ALT01 AND ASV002) # SOURCE 1 52A EMULATOR SET
PLT22R := R_TRIG ASV222 OR R_TRIG PCT12Q OR (R_TRIG ALT01 AND ASV001) # SOURCE 1 52A EMULATOR RESET
PLT23S := R_TRIG ASV222 OR R_TRIG PCT12Q OR (R_TRIG ALT01 AND ASV001) # SOURCE 1 52B EMULATOR SET
PLT23R := R_TRIG ASV208 OR (R_TRIG ALT01 AND ASV002) # SOURCE 1 52B EMULATOR RESET
#
# NO RETURN SEQUENCE LOGIC
PLT18S := R_TRIG ASV236 # SOURCE 1 ITS OPEN LATCH SET
PLT18R := F_TRIG ASV243 OR F_TRIG ALT17 # SOURCE 1 ITS OPEN LATCH RESET
PLT19S := R_TRIG ASV239 # SOURCE 2 ITS OPEN LATCH SET
PLT19R := F_TRIG ASV231 OR F_TRIG ALT18 # SOURCE 2 ITS OPEN LATCH RESET
PLT01S := NOT ASV003 AND ((ASV202 AND F_TRIG PLT18) OR (ASV202 AND F_TRIG PLT19)) # EXIT AUTO ON "NO RETURN SEQUENCE" VARIABLE
PLT01R := F_TRIG ALT01 OR F_TRIG ALT02
#
# REMOTE BIT TIME STRETCHERS
PCT17PU := 0.000000
PCT17DO := 60.000000
PCT17IN := RB01
PCT18PU := 0.000000
PCT18DO := 60.000000
PCT18IN := RB02
PCT19PU := 0.000000
PCT19DO := 60.000000
PCT19IN := RB03
PCT20PU := 0.000000
PCT20DO := 60.000000
PCT20IN := RB04
PCT21PU := 0.000000
PCT21DO := 5.000000
PCT21IN := RB05
PCT22PU := 0.000000
PCT22DO := 5.000000
PCT22IN := RB06
#
#
#
#
PCT12PU := AMV116 # OBW TIMER
PCT12DO := 0.000000
PCT12IN := PSV01 # OBW QUALIFIER
#
PCT25PU := 60.000000
PCT25DO := 5.000000
PCT25IN := RB09
PCT26PU := 0.000000
PCT26DO := 60.000000
PCT26IN := RB10
PSV01 := ASV106 AND ASV116 AND NOT ASV004 AND ASV019 AND ASV055 # FOR TIMING OBW
PCT01PU := 0.000000
PCT01DO := 60.000000
PCT01IN := (RSTTRGT AND ASV068) OR TRGTR # TARGET RESET










































































































































