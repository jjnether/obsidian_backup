OUT101 := ASV232 AND ASV043 AND NOT IN201 AND NOT AST15Q # OPEN SOURCE 1
OUT102 := ASV231 AND ASV043 AND NOT IN201 AND NOT AST15Q AND ASV223 # CLOSE SOURCE 1
OUT103 := ASV244 AND ASV043 AND NOT IN202 AND NOT AST15Q # OPEN SOURCE 2
OUT104 := ASV243 AND ASV043 AND NOT IN202 AND NOT AST15Q AND ASV233 # CLOSE SOURCE 2
OUT107 := NOT ASV121 OR ASV140 # LOW SF6 / S1/S2 FAULT ALARM
OUT108 := ASV214 # BATTERY TEST COMMAND OUTPUT

OUT201 := (PLT04 OR PLT27) AND NOT ALT10 OR PLT01 # TRIP WAY W
OUT202 := (PLT07 OR PLT30) AND NOT ALT11 OR PLT02 # TRIP WAY X
OUT203 := PLT31 AND NOT ALT11 OR PLT02 AND (SG2 OR SG4) # TRIP WAY X B-PHASE
OUT204 := PLT32 AND NOT ALT11 OR PLT02 AND (SG2 OR SG4) # TRIP WAY X C-PHASE
OUT205 := PLT28 AND NOT ALT10 OR PLT01 AND (SG2 OR SG4) # TRIP WAY W B-PHASE
OUT206 := PLT29 AND NOT ALT10 OR PLT01 AND (SG2 OR SG4) # TRIP WAY W C-PHASE
OUT207 := ALT20 # AUTO MODE
OUT208 := ALT23 # LOCAL MODE

OUT301 := PLT13 # GENERATOR START COMMAND
OUT302 := ACT21Q # GENERATOR STOP COMMAND