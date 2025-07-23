
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\451 ATC GWI UPDATE>)

Source 1 ITS = transferring FROM source 1 TO source 2
Source 1 RTS = transferring BACK TO source 1

QUESTIONS:
- Need to double check logic for emergency transfer
	- emergency transfer is when we're on the alternate source, and we lose it, but the primary is back
	- should always be an OBC because we don't want to close into whatever caused us to lose the alternate
- Might want to add a block where if source 1 is open and dead and source 2 is closed and live, we can't close the live source into the dead source (vice versa for S1 live and S2 dead)


-   Protection logic
    -   Guaranteed to execute in 1/8th of a cycle
    -   2 ms update times
-   Automation logic
    -   ~75 ms update time , variable time (can check with `STA S` command)

Remove 51 timing and fault targeting
Remove single ph mech fail? - never used
Blocks operation based on FCI input, but we can just implement to use CT's instead of FCI
-   Use current for transfer block (analog rather than FCI's)
Nic - Eversource errors, discrepancies, DNP stuff?


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
- FCI's currently block transfer, and take it out of auto? (should it take it out of auto?)

**If RTS is CBO and you're timing for a return, but you lose the source you're on, it'll transfer immediately with CBO. In an emergency like this, it always needs to be OBC.**
- `X:\DA\Dept\_Lazer\91484 - City of Columbus - PEPCO\91484_00 - Current Program & Documentation`

**PPL - sync on CBO return transfer, logic moved to Automation, logic diagrams, test mode removed, removed ITS CBO**
- `X:\DA\Dept\_Lazer\101824 - PPL (ATC Modifications)\0_Current Program and Documentation`


Should we keep AST06/AST07? - hardcoded to provide a set buffer - if so, may need to specify in GWI?
Update AST06/AST07 comments - maybe should just be "s1 stable"
For Bob's ALT15R/ALT16R, should we include excess run, as it is originally?
Why have ACT12? - it just makes sure that uncommanded operation checks for no current operations, PLUS an additional 2 sec after those drop out


I think this is an actual logic issue, that's easy to fix if you are still working on the ATC revamp.  The logic should take into consideration if it is in preferred source mode or non-preferred mode.
Current - PSV26 := (ASV202 AND F_TRIG PLT18) OR (ASV202 AND F_TRIG PLT19) # EXIT AUTO ON "NO RETURN SEQUENCE" VARIABLE
New - PSV26 := (ASV202 AND F_TRIG PLT18 AND ASV001) OR (ASV202 AND F_TRIG PLT19 AND ASV002) # EXIT AUTO ON "NO RETURN SEQUENCE" VARIABLE
OR
New - PSV26 := ASV003 and ((ASV202 AND F_TRIG PLT18) OR (ASV202 AND F_TRIG PLT19)) # EXIT AUTO ON "NO RETURN SEQUENCE" VARIABLE
where:

NEED TO ADD/TEST:
- Refer to AMS case where all initial, return, and RTID timers are set to 0, source paralleling is allowed, and no return transfers, all open transition. They had a lightning strike and the ATC saw a voltage loss for an instant, initiating a transfer, but the voltage was immediately back
	- add a state machine for transfers - there should only ever be 1 transfer at a time
		- So when you start an transfer, a latch sets, preventing any other transfers - once that transfer is completed, the latch resets
	- In the case of if both sources come back simultaneously, might need a tiebreaker to decide which one closes?





- New GWI for this iteration
- All documentation will need to be reviewed after changes are finalized
- Update DNP maps
- Do we want Aliases?
	- Add to the GWI
- Guide spec?
	- describes ATC 451, as it's supposed to be used
	- customer copies and puts it in their own spec
	- let's us put our particulars in

ASV001 = S1 Preferred
ASV002 = S2 Preferred
ASV003 = Non-Preferred
ASV101 = SRC 1 52A
ASV102 = SRC 1 52B
ASV111 = SRC 2 52A
ASV112 = SRC 2 52B

NOT ASV141 AND (NOT ALT07 OR PCT12Q) AND ((NOT ALT02 AND ASV061) OR (ASV055 AND (R_TRIG PCT12Q AND ASV111 OR R_TRIG ASV222))) # SOURCE 2 OPEN
- not in lockout
- S1 not in ITS or OBW
- not in auto and 



G&W to program SEL-451 to accommodate the below:

1)    If an initial transfer has taken place and the load is being fed from the secondary source, the control will monitor the primary source for a return of healthy voltage.

2)    Upon the return of healthy voltage on the primary source, the control will begin timing for a return transfer using the Return Transfer Timer as set by the user.

3)    The return transfer shall be executed in one of the two following ways:

a.    If the secondary source voltage remains healthy for the duration of the Return Transfer Timer, the control shall initiate a return transfer in the sequence as set by the user (Open Before Close or Close Before Open).

b.    If there is a loss of the secondary source voltage during the Return Transfer Timer, the control shall initiate a return transfer in an Open Before Close sequence.

4)    The control will only ever transfer from preferred source to alternate source if the preferred source is dead (following the Initial Transfer Sequence).  To comply with the City of Columbus requirements, the Initial Transfer Sequence setting must be set to Open Before Close.

5)    Factory Acceptance Test (FAT) at G&W factory in Bolingbrook, IL to verify functionality of SEL-451 programming as per points 1)-4) above. G&W to host conference call with screensharing ability for City of Columbus to attend and witness FAT remotely.