# BREAKER CLOSING OPENING IN TEST DISPLAY POINT LOGIC
ASV046 := ALT01 AND (OUT101 OR (PLT21 AND NOT AST12Q)) # SOURCE 1 OPENING
ASV047 := ALT01 AND (OUT102 OR (PLT20 AND NOT AST11Q)) # SOURCE 1 CLOSING
ASV048 := ALT01 AND (OUT103 OR (PLT23 AND NOT AST14Q)) # SOURCE 2 OPENING
ASV049 := ALT01 AND (OUT104 OR (PLT22 AND NOT AST13Q)) # SOURCE 2 CLOSING
#
# SOURCE LIVE IN TEST DISPLAY POINT LOGIC
ASV044 := ALT01 AND ASV107 # SOURCE 1 LIVE TEST
ASV045 := ALT01 AND ASV117 # SOURCE 2 LIVE TEST
ASV056 := ALT01 AND ASV106 # SOURCE 1 DEAD TEST
ASV057 := ALT01 AND ASV116 # SOURCE 2 DEAD TEST
#
# DISPLAY POINT TIMING IN TEST LOGIC
AST01PT := 999999.000000 # 999999 SECONDS
AST01R := (ASV232 AND ASV243) OR F_TRIG ALT01 OR F_TRIG ASV020 # SOURCE 1 OPEN VAR2
AST01IN := ASV020 AND ALT01 # SOURCE 1 IT INITIAL TIMING DISPLAY POINT
AST02PT := 999999.000000 # 999999 SECONDS
AST02R := ASV231 OR F_TRIG ALT01 OR F_TRIG ASV021 # SOURCE 1 CLOSE VAR2
AST02IN := ASV021 AND ALT01 # SOURCE 1 RT TRANSFER TIMING DISPLAY POINT
AST03PT := 999999.000000 # 999999 SECONDS
AST03R := ASV244 OR F_TRIG ALT01 OR F_TRIG ASV022 # SOURCE 2 OPEN VAR2
AST03IN := ASV022 AND ALT01 # SOURCE 2 IT TRANSFER TIMING DISPLAY POINT
AST04PT := 999999.000000 # 999999 SECONDS
AST04R := ASV243 OR F_TRIG ALT01 OR F_TRIG ASV023 # SOURCE 2 CLOSE VAR2
AST04IN := ASV023 AND ALT01 # SOURCE 2 RT TRANSFER TIMING DISPLAY POINT
AST05PT := 999999.000000 # 999999 SECONDS
AST05R := ASV231 OR ASV232 OR ASV243 OR ASV244 OR F_TRIG ALT01 # SOURCE 1/2 OPEN VAR2
AST05IN := (ACT09Q OR ACT08Q) AND ALT01 # RTID SOURCE 1 OR 2 DISPLAY POINT








































































