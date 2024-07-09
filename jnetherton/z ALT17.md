ALT17S := AST08Q # USED IN PLT18
ALT17R := R_TRIG ASV101

PLT18S := R_TRIG <span class="ob-html-comment" id="comment-c9e2acb0-bd23-4b54-b3e4-4e6b35b2e47a" data-tags="[comment,]"><span class="ob-html-comment-body">start ITS to S2</span>ASV236</span> # SOURCE 1 ITS OPEN LATCH SET
PLT18R := (F_TRIG <span class="ob-html-comment" id="comment-dff6b8fc-5b80-4c80-b948-123cd8444f6c" data-tags="[comment,]"><span class="ob-html-comment-body">S2 close</span>ASV243</span> AND <span class="ob-html-comment" id="comment-b846a12f-b211-4a2a-b7aa-46994b6cb741" data-tags="[comment,]"><span class="ob-html-comment-body">ITS OBC</span>NOT ASV010</span>) OR (F_TRIG <span class="ob-html-comment" id="comment-45bd52ec-95ef-4f0f-9dd3-3348104ac766" data-tags="[comment,]"><span class="ob-html-comment-body">S1 open</span>ASV232</span> AND <span class="ob-html-comment" id="comment-89f68aaa-529d-4360-8838-9e5b53c1af48" data-tags="[comment,]"><span class="ob-html-comment-body">ITS CBO</span>ASV010</span>) OR F_TRIG ALT17 # SOURCE 1 ITS OPEN LATCH RESET

PSV26 := (<span class="ob-html-comment" id="comment-e83fd2c1-d4db-46a7-8b32-36965125df78" data-tags="[comment,]"><span class="ob-html-comment-body">RTS disabled</span>ASV202</span> AND F_TRIG PLT18) OR (<span class="ob-html-comment" id="comment-0f5e79dd-9e1f-444b-ada0-60cc910fe6d6" data-tags="[comment,]"><span class="ob-html-comment-body">RTS disabled</span>ASV202</span> AND F_TRIG PLT19) # EXIT AUTO ON "NO RETURN SEQUENCE" VARIABLE

ALT05S := PSV26 # LATCHING "EXIT AUTO ON NO RETURN SEQUENCE"
ALT05R := NOT ALT01

ALT01S := ALT23 AND R_TRIG PB4 AND NOT ASV141 AND NOT ALT01 AND ASV069 # SET TEST MODE
ALT01R := R_TRIG PB4 AND ALT01 OR ASV141 OR NOT ALT23 OR PFRTEX OR ALT05 # RESET TEST MODE


ALT20R := ((R_TRIG PB2 OR (IN306 OR PCT18Q) AND NOT ALT01 AND NOT ALT23) AND ALT20) OR ASV141 OR ALT23 OR PSV26 OR (IN201 OR IN202) # RESET AUTOMATIC MODE ENABLE

AST08PT := AMV001 # S1 IT TIME
AST08R := NOT (ASV107 AND ALT07 AND (ASV112 AND NOT ASV010) AND ASV055 AND NOT ASV019) OR (ASV117 AND ASV055)
AST08IN := ASV107 AND ALT07 AND (ASV112 AND NOT ASV010) AND ASV055 AND NOT ASV019 # CLOSE ORIGINAL SOURCE DURING ITS TRANSFER FAIL TO SECONDARY SOURCE