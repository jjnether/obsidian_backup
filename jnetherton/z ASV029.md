ASV029 := <span class="ob-html-comment" id="comment-fc5c38d8-a62e-4ae4-b63a-221a85a39909" data-tags="[comment,]"><span class="ob-html-comment-body">test inputs disabled</span>NOT ASV024</span> AND <span class="ob-html-comment" id="comment-80c302f7-bd7a-4d17-b37a-4ff8c9ef9e9d" data-tags="[comment,]"><span class="ob-html-comment-body">not in test mode</span>NOT ALT01</span> AND <span class="ob-html-comment" id="comment-965cadfe-668c-4f4f-b44b-a01d2ec9eb25" data-tags="[comment,]"><span class="ob-html-comment-body">no system test key</span>NOT IN310</span> AND ((<span class="ob-html-comment" id="comment-acd9a54b-2537-4bf1-aac8-a16d8b80b84c" data-tags="[comment,]"><span class="ob-html-comment-body">S1 52A</span>ASV101</span> AND <span class="ob-html-comment" id="comment-acdffd72-207b-4ae5-a0de-fc1c28741a20" data-tags="[comment,]"><span class="ob-html-comment-body">S1 52B</span>ASV102</span>) OR (<span class="ob-html-comment" id="comment-d855aa18-53ee-407d-b739-a170a239435d" data-tags="[comment,]"><span class="ob-html-comment-body">NOT 52A AND NOT 52B</span>NOT ASV101 AND NOT ASV102</span>) OR (<span class="ob-html-comment" id="comment-3caa78f5-5264-49c8-8837-079892d057da" data-tags="[comment,]"><span class="ob-html-comment-body">S2 52A and S2 52B</span>ASV111 AND ASV112</span>) OR (<span class="ob-html-comment" id="comment-934804a2-a3fc-4f88-828c-d95c317997e0" data-tags="[comment,]"><span class="ob-html-comment-body">S2 NOT 52A AND NOT 52B</span>NOT ASV111 AND NOT ASV112</span>))
- test inputs disabled
- not in test mode
- no system test key
	- S1 closed
	- S1 open
		- or 
	- S1 not closed
	- S1 not open
		- or
	- S2 closed
	- S2 open
		- or 
	- S2 not closed
	- S2 not open


ACT22PU := 1.000000 # LOCKOUT QUALIFYING TIMER PICKUP - SECONDS
ACT22DO := 0.000000 # LOCKOUT QUALIFYING TIMER DROPOUT - SECONDS
ACT22IN := ASV029 OR ASV163 OR ALT04 OR ALT24 OR NOT ASV121 OR ASV073 # LOCKOUT QUALIFYING TIMER


ALT04S := ((<span class="ob-html-comment" id="comment-e16f1500-7eb3-4a07-8ea6-236f1e4dffc2" data-tags="[comment,]"><span class="ob-html-comment-body">no S1 close or open operations happening</span>NOT ACT12Q</span> AND (<span class="ob-html-comment" id="comment-1030f585-2abf-4824-ae08-8484a5075028" data-tags="[comment,]"><span class="ob-html-comment-body">just lost S1 close status</span>F_TRIG ASV101</span> OR <span class="ob-html-comment" id="comment-77cd8a4c-cf0b-4de2-93aa-26a672511a40" data-tags="[comment,]"><span class="ob-html-comment-body">just lost S1 open status</span>F_TRIG ASV102</span>)) OR (<span class="ob-html-comment" id="comment-217a82bb-3159-4c0b-8e3c-5e0693cdb0bb" data-tags="[comment,]"><span class="ob-html-comment-body">no S2 close or open operations happening</span>NOT ACT13Q</span> AND (<span class="ob-html-comment" id="comment-f8551d10-f3bf-4628-9108-ebfb89b901b1" data-tags="[comment,]"><span class="ob-html-comment-body">S2 just lost closed status</span>F_TRIG ASV111</span> OR <span class="ob-html-comment" id="comment-6ab4a985-316d-4521-8e82-d500e09c3ff3" data-tags="[comment,]"><span class="ob-html-comment-body">S2 just lost open status</span>F_TRIG ASV112</span>))) AND <span class="ob-html-comment" id="comment-b6bb9aa7-3597-404a-974a-4a65f26c418c" data-tags="[comment,]"><span class="ob-html-comment-body">handles not active</span>NOT IN309</span> AND <span class="ob-html-comment" id="comment-351e624e-0fb7-43a9-b1d1-31e21bf77c61" data-tags="[comment,]"><span class="ob-html-comment-body">not in test mode or 2 sec out of test mode</span>NOT PCT29Q</span> # UNCOMMANDED OPERATION
- no S1 close or open operations happening
- just lost S1 close status
	- or
- just lost S1 open status
			- or
- no S2 close or open operations happening
- just lost S2 close status
	- or
- just lost S2 open status
- handles not active
- not in test mode or 2sec out of test mode


ALT04R := <span class="ob-html-comment" id="comment-6c771bc1-9d13-4980-955e-a5a1f973fc55" data-tags="[comment,]"><span class="ob-html-comment-body">target reset</span>PCT01Q</span>


ACT12PU := 0.000000 # SOURCE 1 UNCOMMANDED OPERATION PICKUP TIMER
ACT12DO := 2.000000 # SOURCE 1 UNCOMMANDED OPERATION DROPOUT TIMER - SECONDS
ACT12IN := (ASV231 OR ASV232) # SOURCE 1 UNCOMMANDED OPERATION TIMER

PCT29PU := 0.000000
PCT29DO := 120.000000 # 2 sec
PCT29IN := <span class="ob-html-comment" id="comment-692b7cfc-0ac9-40a9-b9ee-9ef538c8cec5" data-tags="[comment,]"><span class="ob-html-comment-body">test mode</span>ALT01</span>