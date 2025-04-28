Native base script for every [form](https://ck.uesp.net/wiki/Glossary#Form "Glossary") in the game.

## Definition

```
ScriptName Form
```

## Properties

None

## Global Functions

None

## Member Functions

**Int [GetFormID](https://ck.uesp.net/wiki/GetFormID_-_Form "GetFormID - Form")()**

-   Returns this form's form ID.

**Int [GetGoldValue](https://ck.uesp.net/wiki/GetGoldValue_-_Form "GetGoldValue - Form")()**

-   Returns this form's value in gold.

**Bool [HasKeyword](https://ck.uesp.net/wiki/HasKeyword_-_Form "HasKeyword - Form")(Keyword _akKeyword_)**

-   Returns if this form has the specified [Keyword](https://ck.uesp.net/wiki/Keyword_Script "Keyword Script") attached.

**Bool [PlayerKnows](https://ck.uesp.net/wiki/PlayerKnows_-_Form "PlayerKnows - Form")()**

-   Is the "Known" flag set on the form?

**[RegisterForAnimationEvent](https://ck.uesp.net/wiki/RegisterForAnimationEvent_-_Form "RegisterForAnimationEvent - Form")(ObjectReference _akSender_, String _asEventName_)**

-   Registers this form to receive the specified animation event from the specified object.

**[RegisterForLOS](https://ck.uesp.net/wiki/RegisterForLOS_-_Form "RegisterForLOS - Form")(Actor _akViewer_, ObjectReference _akTarget_)**

-   Registers this form to receive gain and lost LOS events between the viewer and the target.

**[RegisterForSingleLOSGain](https://ck.uesp.net/wiki/RegisterForSingleLOSGain_-_Form "RegisterForSingleLOSGain - Form")(Actor _akViewer_, ObjectReference _akTarget_)**

-   Registers this form to receive a single LOS gain event when the viewer sees the target.

**[RegisterForSingleLOSLost](https://ck.uesp.net/wiki/RegisterForSingleLOSLost_-_Form "RegisterForSingleLOSLost - Form")(Actor _akViewer_, ObjectReference _akTarget_)**

-   Registers this form to receive a single LOS lost event when the viewer loses sight of the target.

**[RegisterForSingleUpdate](https://ck.uesp.net/wiki/RegisterForSingleUpdate_-_Form "RegisterForSingleUpdate - Form")(Float _afInterval_)**

-   Registers this form to receive a single update event in the specified time.

**[RegisterForSingleUpdateGameTime](https://ck.uesp.net/wiki/RegisterForSingleUpdateGameTime_-_Form "RegisterForSingleUpdateGameTime - Form")(Float _afInterval_)**

-   Registers this form to receive a single update event in the specified number of game hours.

**[RegisterForSleep](https://ck.uesp.net/wiki/RegisterForSleep_-_Form "RegisterForSleep - Form")()**

-   Registers this form to receive sleep events for when the player goes to sleep or wakes up.

**[RegisterForTrackedStatsEvent](https://ck.uesp.net/wiki/RegisterForTrackedStatsEvent_-_Form "RegisterForTrackedStatsEvent - Form")()**

-   Registers this form to receive tracked stats events for when tracked stats are updated.

**[RegisterForUpdate](https://ck.uesp.net/wiki/RegisterForUpdate_-_Form "RegisterForUpdate - Form")(Float _afInterval_)**

-   Registers this form to receive update events with the specified interval, or changes the update interval.

**[RegisterForUpdateGameTime](https://ck.uesp.net/wiki/RegisterForUpdateGameTime_-_Form "RegisterForUpdateGameTime - Form")(Float _afInterval_)**

-   Registers this form to receive update events with the specified interval in game time hours, or changes the update interval.

**[StartObjectProfiling](https://ck.uesp.net/wiki/StartObjectProfiling_-_Form "StartObjectProfiling - Form")()**

-   Starts profiling all scripts attached to this form.

**[StopObjectProfiling](https://ck.uesp.net/wiki/StopObjectProfiling_-_Form "StopObjectProfiling - Form")()**

-   Stops profiling all scripts attached to this form.

**[UnregisterForAnimationEvent](https://ck.uesp.net/wiki/UnregisterForAnimationEvent_-_Form "UnregisterForAnimationEvent - Form")(ObjectReference _akSender_, String _asEventName_)**

-   Unregisters this from from receiving the specified animation event from the specified object.

**[UnregisterForLOS](https://ck.uesp.net/wiki/UnregisterForLOS_-_Form "UnregisterForLOS - Form")(Actor _akViewer_, ObjectReference _akTarget_)**

-   Unregisters this form from any LOS events between the viewer and target.

**[UnregisterForSleep](https://ck.uesp.net/wiki/UnregisterForSleep_-_Form "UnregisterForSleep - Form")()**

-   Unregisters this form from sleep events.

**[UnregisterForTrackedStatsEvent](https://ck.uesp.net/wiki/UnregisterForTrackedStatsEvent_-_Form "UnregisterForTrackedStatsEvent - Form")()**

-   Unregisters this form from tracked stats events.

**[UnregisterForUpdate](https://ck.uesp.net/wiki/UnregisterForUpdate_-_Form "UnregisterForUpdate - Form")()**

-   Unregisters this form from update events.

**[UnregisterForUpdateGameTime](https://ck.uesp.net/wiki/UnregisterForUpdateGameTime_-_Form "UnregisterForUpdateGameTime - Form")()**

-   Unregisters this form from game time update events.

## SKSE Member Functions

**Int [GetType](https://ck.uesp.net/wiki/GetType_-_Form "GetType - Form")()**

-   Returns this form's form typecode.

**String [GetName](https://ck.uesp.net/wiki/GetName_-_Form "GetName - Form")()**

-   Returns this form's full name.

**[SetName](https://ck.uesp.net/wiki/SetName_-_Form "SetName - Form")(String _name_)**

-   Sets this form's full name.

**Float [GetWeight](https://ck.uesp.net/wiki/GetWeight_-_Form "GetWeight - Form")()**

-   Returns this form's weight.

**[SetWeight](https://ck.uesp.net/wiki/SetWeight_-_Form "SetWeight - Form")(Float _weight_)**

-   Sets this form's weight.

**[SetGoldValue](https://ck.uesp.net/wiki/SetGoldValue_-_Form "SetGoldValue - Form")(Int _value_)**

-   Sets this form's base gold value.

**Int [GetNumKeywords](https://ck.uesp.net/wiki/GetNumKeywords_-_Form "GetNumKeywords - Form")()**

-   Returns the number of keywords on this form.

**Keyword [GetNthKeyword](https://ck.uesp.net/wiki/GetNthKeyword_-_Form "GetNthKeyword - Form")(Int _index_)**

-   Returns the keyword specified by index on this form.

**Bool [HasKeywordString](https://ck.uesp.net/wiki/HasKeywordString_-_Form "HasKeywordString - Form")(String _s_)**

-   Returns whether this form has a keyword with the specified string.

**[SetPlayerKnows](https://ck.uesp.net/w/index.php?title=SetPlayerKnows_-_Form&action=edit&redlink=1 "SetPlayerKnows - Form (page does not exist)")(Bool _knows_)**

-   Sets whether the player know this form. Should only be used For Magic Effects, Words of Power and Enchantments.

**Bool [IsPlayable](https://ck.uesp.net/w/index.php?title=IsPlayable_-_Form&action=edit&redlink=1 "IsPlayable - Form (page does not exist)")()**

-   Returns if the form is marked playable or not. Only works on forms that have that flag, such as Armors.

**Bool [HasWorldModel](https://ck.uesp.net/w/index.php?title=HasWorldModel_-_Form&action=edit&redlink=1 "HasWorldModel - Form (page does not exist)")()**

-   Returns whether this form has a world model or not.

**String [GetWorldModelPath](https://ck.uesp.net/w/index.php?title=GetWorldModelPath_-_Form&action=edit&redlink=1 "GetWorldModelPath - Form (page does not exist)")()**

-   Gets this form's world model.

**[SetWorldModelPath](https://ck.uesp.net/wiki/SetWorldModelPath_-_Form "SetWorldModelPath - Form")(String _path_)**

-   Sets this form's world model.

**Int [GetWorldModelNumTextureSets](https://ck.uesp.net/w/index.php?title=GetWorldModelNumTextureSets_-_Form&action=edit&redlink=1 "GetWorldModelNumTextureSets - Form (page does not exist)")()**

-   Returns the number of texture sets the world model has.

**TextureSet [GetWorldModelNthTextureSet](https://ck.uesp.net/w/index.php?title=GetWorldModelNthTextureSet_-_Form&action=edit&redlink=1 "GetWorldModelNthTextureSet - Form (page does not exist)")(Int _n_)**

-   Returns the Nth texture set of the forms world model.

**[SetWorldModelNthTextureSet](https://ck.uesp.net/w/index.php?title=SetWorldModelNthTextureSet_-_Form&action=edit&redlink=1 "SetWorldModelNthTextureSet - Form (page does not exist)")(TextureSet _nSet_, Int _n_)**

-   Sets the Nth texture set of the forms world model to the specified TextureSet.

**[RegisterForKey](https://ck.uesp.net/wiki/RegisterForKey_-_Form "RegisterForKey - Form")(Int _keyCode_)**

-   Registers the given [DXScanCode](https://ck.uesp.net/wiki/Input_Script#DXScanCodes "Input Script") for OnKeyDown and OnKeyUp events.

**[UnregisterForKey](https://ck.uesp.net/wiki/UnregisterForKey_-_Form "UnregisterForKey - Form")(Int _keyCode_)**

-   Unregisters the given [DXScanCode](https://ck.uesp.net/wiki/Input_Script#DXScanCodes "Input Script") for OnKeyDown and OnKeyUp events.

**[UnregisterForAllKeys](https://ck.uesp.net/wiki/UnregisterForAllKeys_-_Form "UnregisterForAllKeys - Form")()**

-   Unregisters all registered [DXScanCodes](https://ck.uesp.net/wiki/Input_Script#DXScanCodes "Input Script").

**[RegisterForControl](https://ck.uesp.net/wiki/RegisterForControl_-_Form "RegisterForControl - Form")(String _control_)**

-   Registers the given control for OnControlDown and OnControlUp events.

**[UnregisterForControl](https://ck.uesp.net/wiki/UnregisterForControl_-_Form "UnregisterForControl - Form")(String _control_)**

-   Unregisters the given control for OnControlDown and OnControlUp events.

**[UnregisterForAllControls](https://ck.uesp.net/wiki/UnregisterForAllControls_-_Form "UnregisterForAllControls - Form")()**

-   Unregisters all registered controls.

**[RegisterForMenu](https://ck.uesp.net/wiki/RegisterForMenu_-_Form "RegisterForMenu - Form")(String _menuName_)**

-   Registers for OnMenuOpen and OnMenuClose events for the given menu.

**[UnregisterForMenu](https://ck.uesp.net/wiki/UnregisterForMenu_-_Form "UnregisterForMenu - Form")(String _menuName_)**

-   Unregisters for OnMenuOpen and OnMenuClose events for the given menu.

**[UnregisterForAllMenus](https://ck.uesp.net/wiki/UnregisterForAllMenus_-_Form "UnregisterForAllMenus - Form")()**

-   Unregisters all registered menus.

**[RegisterForModEvent](https://ck.uesp.net/wiki/RegisterForModEvent_-_Form "RegisterForModEvent - Form")(String _eventName_, String _callbackName_)**

-   Registers a custom event callback for given event name.

**[SendModEvent](https://ck.uesp.net/wiki/SendModEvent "SendModEvent")(String _eventName_, String _strArg_, Float _numArg_)**

-   Sends a custom event with given generic parameters.

**[UnregisterForModEvent](https://ck.uesp.net/w/index.php?title=UnregisterForModEvent_-_Form&action=edit&redlink=1 "UnregisterForModEvent - Form (page does not exist)")(String _eventName_)**

-   Unregisters a custom event callback for given event name.

**[UnregisterForAllModEvents](https://ck.uesp.net/w/index.php?title=UnregisterForAllModEvents&action=edit&redlink=1 "UnregisterForAllModEvents (page does not exist)")()**

-   Unregisters all registered custom events.

**Form [TempClone](https://ck.uesp.net/wiki/TempClone_-_Form "TempClone - Form")()**

-   Returns a temporary clone of this form

**[RegisterForCameraState](https://ck.uesp.net/wiki/RegisterForCameraState_-_Form "RegisterForCameraState - Form")()**

-   Registers for OnPlayerCameraState events.

**[UnregisterForCameraState](https://ck.uesp.net/wiki/UnregisterForCameraState_-_Form "UnregisterForCameraState - Form")()**

-   Unregisters for OnPlayerCameraState events.

**[RegisterForCrosshairRef](https://ck.uesp.net/wiki/RegisterForCrosshairRef_-_Form "RegisterForCrosshairRef - Form")()**

-   Registers for OnCrosshairRefChange events.

**[UnregisterForCrosshairRef](https://ck.uesp.net/wiki/UnregisterForCrosshairRef_-_Form "UnregisterForCrosshairRef - Form")()**

-   Unregisters for OnCrosshairRefChange events.

**[RegisterForActorAction](https://ck.uesp.net/wiki/RegisterForActorAction_-_Form "RegisterForActorAction - Form")(Int _actionType_)**

-   Registers for OnActorAction events.

**[UnregisterForActorAction](https://ck.uesp.net/wiki/UnregisterForActorAction_-_Form "UnregisterForActorAction - Form")(Int _actionType_)**

-   Unregisters for OnActorAction events.

**[RegisterForNiNodeUpdate](https://ck.uesp.net/wiki/RegisterForNiNodeUpdate "RegisterForNiNodeUpdate")()**

-   Registers the script for when a QueueNiNodeUpdate is called

**[UnregisterForNiNodeUpdate](https://ck.uesp.net/wiki/UnregisterForNiNodeUpdate "UnregisterForNiNodeUpdate")()**

-   Unregisters the script for when a QueueNiNodeUpdate is called

## Events

**[OnAnimationEvent](https://ck.uesp.net/wiki/OnAnimationEvent_-_Form "OnAnimationEvent - Form")(ObjectReference _akSource_, String _asEventName_)**

-   Received when one of animation events we are listening for is recieved.

**[OnAnimationEventUnregistered](https://ck.uesp.net/wiki/OnAnimationEventUnregistered_-_Form "OnAnimationEventUnregistered - Form")(ObjectReference _akSource_, String _asEventName_)**

-   Received when one of the animation events we are listening for has been automatically unregistered by the game due to the target animation graph unloading.

**[OnGainLOS](https://ck.uesp.net/wiki/OnGainLOS_-_Form "OnGainLOS - Form")(Actor _akViewer_, ObjectReference _akTarget_)**

-   Received when the viewer goes from not seeing the target to seeing the target - if this form is registered.

**[OnLostLOS](https://ck.uesp.net/wiki/OnLostLOS_-_Form "OnLostLOS - Form")(Actor _akViewer_, ObjectReference _akTarget_)**

-   Received when the viewer goes from seeing the target to not seeing the target - if this form is registered.

**[OnSleepStart](https://ck.uesp.net/wiki/OnSleepStart_-_Form "OnSleepStart - Form")(Float _afSleepStartTime_, Float _afDesiredSleepEndTime_)**

-   Received when the player goes to sleep.

**[OnSleepStop](https://ck.uesp.net/wiki/OnSleepStop_-_Form "OnSleepStop - Form")(Bool _abInterrupted_)**

-   Received when the player wakes up or is interrupted in sleep.

**[OnTrackedStatsEvent](https://ck.uesp.net/wiki/OnTrackedStatsEvent_-_Form "OnTrackedStatsEvent - Form")(String _asStat_, Int _aiStatValue_)**

-   Received when tracked stats are updated.

**[OnUpdate](https://ck.uesp.net/wiki/OnUpdate_-_Form "OnUpdate - Form")()**

-   Received at periodic intervals, if the form is registered.

**[OnUpdateGameTime](https://ck.uesp.net/wiki/OnUpdateGameTime_-_Form "OnUpdateGameTime - Form")()**

-   Received at periodic intervals of game time, if the form is registered.

## SKSE Events

**[OnKeyDown](https://ck.uesp.net/wiki/OnKeyDown_-_Form "OnKeyDown - Form")(Int _keyCode_)**

-   Received when key(s) registered via [RegisterForKey](https://ck.uesp.net/wiki/RegisterForKey_-_Form "RegisterForKey - Form") are pressed.

**[OnKeyUp](https://ck.uesp.net/wiki/OnKeyUp_-_Form "OnKeyUp - Form")(Int _keyCode_, Float _holdTime_)**

-   Received when key(s) registered via [RegisterForKey](https://ck.uesp.net/wiki/RegisterForKey_-_Form "RegisterForKey - Form") are released.

**[OnControlDown](https://ck.uesp.net/wiki/OnControlDown_-_Form "OnControlDown - Form")(String _control_)**

-   Received when control(s) registered via [RegisterForControl](https://ck.uesp.net/wiki/RegisterForControl_-_Form "RegisterForControl - Form") are pressed.

**[OnControlUp](https://ck.uesp.net/wiki/OnControlUp_-_Form "OnControlUp - Form")(String _control_, Float _holdTime_)**

-   Received when control(s) registered via [RegisterForControl](https://ck.uesp.net/wiki/RegisterForControl_-_Form "RegisterForControl - Form") are released.

**[OnMenuOpen](https://ck.uesp.net/wiki/OnMenuOpen_-_Form "OnMenuOpen - Form")(String _menuName_)**

-   Received when menu(s) registered via [RegisterForMenu](https://ck.uesp.net/wiki/RegisterForMenu_-_Form "RegisterForMenu - Form") are opened.

**[OnMenuClose](https://ck.uesp.net/wiki/OnMenuClose_-_Form "OnMenuClose - Form")(String _menuName_)**

-   Received when menu(s) registered via [RegisterForMenu](https://ck.uesp.net/wiki/RegisterForMenu_-_Form "RegisterForMenu - Form") are closed.

**[OnPlayerCameraState](https://ck.uesp.net/wiki/OnPlayerCameraState_-_Form "OnPlayerCameraState - Form")(Int _oldState_, Int _newState_)**

-   Received when (player camera state changes?) when registered via [RegisterForCameraState](https://ck.uesp.net/wiki/RegisterForCameraState_-_Form "RegisterForCameraState - Form")

**[OnCrosshairRefChange](https://ck.uesp.net/wiki/OnCrosshairRefChange_-_Form "OnCrosshairRefChange - Form")(ObjectReference _ref_)**

-   Received when player crosshair changes when registered via [RegisterForCrosshairRef](https://ck.uesp.net/wiki/RegisterForCrosshairRef_-_Form "RegisterForCrosshairRef - Form") (Note: ref is none for no target)(Note:Crosshair uses activate pick)

**[OnActorAction](https://ck.uesp.net/wiki/OnActorAction_-_Form "OnActorAction - Form")(Int _actionType_, Actor _akActor_, Form _source_, Int _slot_)**

-   Received when the Actor performs an action that is registered via [RegisterForActorAction](https://ck.uesp.net/wiki/RegisterForActorAction_-_Form "RegisterForActorAction - Form")

**[OnNiNodeUpdate](https://ck.uesp.net/wiki/OnNiNodeUpdate "OnNiNodeUpdate")(ObjectReference _akActor_)**

-   Received when a NINodeUpdate is performed. To recieve this the form must have been registered via [RegisterForNiNodeUpdate](https://ck.uesp.net/wiki/RegisterForNiNodeUpdate_-_Form "RegisterForNiNodeUpdate - Form")