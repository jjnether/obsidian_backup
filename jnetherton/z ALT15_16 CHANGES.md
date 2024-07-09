PLT14 == ALT15
PLT15 == ALT16
PCT02 == ACT15
PSV30 == ASV238
PCT04 == ACT17
PSV28 == ASV241
PSV49 == ASV198
PSV52 == ASV207
PSV42 == ASV209
PSV45 == ASV216

PSV27 == ASV236
PLT25 == ALT07
PCT05 == ACT09
PCT06 == ACT08


**Original**
ALT15S := R_TRIG <span class="ob-html-comment" id="comment-4c0c3fb2-6e64-48fb-bf9a-9d8e7e2b1d54" data-tags="[comment,]"><span class="ob-html-comment-body">S1 live</span>ASV107</span> AND <span class="ob-html-comment" id="comment-aaf4e185-9109-41bf-b799-3d81c7bed013" data-tags="[comment,]"><span class="ob-html-comment-body">S1 open</span>ASV102</span> AND <span class="ob-html-comment" id="comment-6c8f92a9-806c-43a1-9bdb-f65ed92a2a2d" data-tags="[comment,]"><span class="ob-html-comment-body">S1 preferred</span>ALT21</span> AND <span class="ob-html-comment" id="comment-90c0177f-9c1c-4b17-ae8f-e3a5285276c1" data-tags="[comment,]"><span class="ob-html-comment-body">S2 dead</span>ASV116</span> AND <span class="ob-html-comment" id="comment-5e313d1a-d8c4-48d0-9586-a102f98698cd" data-tags="[comment,]"><span class="ob-html-comment-body">S2 closed</span>ASV111</span> AND NOT AST08Q # RETURN TO SOURCE 1
ALT15R := (<span class="ob-html-comment" id="comment-2bb96ab4-c059-47a4-ac47-628a0d161f66" data-tags="[comment,]"><span class="ob-html-comment-body">S1 OPEN</span>ASV101</span> OR <span class="ob-html-comment" id="comment-14de66f1-f6c3-4708-83e8-3334be5be258" data-tags="[comment,]"><span class="ob-html-comment-body">S1 EXCESS RUN</span>ACT10Q</span>) AND ALT15

ACT15PU := AMV002 # SOURCE 1 RT TIME
ACT15DO := 0.000000
ACT15IN := ASV107 AND ALT21 AND ASV102 AND NOT ALT07 AND ASV055 # SOURCE 1 RT

ASV238 := (ASV116 AND NOT ALT26) AND (ASV107 AND ALT21 AND ASV102 AND NOT ALT07) OR R_TRIG ACT15Q OR (ASV238 AND NOT (ACT09Q OR PCT12Q)) # SOURCE 1 RT

ASV198 := (ASV238 AND ASV011) OR NOT ASV011 AND ASV112 AND F_TRIG ACT09Q # SOURCE 1 RTS CLOSE

ASV209 := (F_TRIG ACT08Q AND ASV111 AND ASV011) OR (ASV241 AND NOT ASV011) # SOURCE 1 OPEN COMMAND FOR S2 RT




**Bob's**
ALT15S := (<span class="ob-html-comment" id="comment-40101136-a43e-4d2d-a789-20a41b0330d1" data-tags="[comment,]"><span class="ob-html-comment-body">S2 dead</span>ASV116</span> AND <span class="ob-html-comment" id="comment-26b72592-8490-4b39-83b5-dff24517613c" data-tags="[comment,]"><span class="ob-html-comment-body">no OBW</span>NOT ALT26</span>) AND (<span class="ob-html-comment" id="comment-695764ee-f467-423e-b1d9-a44a83b17e69" data-tags="[comment,]"><span class="ob-html-comment-body">S1 live</span>ASV107</span> AND <span class="ob-html-comment" id="comment-ef38804f-0381-49a4-be86-69926536c8c7" data-tags="[comment,]"><span class="ob-html-comment-body">S1 preferred</span>ALT21</span> AND <span class="ob-html-comment" id="comment-7a24ec99-09c0-4a4f-9158-3fa96c51be7c" data-tags="[comment,]"><span class="ob-html-comment-body">S1 open</span>ASV102</span> AND <span class="ob-html-comment" id="comment-3bb37aae-0b80-46af-a76a-2858745812b4" data-tags="[comment,]"><span class="ob-html-comment-body">not S1 IT</span>NOT ALT07</span>) # EMERGENCY CLOSE SOURCE 1 DUE TO LOV WHILE TRANSFERRING BASED ON BOB'S POD
- S2 dead
- OBW didn't happen
- S1 live
- S1 preferred
- S1 open
- no S1 IT
ALT15R := ((<span class="ob-html-comment" id="comment-837879d6-12be-4266-9d76-670877f0ef77" data-tags="[comment,]"><span class="ob-html-comment-body">S1 closed</span>ASV101</span> AND <span class="ob-html-comment" id="comment-205cd3c4-3bf4-4cb4-bf58-403f69ff580e" data-tags="[comment,]"><span class="ob-html-comment-body">S2 open</span>ASV112</span>) OR <span class="ob-html-comment" id="comment-66b1758b-70c3-4b6f-b8fd-4912ebfba9d0" data-tags="[comment,]"><span class="ob-html-comment-body">comes out of test/auto mode</span>F_TRIG ASV055</span> OR ACT10Q) AND ALT15
- S1 closed
- S2 open
	- or
