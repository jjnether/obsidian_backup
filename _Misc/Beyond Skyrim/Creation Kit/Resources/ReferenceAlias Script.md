  Script for the manipulation of reference aliases.

## Definition

```
ScriptName ReferenceAlias extends Alias
```

## Properties

None

## Global Functions

None

## Member Functions

**[AddInventoryEventFilter](https://ck.uesp.net/wiki/AddInventoryEventFilter_-_ObjectReference "AddInventoryEventFilter - ObjectReference")(Form _akFilter_)**

-   Adds an inventory event filter to this alias.

**[Clear](https://ck.uesp.net/wiki/Clear_-_ReferenceAlias "Clear - ReferenceAlias")()**

-   Clears this alias from pointing at anything.

**Bool [ForceRefIfEmpty](https://ck.uesp.net/wiki/ForceRefIfEmpty_-_ReferenceAlias "ForceRefIfEmpty - ReferenceAlias")(ObjectReference _akNewRef_)**

-   Tries to force a reference into the alias, but only if it's already empty.

**[ForceRefTo](https://ck.uesp.net/wiki/ForceRefTo_-_ReferenceAlias "ForceRefTo - ReferenceAlias")(ObjectReference _akNewRef_)**

-   Forces this alias to use the specified [ObjectReference](https://ck.uesp.net/wiki/ObjectReference_Script "ObjectReference Script")

**Actor [GetActorRef](https://ck.uesp.net/wiki/GetActorReference_-_ReferenceAlias "GetActorReference - ReferenceAlias")()**

-   Shorthand for GetActorReference().

**Actor [GetActorReference](https://ck.uesp.net/wiki/GetActorReference_-_ReferenceAlias "GetActorReference - ReferenceAlias")()**

-   Shorthand for GetReference() as [Actor](https://ck.uesp.net/wiki/Actor_Script "Actor Script").

**ObjectReference [GetRef](https://ck.uesp.net/wiki/GetReference_-_ReferenceAlias "GetReference - ReferenceAlias")()**

-   Shorthand for GetReference().

**ObjectReference [GetReference](https://ck.uesp.net/wiki/GetReference_-_ReferenceAlias "GetReference - ReferenceAlias")()** ^55fb9a

-   Attempts to retrieve the [ObjectReference](https://ck.uesp.net/wiki/ObjectReference_Script "ObjectReference Script") that this alias is pointing at

**[RemoveAllInventoryEventFilters](https://ck.uesp.net/wiki/RemoveAllInventoryEventFilters_-_ObjectReference "RemoveAllInventoryEventFilters - ObjectReference")()**

-   Remove all inventory event filters on this alias.

**[RemoveInventoryEventFilter](https://ck.uesp.net/wiki/RemoveInventoryEventFilter_-_ObjectReference "RemoveInventoryEventFilter - ObjectReference")(Form _akFilter_)**

-   Remove a specific inventory event filter.

**Bool [TryToAddToFaction](https://ck.uesp.net/wiki/TryToAddToFaction_-_ReferenceAlias "TryToAddToFaction - ReferenceAlias")(Faction _FactionToAddTo_)**

-   Attempts to add the reference this alias points to to a faction

**Bool [TryToClear](https://ck.uesp.net/wiki/TryToClear_-_ReferenceAlias "TryToClear - ReferenceAlias")()**

-   Attempts to clear this alias

**Bool [TryToDisable](https://ck.uesp.net/wiki/TryToDisable_-_ReferenceAlias "TryToDisable - ReferenceAlias")()**

-   Attempts to disable the reference this alias points at

**Bool [TryToDisableNoWait](https://ck.uesp.net/wiki/TryToDisableNoWait_-_ReferenceAlias "TryToDisableNoWait - ReferenceAlias")()**

-   Attempts to disable the reference this alias points at (the no-wait version)

**Bool [TryToEnable](https://ck.uesp.net/wiki/TryToEnable_-_ReferenceAlias "TryToEnable - ReferenceAlias")()**

-   Attempts to enable the reference this alias points at

**Bool [TryToEnableNoWait](https://ck.uesp.net/wiki/TryToEnableNoWait_-_ReferenceAlias "TryToEnableNoWait - ReferenceAlias")()**

-   Attempts to enable the reference this alias points at (no-wait version)

**Bool [TryToEvaluatePackage](https://ck.uesp.net/wiki/TryToEvaluatePackage_-_ReferenceAlias "TryToEvaluatePackage - ReferenceAlias")()**

-   Attempts to get the actor this alias points at to re-evaluate his package stack

**Bool [TryToKill](https://ck.uesp.net/wiki/TryToKill_-_ReferenceAlias "TryToKill - ReferenceAlias")()**

-   Attempts to kill the actor this alias points at

**Bool [TryToMoveTo](https://ck.uesp.net/wiki/TryToMoveTo_-_ReferenceAlias "TryToMoveTo - ReferenceAlias")(ObjectReference _RefToMoveTo_)**

-   Attempts to move the reference this alias points to to the target reference

**Bool [TryToRemoveFromFaction](https://ck.uesp.net/wiki/TryToRemoveFromFaction_-_ReferenceAlias "TryToRemoveFromFaction - ReferenceAlias")(Faction _FactionToRemoveFrom_)**

-   Attempts to remove the reference this alias points to from a faction

**Bool [TryToReset](https://ck.uesp.net/wiki/TryToReset_-_ReferenceAlias "TryToReset - ReferenceAlias")()**

-   Attempts to reset the reference this alias points at

**Bool [TryToStopCombat](https://ck.uesp.net/wiki/TryToStopCombat_-_ReferenceAlias "TryToStopCombat - ReferenceAlias")()**

-   Attempts to remove the actor this alias points at from combat

## Events

ReferenceAliases receive [events](https://ck.uesp.net/wiki/ObjectReference_Script#Events "ObjectReference Script") from the [ObjectReference](https://ck.uesp.net/wiki/ObjectReference_Script "ObjectReference Script") they are pointing at.

ReferenceAliases may also receive [additional events](https://ck.uesp.net/wiki/Actor_Script#Events "Actor Script") if they are pointing at an [Actor](https://ck.uesp.net/wiki/Actor_Script "Actor Script").

## Special Edition Exclusive Events

**[OnLycanthropyStateChanged](https://ck.uesp.net/w/index.php?title=OnLycanthropyStateChanged_-_ReferenceAlias&action=edit&redlink=1 "OnLycanthropyStateChanged - ReferenceAlias (page does not exist)")(Bool _abIsWerewolf_)**

-   Event received when the lycanthropy state of this actor changes

**[OnPlayerFastTravelEnd](https://ck.uesp.net/w/index.php?title=OnPlayerFastTravelEnd_-_ReferenceAlias&action=edit&redlink=1 "OnPlayerFastTravelEnd - ReferenceAlias (page does not exist)")(Float _afTravelGameTimeHours_)**

-   Event received when the player finishes fast travel.

**[OnVampirismStateChanged](https://ck.uesp.net/w/index.php?title=OnVampirismStateChanged_-_ReferenceAlias&action=edit&redlink=1 "OnVampirismStateChanged - ReferenceAlias (page does not exist)")(bool _abIsVampire_)**

-   Event received when the vampirism state of this actor changes

**[OnVampireFeed](https://ck.uesp.net/w/index.php?title=OnVampireFeed_-_ReferenceAlias&action=edit&redlink=1 "OnVampireFeed - ReferenceAlias (page does not exist)")(Actor _akTarget_)**

-   Event received when this actor feeds on another, as a vampire