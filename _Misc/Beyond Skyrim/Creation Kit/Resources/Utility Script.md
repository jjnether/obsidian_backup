Collection of generic utility global functions

## Definition

## Properties

None

## Member Functions

None

## Global Functions

**String [GameTimeToString](https://ck.uesp.net/wiki/GameTimeToString_-_Utility "GameTimeToString - Utility")()**

-   Converts a float game time (in terms of game days passed) to a string detailing the date and time it represents.

**Float [GetCurrentGameTime](https://ck.uesp.net/wiki/GetCurrentGameTime_-_Utility "GetCurrentGameTime - Utility")()**

-   Obtains the current game time in terms of game days passed (the same as the global variable of a similar name)

**Float [GetCurrentRealTime](https://ck.uesp.net/wiki/GetCurrentRealTime_-_Utility "GetCurrentRealTime - Utility")()**

-   Obtains the number of real-world seconds that have passed since the game has launched (ignoring time alt-tabbed away, or other cases where the game might be frozen)

**Bool [IsInMenuMode](https://ck.uesp.net/wiki/IsInMenuMode_-_Utility "IsInMenuMode - Utility")()**

-   Returns whether the game is currently in "menu mode" or not.

**Float [RandomFloat](https://ck.uesp.net/wiki/RandomFloat_-_Utility "RandomFloat - Utility")(Float _afMin_, Float _afMax_)**

-   Generates a random float between the minimum and maximum (inclusive)

**Int [RandomInt](https://ck.uesp.net/wiki/RandomInt_-_Utility "RandomInt - Utility")(Int _aiMin_, Int _aiMax_)**

-   Generates a random integer between the minimum and maximum (inclusive)

**[SetINIFloat](https://ck.uesp.net/wiki/SetINIFloat_-_Utility "SetINIFloat - Utility")(String _ini_, Float _value_)**

-   Sets the float value of the associated INI entry.

**[SetINIInt](https://ck.uesp.net/wiki/SetINIInt_-_Utility "SetINIInt - Utility")(String _ini_, Int _value_)**

-   Sets the integer value of the associated INI entry.

**[SetINIBool](https://ck.uesp.net/wiki/SetINIBool_-_Utility "SetINIBool - Utility")(String _ini_, Bool _value_)**

-   Sets the boolean value of the associated INI entry.

**[SetINIString](https://ck.uesp.net/wiki/SetINIString_-_Utility "SetINIString - Utility")(String _ini_, String _value_)**

-   Sets the string value of the associated INI entry.

**[Wait](https://ck.uesp.net/wiki/Wait_-_Utility "Wait - Utility")(Float _afSeconds_)**

-   Pauses the script for at least the specified time (latent). Does not count time spent in a menu.

**[WaitGameTime](https://ck.uesp.net/wiki/WaitGameTime_-_Utility "WaitGameTime - Utility")(Float _afHours_)**

-   Pauses the script for at least the specified amount of game time (latent).

**[WaitMenuMode](https://ck.uesp.net/wiki/WaitMenuMode_-_Utility "WaitMenuMode - Utility")(Float _afSeconds_)**

-   Pauses the script for at least the specified time (latent). _Does_ count time spent in a menu.

**Int [GetCurrentMemory](https://ck.uesp.net/w/index.php?title=GetCurrentMemory_-_Utility&action=edit&redlink=1 "GetCurrentMemory - Utility (page does not exist)")()**

-   Returns the currently used memory amount. To use any other memory functions this must be called first as it sets up the memory stats used by the other functions.

**Int [GetBudgetCount](https://ck.uesp.net/w/index.php?title=GetBudgetCount_-_Utility&action=edit&redlink=1 "GetBudgetCount - Utility (page does not exist)")()**

**Int [GetCurrentBudget](https://ck.uesp.net/w/index.php?title=GetCurrentBudget_-_Utility&action=edit&redlink=1 "GetCurrentBudget - Utility (page does not exist)")(Int _aiBudgetNumber_)**

**Bool [OverBudget](https://ck.uesp.net/w/index.php?title=OverBudget_-_Utility&action=edit&redlink=1 "OverBudget - Utility (page does not exist)")(Int _aiBudgetNumber_)**

**String [GetBudgetName](https://ck.uesp.net/w/index.php?title=GetBudgetName-_Utility&action=edit&redlink=1 "GetBudgetName- Utility (page does not exist)")(Int _aiBudgetNumber_)**

### Global Functions Only Available in Beta

Frame Rate Capture functions were only available during beta versions, and are added here for completeness.

**String [CaptureFrameRate](https://ck.uesp.net/w/index.php?title=CaptureFrameRate_-_Utility&action=edit&redlink=1 "CaptureFrameRate - Utility (page does not exist)")(Int _numFrames_)**

-   Gets a string describing the frame rate for a certain number of frames, the string returned will never be longer then 1,000 characters and is separated by commas.

**[StartFrameRateCapture](https://ck.uesp.net/w/index.php?title=StartFrameRateCapture_-_Utility&action=edit&redlink=1 "StartFrameRateCapture - Utility (page does not exist)")()**

-   Starts a frame rate capture.

**[EndFrameRateCapture](https://ck.uesp.net/w/index.php?title=EndFrameRateCapture_-_Utility&action=edit&redlink=1 "EndFrameRateCapture - Utility (page does not exist)")()**

-   Ends a frame rate capture.

**[GetAverageFrameRate](https://ck.uesp.net/w/index.php?title=GetAverageFrameRate_-_Utility&action=edit&redlink=1 "GetAverageFrameRate - Utility (page does not exist)")()**

-   Returns the average frame rate during the capture.

**[GetMinFrameRate](https://ck.uesp.net/w/index.php?title=GetMinFrameRate_-_Utility&action=edit&redlink=1 "GetMinFrameRate - Utility (page does not exist)")()**

-   Returns the minimum frame rate during the capture.

**[GetMaxFrameRate](https://ck.uesp.net/w/index.php?title=GetMaxFrameRate_-_Utility&action=edit&redlink=1 "GetMaxFrameRate - Utility (page does not exist)")()**

-   Returns the maximum frame rate during the capture.