- comes out of test/auto mode


ACT15PU := AMV002 # S1 RT TIME
ACT15DO := AMV033 # 2 X BREAKER CYCLE TIME, IN CYCLES
ACT15IN := <span class="ob-html-comment" id="comment-9dc9c6f7-205f-429a-9d96-0cf039528b43" data-tags="[comment,]"><span class="ob-html-comment-body">S1 live</span>ASV107</span> AND <span class="ob-html-comment" id="comment-6de15d57-f6f9-41a6-bd35-4207fbf05cde" data-tags="[comment,]"><span class="ob-html-comment-body">S1 preferred</span>ALT21</span> AND <span class="ob-html-comment" id="comment-90b4e1b9-dff1-4226-a33b-0bbecd8b5b0b" data-tags="[comment,]"><span class="ob-html-comment-body">S1 open</span>ASV102</span> AND <span class="ob-html-comment" id="comment-2c92c75a-d15c-44cd-8eae-4c5df6ed0dd0" data-tags="[comment,]"><span class="ob-html-comment-body">S1 no IT</span>NOT ALT07</span> AND <span class="ob-html-comment" id="comment-a9fa530e-98cd-436e-b10d-88c450128b65" data-tags="[comment,]"><span class="ob-html-comment-body">test/auto mode</span>ASV055</span> AND <span class="ob-html-comment" id="comment-0c543503-92cb-4131-b46e-6928f42072e1" data-tags="[comment,]"><span class="ob-html-comment-body">no emergency close S1</span>NOT ALT15</span> # SOURCE 1 RT QUALIFIER
- S1 live
- S1 preferred
- S1 open
- S1 no IT
- test/auto mode
- no emergency close S1

ASV238 := R_TRIG <span class="ob-html-comment" id="comment-d41e0cae-c75b-49af-bf11-1c8911a70862" data-tags="[comment,]"><span class="ob-html-comment-body">S1 emergency close</span>ALT15</span> OR R_TRIG <span class="ob-html-comment" id="comment-5e61b709-e593-40e8-8dc6-ee6b99989450" data-tags="[comment,]"><span class="ob-html-comment-body">S1 RT</span>ACT15Q</span> OR (<span class="ob-html-comment" id="comment-680dc971-1120-4fc6-bb10-a627569af7c2" data-tags="[comment,]"><span class="ob-html-comment-body">S1 RT</span>ASV238</span> AND NOT (<span class="ob-html-comment" id="comment-812c8bb9-898b-4bce-8fec-2990dd7fa6d5" data-tags="[comment,]"><span class="ob-html-comment-body">RTID S1</span>ACT09Q</span> OR PCT12Q)) # RT SOURCE 1
- S1 emergency close
	- or
- S1 RT qualifier
	- or
- S1 RT
- no RTID S1 timing --and-- no PCT12

