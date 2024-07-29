
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\451 ATC GWI UPDATE>)

QUESTIONS:
- There's always lockout active when there's external fault indication - do we want this?


TO DO:
- Need to double check logic for emergency transfer
	- emergency transfer is when we're on the alternate source, and we lose it, but the primary is back
	- should always be an OBC because we don't want to close into whatever caused us to lose the alternate

-   Clean up what we have now
-   Uncommanded operation (handle)
    -   Relay sees something tripped, but it didn't command that trip
-   Protection logic
    -   Guaranteed to execute in 1/8th of a cycle
    -   2 ms update times
    -   Custom protection functions
-   Automation logic
    -   Not guaranteed
    -   (70-75 ms update time)
-   Time (rising) stretchers
-   Pushbutton (command)
-   LED (status)



**Tips:**
- Can sorta use a sequencing timer as a conditioning timer by notting the IN value in the reset

Remove 51 timing and fault targeting
Remove single ph mech fail? - never used
Sync check - supposed to be included, but didn't work properly? - Nic
Blocks operation based on FCI input, but we can just implement to use CT's instead of FCI
-   Use current for transfer block (analog rather than FCI's)
Nic - Eversource errors, discrepancies, DNP stuff?



Scope
-   Auto and local mode can be moved to automation from protection
-   No delay for 50 element (holds for time then trips) (50P1D, 50P1G)
-   We use firmware z19 - what comes with newer firmware (z30)? New signals? New optimization?
-   Test mode - is it still useful? Should we get rid of it?
-   Add solid dielectric or gas in design template - IN107 (low SF6 pressure) is normally hardwired for SolidDi



SEL-351S-6-R516-V0-Z106105-D20150202
0351S6XH42F1122


In frame:
SEL-451-5-R314-V2-Z019012-D20220630
0451521DXC4X1H74171XX
1112150358



On table:
SEL-451-5-R327-V0-Z030014-D20221209
04515211XXXX1H74141XX

Examples:
-   UofHouston - return transfer
-   DSM_freeport - stripped down ATC
-   UofOregon - no ATC, but 451 for protection (50P delay and 50G delay incorporated into protection logic



**Don't transfer on a fault** (on source 1 or 2)
- FCI's currently block transfer, and maybe take it out of auto? (should it take it out of auto?)


**If RTS is CBO and you're timing for a return, but you lose the source you're on, it'll transfer immediately with CBO. In an emergency like this, it always needs to be OBC.**
- X:\DA\Dept\_Lazer\91484 - City of Columbus - PEPCO\91484_00 - Current Program & Documentation

**PPL - sync on CBO return transfer, logic moved to Automation, logic diagrams, test mode removed, removed ITS CBO**
- X:\DA\Dept\_Lazer\101824 - PPL (ATC Modifications)\0_Current Program and Documentation


Add aliases when finished with the program
Should we keep AST06/AST07? - hardcoded to provide a set buffer - if so, may need to specify in GWI?
Update AST06/AST07 comments - maybe should just be "s1 stable"
For Bob's ALT15R/ALT16R, should we include excess run, as it is originally?
Based on Bob's changes, added back in AMV033 for ACT15DO/ACT17DO
Need to check if "ASV007 AND ASV208" is necessary in ASV235
Why have ACT12? - it just makes sure that uncommanded operation checks for no current operations, PLUS an additional 2 sec after those drop out


Move close logic to protection? (along with sync check)
Move lines calculating 50 elements to protection


I think this is an actual logic issue, that's easy to fix if you are still working on the ATC revamp.  The logic should take into consideration if it is in preferred source mode or non-preferred mode.
Current - PSV26 := (ASV202 AND F_TRIG PLT18) OR (ASV202 AND F_TRIG PLT19) # EXIT AUTO ON "NO RETURN SEQUENCE" VARIABLE
New - PSV26 := (ASV202 AND F_TRIG PLT18 AND ASV001) OR (ASV202 AND F_TRIG PLT19 AND ASV002) # EXIT AUTO ON "NO RETURN SEQUENCE" VARIABLE
OR
New - PSV26 := ASV003 and ((ASV202 AND F_TRIG PLT18) OR (ASV202 AND F_TRIG PLT19)) # EXIT AUTO ON "NO RETURN SEQUENCE" VARIABLE
where:
ASV001 = S1 Preferred
ASV002 = S2 Preferred
ASV003 = Non-Preferred


Get feedback from Enio regarding new test mode with local bits (keep logic intact, but make it use actual logic instead of its own test logic)


- New GWI for this iteration
- All documentation will need to be reviewed after changes are finalized
- Update DNP maps
- Do we want Aliases?
	- Add to the GWI
- Guide spec?
	- describes ATC 451, as it's supoosed to be used
	- customer copies and puts it in their own spec
	- let's us put our particulars in


(PLT27 AND NOT ASV203) OR ( AND ASV203) # W WAY A PH FAULT