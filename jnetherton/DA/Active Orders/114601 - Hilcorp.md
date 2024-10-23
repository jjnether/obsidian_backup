
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\114601 - Hilcorp Alaska>)

Things to note:
- Relay identifiers can only be 16 characters, so I shortened the identifiers requested to the following:
	- SG-4502 W1_MAIN
	- SG-4502 W2_RIG
	- SG-4502 W3_VFD
	- SG-4502 W4_PAD
- 81 underfrequency trip was requested for Way 1, but because there is no fault interrupter on that way, so I am treating it the same as we did last order where, upon an underfrequency event, there will be no operation, but the relay will provide indication via target LED. This LED will latch and can be reset via the TARGET RESET pushbutton.
- The customer remote trip for way 1 will only be available when way 1 is in remote mode
	- IN304 is wetted and wired to the terminal block, so customer only needs dry contacts to activate the remote open on Way 1
- Meter cutoff threshold is enabled on all relays
	- This was the setting that was Brendon disabled on the past order due to the relay not showing the very low current levels