ASV198 := (<span class="ob-html-comment" id="comment-6a2b60c2-cc9e-4ce9-b9eb-dfe542dbb3d3" data-tags="[comment,]"><span class="ob-html-comment-body">RT S1</span>ASV238</span> AND (<span class="ob-html-comment" id="comment-ec9a512b-5f9f-41e1-bad1-1c1c847c26a2" data-tags="[comment,]"><span class="ob-html-comment-body">CBO RTS</span>ASV011</span> AND <span class="ob-html-comment" id="comment-d48eef13-01c2-4279-a7ca-92d24c1bb2b6" data-tags="[comment,]"><span class="ob-html-comment-body">NO S1 EMERGENCY CLOSE</span>NOT ALT15</span>)) OR (<span class="ob-html-comment" id="comment-4fb4e056-147e-403d-a6fa-4f119e30050f" data-tags="[comment,]"><span class="ob-html-comment-body">OBC RTS</span>NOT ASV011</span> OR <span class="ob-html-comment" id="comment-fb561f7f-39d1-4a39-a06b-08be93706351" data-tags="[comment,]"><span class="ob-html-comment-body">S1 EMERGENCY CLOSE</span>ALT15</span>) AND <span class="ob-html-comment" id="comment-9039fd76-a15e-482b-a183-4977a8ae6286" data-tags="[comment,]"><span class="ob-html-comment-body">S2 OPEN</span>ASV112</span> AND <span class="ob-html-comment" id="comment-7ecf5eee-a94a-4b52-bbef-b30359def633" data-tags="[comment,]"><span class="ob-html-comment-body">S1 RTID has timed out</span>F_TRIG ACT09Q</span> # SOURCE 1 RTS CLOSE
- S1 RT is timing
- CBO RTS
- no S1 emergency close
	- or
- S1 RTID has timed out
- S2 is open
- OBC RTS or S1 emergency close

ASV216 := (F_TRIG ACT09Q AND ASV101 AND (ASV011 AND NOT ALT15)) OR (ASV238 AND (NOT ASV011 OR ALT15)) # SOURCE 2 OPEN COMMAND FOR S1 RT
- S1 RTID has timed out
- S1 is closed
- CBO RTS
- no S1 emergency close
	- or
- S1 RT is timing
- OBC RTS or S1 emergency close

ASV209 := (F_TRIG <span class="ob-html-comment" id="comment-a74a6ee1-c7f6-4026-8c48-ef21c317844c" data-tags="[comment,]"><span class="ob-html-comment-body">RTID S2</span>ACT08Q</span> AND <span class="ob-html-comment" id="comment-a0abbbf1-310f-4d00-9512-2c69a0750fd6" data-tags="[comment,]"><span class="ob-html-comment-body">S2 closed</span>ASV111</span> AND (<span class="ob-html-comment" id="comment-0f101d7b-0762-445b-94a6-c32152c0532c" data-tags="[comment,]"><span class="ob-html-comment-body">CBO RTS</span>ASV011</span> AND <span class="ob-html-comment" id="comment-d7836814-504e-443b-ad6d-012f56a56ec1" data-tags="[comment,]"><span class="ob-html-comment-body">no S2 emergency close</span>NOT ALT16</span>)) OR (<span class="ob-html-comment" id="comment-45036fe7-00ae-48e2-8c4f-978ada8aa198" data-tags="[comment,]"><span class="ob-html-comment-body">S2 RT</span>ASV241</span> AND (<span class="ob-html-comment" id="comment-41aabf38-083f-41af-988c-7b63e62c9e48" data-tags="[comment,]"><span class="ob-html-comment-body">OBC RTS</span>NOT ASV011</span> OR <span class="ob-html-comment" id="comment-d80006f3-0369-4b6b-a714-f93099a8df85" data-tags="[comment,]"><span class="ob-html-comment-body">S2 emergency close</span>ALT16</span>)) # SOURCE 1 OPEN COMMAND FOR S2 RT
- S2 RTID has timed out
- S2 is closed
- CBO RTS
- no S2 emergency close
	- or
- S2 RT is timing
- OBC RTS or S2 emergency close


