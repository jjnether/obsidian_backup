Collection of debug-related global functions

## Definition

`ScriptName Debug`

## Properties

None

## Global Functions

**[CenterOnCell](https://ck.uesp.net/wiki/CenterOnCell_-_Debug "CenterOnCell - Debug")(String _asCellName_)**

-   Teleports the player to the specified cell.

**Float [CenterOnCellAndWait](https://ck.uesp.net/wiki/CenterOnCellAndWait_-_Debug "CenterOnCellAndWait - Debug")(String _asCellName_)**

-   Teleports the player to the specified cell and doesn't return until he gets there.

**Float [PlayerMoveToAndWait](https://ck.uesp.net/wiki/PlayerMoveToAndWait_-_Debug "PlayerMoveToAndWait - Debug")(String _asDestRef_)**

-   Teleports the player to the specified reference and doesn't return until he gets there.

**[CloseUserLog](https://ck.uesp.net/wiki/CloseUserLog_-_Debug "CloseUserLog - Debug")(String _asLogName_)**

-   Closes the specified user log

**[DumpAliasData](https://ck.uesp.net/wiki/DumpAliasData_-_Debug "DumpAliasData - Debug")(Quest _akQuest_)**

-   Dumps all alias fill information to the alias dump log.

**String [GetConfigName](https://ck.uesp.net/wiki/GetConfigName_-_Debug "GetConfigName - Debug")()**

-   Obtains the build configuration name

**String [GetPlatformName](https://ck.uesp.net/wiki/GetPlatformName_-_Debug "GetPlatformName - Debug")()**

-   Obtains the current platform name

**String [GetVersionNumber](https://ck.uesp.net/wiki/GetVersionNumber_-_Debug "GetVersionNumber - Debug")()**

-   Obtains the current version number

**[MessageBox](https://ck.uesp.net/wiki/MessageBox_-_Debug "MessageBox - Debug")(String _asMessageBoxText_)** ^29ea68

-   Displays an OK message box with the specified text

**[Notification](https://ck.uesp.net/wiki/Notification_-_Debug "Notification - Debug")(String _asNotificationText_)**

-   Displays an in-game notification message (on the top-left corner)

**Bool [OpenUserLog](https://ck.uesp.net/wiki/OpenUserLog_-_Debug "OpenUserLog - Debug")(String _asLogName_)**

-   Opens the specified user log (fails if already open)

**[QuitGame](https://ck.uesp.net/wiki/QuitGame_-_Debug "QuitGame - Debug")()**

-   Quits the game

**[SetFootIK](https://ck.uesp.net/wiki/SetFootIK_-_Debug "SetFootIK - Debug")(Bool _abFootIK_)**

-   Turns foot IK on and off

**[SetGodMode](https://ck.uesp.net/wiki/SetGodMode_-_Debug "SetGodMode - Debug")(Bool _abGodMode_)**

-   Turns god mode on and off

**[SendAnimationEvent](https://ck.uesp.net/wiki/SendAnimationEvent_-_Debug "SendAnimationEvent - Debug")(ObjectReference _arRef_, String _asEventName_)**

-   Sends an animation event to the specified reference.

**[StartScriptProfiling](https://ck.uesp.net/wiki/StartScriptProfiling_-_Debug "StartScriptProfiling - Debug")(String _asScriptName_)**

-   Starts profiling a specific Papyrus script

**[StartStackProfiling](https://ck.uesp.net/wiki/StartStackProfiling_-_Debug "StartStackProfiling - Debug")()**

-   Starts profiling the calling stack

**[StopScriptProfiling](https://ck.uesp.net/wiki/StopScriptProfiling_-_Debug "StopScriptProfiling - Debug")(String _asScriptName_)**

-   Stops profiling a specific Papyrus script

**[StopStackProfiling](https://ck.uesp.net/wiki/StopStackProfiling_-_Debug "StopStackProfiling - Debug")()**

-   Stops profiling the calling stack

**[ToggleAI](https://ck.uesp.net/wiki/ToggleAI_-_Debug "ToggleAI - Debug")()**

-   Turns AI on and off.

**[ToggleCollisions](https://ck.uesp.net/wiki/ToggleCollisions_-_Debug "ToggleCollisions - Debug")()**

-   Turns collision on and off.

**[ToggleMenus](https://ck.uesp.net/wiki/ToggleMenus_-_Debug "ToggleMenus - Debug")()**

-   Toggles menus on and off.

**[Trace](https://ck.uesp.net/wiki/Trace_-_Debug "Trace - Debug")(String _asTextToPrint_, Int _aiSeverity_)**

-   Outputs the string to the Papyrus log and debug text page

**[TraceAndBox](https://ck.uesp.net/wiki/TraceAndBox_-_Debug "TraceAndBox - Debug")(String _asTextToPrint_, Int _aiSeverity_)**

-   Outputs the string to the log and puts up a message box

**[TraceConditional](https://ck.uesp.net/wiki/TraceConditional_-_Debug "TraceConditional - Debug")(String _TextToPrint_, Bool _ShowTrace_)**

-   Outputs the string to the Papyrus log, but only if the condition is true

**[TraceStack](https://ck.uesp.net/wiki/TraceStack_-_Debug "TraceStack - Debug")(String _asTextToPrint_, Int _aiSeverity_)**

-   Outputs the string to the Papyrus log and debug text page, along with a full call stack

**Bool [TraceUser](https://ck.uesp.net/wiki/TraceUser_-_Debug "TraceUser - Debug")(String _asUserLog_, String _asTextToPrint_, Int _aiSeverity_)**

-   Outputs the string to the specified user log (and debug text page)

## Member Functions

None

## Events

None