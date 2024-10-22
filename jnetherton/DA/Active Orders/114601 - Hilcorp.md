
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\114601 - Hilcorp Alaska>)

Things to note:
- Relay identifiers can only be 16 characters, so I had to slightly shorten the identifiers requested
- 81 underfrequency trip was requested for Way 1, but because there is no fault interrupter on that way, so I am treating it the same as we did last order where, upon an underfrequency event, there will be no operation, but the relay will provide indication via target LED. This LED will latch and can be reset via the TARGET RESET pushbutton.
- The customer remote trip for way 1 will only be available when way 1 is in remote mode
- Meter cutoff threshold is enabled on all relays