ALT26S := PCT12Q # OBW CHECK FOR EMERGENCY CLOSE
ALT26R := (<span class="ob-html-comment" id="comment-9dc9c6f7-205f-429a-9d96-0cf039528b43" data-tags="[comment,]"><span class="ob-html-comment-body">S1 live</span>ASV107</span> AND <span class="ob-html-comment" id="comment-0fe93d9c-f737-4729-9d6d-338eede2c5e4" data-tags="[comment,]"><span class="ob-html-comment-body">S1 open</span>ASV101</span>) OR (<span class="ob-html-comment" id="comment-d197bb7d-ab9d-4842-9909-88e4e32f0b65" data-tags="[comment,]"><span class="ob-html-comment-body">S2 live</span>ASV117</span> AND <span class="ob-html-comment" id="comment-a0abbbf1-310f-4d00-9512-2c69a0750fd6" data-tags="[comment,]"><span class="ob-html-comment-body">S2 open</span>ASV111</span>) OR <span class="ob-html-comment" id="comment-5fcc519f-e740-4990-a3f1-c30e95633c3a" data-tags="[comment,]"><span class="ob-html-comment-body">OBW OFF</span>NOT ASV019</span> OR <span class="ob-html-comment" id="comment-83c5b181-1c5c-407f-96fb-9c6899e568fe" data-tags="[comment,]"><span class="ob-html-comment-body">no test/auto mode</span>NOT ASV055</span>

PCT12PU := <span class="ob-html-comment" id="comment-2c9d64ec-78ca-44c5-b5ed-f4778edaf204" data-tags="[comment,]"><span class="ob-html-comment-body">OBW timer</span>AMV116</span> # OBW TIMER
PCT12DO := 0.000000
PCT12IN := PSV01 # OBW QUALIFIER

PSV01 := <span class="ob-html-comment" id="comment-223cfcff-8426-4a29-8677-f3177fe93d77" data-tags="[comment,]"><span class="ob-html-comment-body">S1 dead</span>ASV106</span> AND <span class="ob-html-comment" id="comment-152da9a5-6eb0-4552-9d15-b90e6f592de8" data-tags="[comment,]"><span class="ob-html-comment-body">S2 dead</span>ASV116</span> AND <span class="ob-html-comment" id="comment-3305e851-d433-470d-b435-5a57e2ff43cf" data-tags="[comment,]"><span class="ob-html-comment-body">gen not alternate</span>NOT ASV004</span> AND <span class="ob-html-comment" id="comment-16e38c13-12ac-40f1-88c1-a57cfeed6bdc" data-tags="[comment,]"><span class="ob-html-comment-body">OBW on</span>ASV019</span> AND <span class="ob-html-comment" id="comment-b2728ea4-8142-483a-a9ff-6f40ac02b8fe" data-tags="[comment,]"><span class="ob-html-comment-body">test/auto mode</span>ASV055</span> AND (<span class="ob-html-comment" id="comment-578371b0-7970-4949-b575-c68121b71f6b" data-tags="[comment,]"><span class="ob-html-comment-body">CBO ITS</span>ASV010</span> AND (<span class="ob-html-comment" id="comment-8b3bfec2-1810-41ba-b2ae-2bcf49190754" data-tags="[comment,]"><span class="ob-html-comment-body">no IT happening</span>NOT ALT08 AND NOT ALT07</span>) OR <span class="ob-html-comment" id="comment-fd1c9d7a-bf5d-43d8-9f7e-d028aadce58f" data-tags="[comment,]"><span class="ob-html-comment-body">OBC ITS</span>NOT ASV010</span>) # FOR TIMING OBW
- S1 dead
- S2 dead
- gen not alternate
- OBW active
- test/auto mode
- CBO ITS and no IT --or-- OBC ITS


ASV199 := (ASV197 OR ASV198 OR ACT23Q) AND AST06Q OR AST08Q # SOURCE 1 CLOSE FROM ITS, RTS, EMERGENCY, AND TRANSFER FAIL

AST06PT := 3.000000 # SECONDS - HARDCODED TO PROVIDE A BUFFER
AST06R := (NOT ASV107 OR F_TRIG ASV107)
AST06IN := ASV107 AND ASV055 # CLOSE DESTINATION SOURCE AFTER LOSS AND RETURN OF VOLTAGE DURING TRANSFER

AST08PT := AMV001 # S1 IT TIME
AST08R := NOT (ASV107 AND ALT07 AND (ASV112 AND NOT ASV010) AND ASV055 AND NOT ASV019) OR (ASV117 AND ASV055)
AST08IN := ASV107 AND ALT07 AND (ASV112 AND NOT ASV010) AND ASV055 AND NOT ASV019 # CLOSE ORIGINAL SOURCE DURING ITS TRANSFER FAIL TO SECONDARY SOURCE



- Originally (REV0 final), for emergency LOV with a CBO RT, preferred would immediately close, then non-preferred open after RTID
- New logic for emergency LOV with a CBO RT has non-preferred open, then close into the preferred after RTID