Script for the manipulation of object instances.  
If you are adding a script to an object that is going to be a reference in the world (like a button for example) your script will need to extend this script.

## Definition

```
ScriptName ObjectReference extends Form
```

## Properties

-   float X \[read-only\]: The current X position of the reference.
-   float Y \[read-only\]: The current Y position of the reference.
-   float Z \[read-only\]: The current Z position of the reference.

These properties are meant to be used when calling [SetMotionType](https://ck.uesp.net/wiki/SetMotionType_-_ObjectReference "SetMotionType - ObjectReference"):

-   int Motion\_Dynamic \[read-only\]: 1
-   int Motion\_SphereInertia \[read-only\]: 2
-   int Motion\_BoxInertia \[read-only\]: 3
-   int Motion\_Keyframed \[read-only\]: 4
-   int Motion\_Fixed \[read-only\]: 5
-   int Motion\_ThinBoxInertia \[read-only\]: 6
-   int Motion\_Character \[read-only\]: 7

## Global Functions

None

## Member Functions

**[Activate](https://ck.uesp.net/wiki/Activate_-_ObjectReference "Activate - ObjectReference")(ObjectReference _akActivator_)**

-   Have the passed in reference activate this object.

**[AddInventoryEventFilter](https://ck.uesp.net/wiki/AddInventoryEventFilter_-_ObjectReference "AddInventoryEventFilter - ObjectReference")(Form _akFilter_)**

-   Adds an inventory event filter to this reference.

**[AddItem](https://ck.uesp.net/wiki/AddItem_-_ObjectReference "AddItem - ObjectReference")(Form _akItemToAdd_, Int _aiCount_, Bool _abSilent_)**

-   Adds the passed in item to this object's inventory.

**[AddKeyIfNeeded](https://ck.uesp.net/wiki/AddKeyIfNeeded_-_ObjectReference "AddKeyIfNeeded - ObjectReference")(ObjectReference _ObjectWithNeededKey_)**

-   Adds the key to ObjectWithNeededKey if this object's inventory does not contain it already.

**[AddToMap](https://ck.uesp.net/wiki/AddToMap_-_ObjectReference "AddToMap - ObjectReference")(Bool _abAllowFastTravel_)**

-   Adds this map marker to the map, optionally making it available for fast travel.

**[ApplyHavokImpulse](https://ck.uesp.net/wiki/ApplyHavokImpulse_-_ObjectReference "ApplyHavokImpulse - ObjectReference")(Float _afX_, Float _afY_, Float _afZ_, Float _afMagnitude_)**

-   Apply a Havok impulse force to this object.

**[BlockActivation](https://ck.uesp.net/wiki/BlockActivation_-_ObjectReference "BlockActivation - ObjectReference")(Bool _abBlocked_)**

-   Blocks normal activation processing for this reference.

**Int [CalculateEncounterLevel](https://ck.uesp.net/wiki/CalculateEncounterLevel_-_ObjectReference "CalculateEncounterLevel - ObjectReference")(Int _aiDifficulty_)**

-   Calculate this object's encounter level, using the specified difficulty.

**Bool [CanFastTravelToMarker](https://ck.uesp.net/wiki/CanFastTravelToMarker_-_ObjectReference "CanFastTravelToMarker - ObjectReference")()**

-   Can the player fast travel to this map marker?

**[ClearDestruction](https://ck.uesp.net/wiki/ClearDestruction_-_ObjectReference "ClearDestruction - ObjectReference")()**

-   Clears all effects of destruction from this object.

**Int [CountLinkedRefChain](https://ck.uesp.net/wiki/CountLinkedRefChain_-_ObjectReference "CountLinkedRefChain - ObjectReference")(Keyword _apKeyword_, Int _maxExpectedLinkedRefs_)**

-   Counts the number of linked refs that are in a linked Ref chain

**[CreateDetectionEvent](https://ck.uesp.net/wiki/CreateDetectionEvent_-_ObjectReference "CreateDetectionEvent - ObjectReference")(Actor _akOwner_, Int _aiSoundLevel_)**

-   Create a detection event at this reference, with the specified owner.

**[DamageObject](https://ck.uesp.net/wiki/DamageObject_-_ObjectReference "DamageObject - ObjectReference")(Float _afDamage_)**

-   Damages this object and advances the destruction stage.

**[Delete](https://ck.uesp.net/wiki/Delete_-_ObjectReference "Delete - ObjectReference")()**

-   Deletes this object.

**[DeleteWhenAble](https://ck.uesp.net/wiki/DeleteWhenAble_-_ObjectReference "DeleteWhenAble - ObjectReference")()**

-   Waits until this reference is out of the loaded area and then deletes it

**[Disable](https://ck.uesp.net/wiki/Disable_-_ObjectReference "Disable - ObjectReference")(Bool _abFadeOut_)**

-   Disables this object.

**[DisableLinkChain](https://ck.uesp.net/wiki/DisableLinkChain_-_ObjectReference "DisableLinkChain - ObjectReference")(Keyword _apKeyword_, Bool _abFadeOut_)**

-   Disables all of the references that are linked, in a chain, to this one.

**[DisableNoWait](https://ck.uesp.net/wiki/DisableNoWait_-_ObjectReference "DisableNoWait - ObjectReference")(Bool _abFadeOut_)**

-   Disables this object and does not wait for the object to be disable or faded out.

**[DropObject](https://ck.uesp.net/wiki/DropObject_-_ObjectReference "DropObject - ObjectReference")(Form _akObject_, Int _aiCount_)**

-   Drops the specified object from this object's inventory.

**[Enable](https://ck.uesp.net/wiki/Enable_-_ObjectReference "Enable - ObjectReference")(Bool _abFadeIn_)**

-   Enables this object.

**[EnableFastTravel](https://ck.uesp.net/wiki/EnableFastTravel_-_ObjectReference "EnableFastTravel - ObjectReference")(Bool _abEnable_)**

-   Enables or disables fast travel to this map marker.

**[EnableLinkChain](https://ck.uesp.net/wiki/EnableLinkChain_-_ObjectReference "EnableLinkChain - ObjectReference")(Keyword _apKeyword_)**

-   Enables all of the references that are linked, in a chain, to this one.

**[EnableNoWait](https://ck.uesp.net/wiki/EnableNoWait_-_ObjectReference "EnableNoWait - ObjectReference")(Bool _abFadeIn_)**

-   Enables this object and does not wait for the object to be enabled or faded in.

**[ForceAddRagdollToWorld](https://ck.uesp.net/wiki/ForceAddRagdollToWorld_-_ObjectReference "ForceAddRagdollToWorld - ObjectReference")()**

-   Forcibly adds the ragdoll of a reference to the world

**[ForceRemoveRagdollFromWorld](https://ck.uesp.net/wiki/ForceRemoveRagdollFromWorld_-_ObjectReference "ForceRemoveRagdollFromWorld - ObjectReference")()**

-   Forcibly removes the ragdoll of a reference from the world

**ActorBase [GetActorOwner](https://ck.uesp.net/wiki/GetActorOwner_-_ObjectReference "GetActorOwner - ObjectReference")()**

-   Obtains the actor base that owns this object.

**Float [GetAngleX](https://ck.uesp.net/wiki/GetAngleX_-_ObjectReference "GetAngleX - ObjectReference")()**

-   Obtains this object's rotation around the x axis.

**Float [GetAngleY](https://ck.uesp.net/wiki/GetAngleY_-_ObjectReference "GetAngleY - ObjectReference")()**

-   Obtains this object's rotation around the y axis.

**Float [GetAngleZ](https://ck.uesp.net/wiki/GetAngleZ_-_ObjectReference "GetAngleZ - ObjectReference")()**

-   Obtains this object's rotation around the z axis.

**Bool [GetAnimationVariableBool](https://ck.uesp.net/wiki/GetAnimationVariableBool_-_ObjectReference "GetAnimationVariableBool - ObjectReference")(String _asVariableName_)**

-   Fetches the value of a variable on the reference's animation graph (bool version).

**Float [GetAnimationVariableFloat](https://ck.uesp.net/wiki/GetAnimationVariableFloat_-_ObjectReference "GetAnimationVariableFloat - ObjectReference")(String _asVariableName_)**

-   Fetches the value of a variable on the reference's animation graph (float version).

**Int [GetAnimationVariableInt](https://ck.uesp.net/wiki/GetAnimationVariableInt_-_ObjectReference "GetAnimationVariableInt - ObjectReference")(String _asVariableName_)**

-   Fetches the value of a variable on the reference's animation graph (int version).

**Form [GetBaseObject](https://ck.uesp.net/wiki/GetBaseObject_-_ObjectReference "GetBaseObject - ObjectReference")()**

-   Obtains this reference's base object.

**Int [GetCurrentDestructionStage](https://ck.uesp.net/wiki/GetCurrentDestructionStage_-_ObjectReference "GetCurrentDestructionStage - ObjectReference")()**

-   Gets the object's current stage of destruction.

**Location [GetCurrentLocation](https://ck.uesp.net/wiki/GetCurrentLocation_-_ObjectReference "GetCurrentLocation - ObjectReference")()**

-   Obtains this reference's current location.

**Scene [GetCurrentScene](https://ck.uesp.net/wiki/GetCurrentScene_-_ObjectReference "GetCurrentScene - ObjectReference")()**

-   Obtains the scene that this reference is currently participating in, if any.

**Float [GetDistance](https://ck.uesp.net/wiki/GetDistance_-_ObjectReference "GetDistance - ObjectReference")(ObjectReference _akOther_)**

-   Calculates the distance between this object and the passed in one.

**Location [GetEditorLocation](https://ck.uesp.net/wiki/GetEditorLocation_-_ObjectReference "GetEditorLocation - ObjectReference")()**

-   Obtains this reference's editor location.

**Faction [GetFactionOwner](https://ck.uesp.net/wiki/GetFactionOwner_-_ObjectReference "GetFactionOwner - ObjectReference")()**

-   Gets the faction that owns this reference.

**Float [GetHeadingAngle](https://ck.uesp.net/wiki/GetHeadingAngle_-_ObjectReference "GetHeadingAngle - ObjectReference")(ObjectReference _akOther_)**

-   Gets the angle between this object's heading, and the direction the other object is in.

**Float [GetHeight](https://ck.uesp.net/wiki/GetHeight_-_ObjectReference "GetHeight - ObjectReference")()**

-   Gets the height of this object

**Int [GetItemCount](https://ck.uesp.net/wiki/GetItemCount_-_ObjectReference "GetItemCount - ObjectReference")(Form _akItem_)**

-   Returns how many of the specified item is in this object's inventory.

**Float [GetItemHealthPercent](https://ck.uesp.net/wiki/GetItemHealthPercent_-_ObjectReference "GetItemHealthPercent - ObjectReference")()**

-   Returns the item health percent of this object (1.0 == 100%).

**Key [GetKey](https://ck.uesp.net/wiki/GetKey_-_ObjectReference "GetKey - ObjectReference")()**

-   Obtains the key that unlocks this object (if any).

**Float [GetLength](https://ck.uesp.net/wiki/GetLength_-_ObjectReference "GetLength - ObjectReference")()**

-   Obtains the length of this object.

**ObjectReference [GetLinkedRef](https://ck.uesp.net/wiki/GetLinkedRef_-_ObjectReference "GetLinkedRef - ObjectReference")(Keyword _apKeyword_)**

-   Returns our linked reference for the given Keyword, if any.

**Int [GetLockLevel](https://ck.uesp.net/wiki/GetLockLevel_-_ObjectReference "GetLockLevel - ObjectReference")()**

-   Obtains the level of the lock on this object.

**Float [GetMass](https://ck.uesp.net/wiki/GetMass_-_ObjectReference "GetMass - ObjectReference")()**

-   Obtains this object's mass in Havok.

**ObjectReference [GetNthLinkedRef](https://ck.uesp.net/wiki/GetNthLinkedRef_-_ObjectReference "GetNthLinkedRef - ObjectReference")(Int _aiLinkedRef_)**

-   Obtains the nth linked ref from this object.

**Int [GetOpenState](https://ck.uesp.net/wiki/GetOpenState_-_ObjectReference "GetOpenState - ObjectReference")()**

-   Obtains this object's current "open state".

**Cell [GetParentCell](https://ck.uesp.net/wiki/GetParentCell_-_ObjectReference "GetParentCell - ObjectReference")()**

-   Obtains the cell this object is currently in.

**Float [GetPositionX](https://ck.uesp.net/wiki/GetPositionX_-_ObjectReference "GetPositionX - ObjectReference")()**

-   Returns this object's current X position.

**Float [GetPositionY](https://ck.uesp.net/wiki/GetPositionY_-_ObjectReference "GetPositionY - ObjectReference")()**

-   Returns this object's current Y position.

**Float [GetPositionZ](https://ck.uesp.net/wiki/GetPositionZ_-_ObjectReference "GetPositionZ - ObjectReference")()**

-   Returns this object's current Z position.

**Float [GetScale](https://ck.uesp.net/wiki/GetScale_-_ObjectReference "GetScale - ObjectReference")()**

-   Get this object's current scale.

**Int [GetTriggerObjectCount](https://ck.uesp.net/wiki/GetTriggerObjectCount_-_ObjectReference "GetTriggerObjectCount - ObjectReference")()**

-   Returns the number of objects inside this trigger volume.

**VoiceType [GetVoiceType](https://ck.uesp.net/wiki/GetVoiceType_-_ObjectReference "GetVoiceType - ObjectReference")()**

-   Obtains the [VoiceType](https://ck.uesp.net/wiki/VoiceType_Script "VoiceType Script") for this actor or talking activator.

**Float [GetWidth](https://ck.uesp.net/wiki/GetWidth_-_ObjectReference "GetWidth - ObjectReference")()**

-   Get the current width of the object.

**Worldspace [GetWorldSpace](https://ck.uesp.net/wiki/GetWorldSpace_-_ObjectReference "GetWorldSpace - ObjectReference")()**

-   Returns the worldspace this reference is in.

**Bool [HasEffectKeyword](https://ck.uesp.net/wiki/HasEffectKeyword_-_ObjectReference "HasEffectKeyword - ObjectReference")(Keyword _akKeyword_)**

-   Returns if this reference has an active effect coming from a magic effect with the specified keyword attached

**Bool [HasNode](https://ck.uesp.net/wiki/HasNode_-_ObjectReference "HasNode - ObjectReference")(String _asNodeName_)**

-   Returns if this reference has the specified name node in its 3D.

**Bool [HasRefType](https://ck.uesp.net/wiki/HasRefType_-_ObjectReference "HasRefType - ObjectReference")(LocationRefType _akRefType_)**

-   Returns if this reference has the specified [LocationRefType](https://ck.uesp.net/wiki/LocationRefType_Script "LocationRefType Script") attached.

**[IgnoreFriendlyHits](https://ck.uesp.net/wiki/IgnoreFriendlyHits_-_ObjectReference "IgnoreFriendlyHits - ObjectReference")(Bool _abIgnore_)**

-   Flags this reference as ignoring (or not ignoring) friendly hits

**[InterruptCast](https://ck.uesp.net/wiki/InterruptCast_-_ObjectReference "InterruptCast - ObjectReference")()**

-   Interrupts any spellcasting this object may be doing.

**Bool [IsActivateChild](https://ck.uesp.net/wiki/IsActivateChild_-_ObjectReference "IsActivateChild - ObjectReference")(ObjectReference _akChild_)**

-   Returns whether the passed in reference is an activate child of this reference.

**Bool [IsActivationBlocked](https://ck.uesp.net/wiki/IsActivationBlocked_-_ObjectReference "IsActivationBlocked - ObjectReference")()**

-   Returns whether normal activation processing is currently blocked on this reference or not.

**Bool [Is3DLoaded](https://ck.uesp.net/wiki/Is3DLoaded_-_ObjectReference "Is3DLoaded - ObjectReference")()**

-   Checks to see if this reference's 3D data is currently loaded or not.

**Bool [IsDeleted](https://ck.uesp.net/wiki/IsDeleted_-_ObjectReference "IsDeleted - ObjectReference")()**

-   Checks to see if this object is currently flagged for delete.

**Bool [IsDisabled](https://ck.uesp.net/wiki/IsDisabled_-_ObjectReference "IsDisabled - ObjectReference")()**

-   Is this object currently disabled?

**Bool [IsEnabled](https://ck.uesp.net/wiki/IsEnabled_-_ObjectReference "IsEnabled - ObjectReference")()**

-   Is this object currently enabled?

**Bool [IsFurnitureInUse](https://ck.uesp.net/wiki/IsFurnitureInUse_-_ObjectReference "IsFurnitureInUse - ObjectReference")(Bool _abIgnoreReserved_)**

-   Is any furniture marker on this object in use?

**Bool [IsFurnitureMarkerInUse](https://ck.uesp.net/wiki/IsFurnitureMarkerInUse_-_ObjectReference "IsFurnitureMarkerInUse - ObjectReference")(Int _aiMarker_, Bool _abIgnoreReserved_)**

-   Is the specified furniture marker on this object in use?

**Bool [IsIgnoringFriendlyHits](https://ck.uesp.net/wiki/IsIgnoringFriendlyHits_-_ObjectReference "IsIgnoringFriendlyHits - ObjectReference")()**

-   Is this object ignoring friendly hits?

**Bool [IsInDialogueWithPlayer](https://ck.uesp.net/wiki/IsInDialogueWithPlayer_-_ObjectReference "IsInDialogueWithPlayer - ObjectReference")()**

-   Is this actor or talking activator currently talking to the player?

**Bool [IsInInterior](https://ck.uesp.net/wiki/IsInInterior_-_ObjectReference "IsInInterior - ObjectReference")()**

-   Returns true if the object is in an interior cell.

**Bool [IsInLocation](https://ck.uesp.net/wiki/IsInLocation_-_ObjectReference "IsInLocation - ObjectReference")(Location _akLocation_)**

-   Returns true if the object is currently in that location or a child of that location.

**Bool [IsLocked](https://ck.uesp.net/wiki/IsLocked_-_ObjectReference "IsLocked - ObjectReference")()**

-   Is the lock on this object locked?

**Bool [IsMapMarkerVisible](https://ck.uesp.net/wiki/IsMapMarkerVisible_-_ObjectReference "IsMapMarkerVisible - ObjectReference")()**

-   Is this map marker visible to the player?

**Bool [IsNearPlayer](https://ck.uesp.net/wiki/IsNearPlayer_-_ObjectReference "IsNearPlayer - ObjectReference")()**

-   A quick-and-dirty function to tell if this object is safe to enable or disable

**[KnockAreaEffect](https://ck.uesp.net/wiki/KnockAreaEffect_-_ObjectReference "KnockAreaEffect - ObjectReference")(Float _afMagnitude_, Float _afRadius_)**

-   Executes a knock effect to an area

**[Lock](https://ck.uesp.net/wiki/Lock_-_ObjectReference "Lock - ObjectReference")(Bool _abLock_, Bool _abAsOwner_)**

-   Locks or unlocks this object.

**[MoveTo](https://ck.uesp.net/wiki/MoveTo_-_ObjectReference "MoveTo - ObjectReference")(ObjectReference _akTarget_, Float _afXOffset_, Float _afYOffset_, Float _afZOffset_, Bool _abMatchRotation_)**

-   Moves this object to the same location as the passed-in reference, offset by the specified amount.

**Bool [MoveToIfUnloaded](https://ck.uesp.net/wiki/MoveToIfUnloaded_-_ObjectReference "MoveToIfUnloaded - ObjectReference")(ObjectReference _akTarget_, Float _afXOffset_, Float _afYOffset_, Float _afZOffset_)**

-   Moves this object to the same location as the passed-in reference, offset by the specified amount, IF this object is not currently loaded.

**[MoveToInteractionLocation](https://ck.uesp.net/wiki/MoveToInteractionLocation_-_ObjectReference "MoveToInteractionLocation - ObjectReference")(ObjectReference _akTarget_)**

-   Moves this object to the specified object's interaction location.

**[MoveToMyEditorLocation](https://ck.uesp.net/wiki/MoveToMyEditorLocation_-_ObjectReference "MoveToMyEditorLocation - ObjectReference")()**

-   Moves this object to its own editor location.

**[MoveToNode](https://ck.uesp.net/wiki/MoveToNode_-_ObjectReference "MoveToNode - ObjectReference")(ObjectReference _akTarget_, String _asNodeName_)**

-   Moves this object to the position (and rotation) of the specified node on the specified object's 3D

**Actor [PlaceActorAtMe](https://ck.uesp.net/wiki/PlaceActorAtMe_-_ObjectReference "PlaceActorAtMe - ObjectReference")(ActorBase _akActorToPlace_, Int _aiLevelMod_, EncounterZone _akZone_)**

-   Create an actor at this object's location.

**ObjectReference [PlaceAtMe](https://ck.uesp.net/wiki/PlaceAtMe_-_ObjectReference "PlaceAtMe - ObjectReference")(Form _akFormToPlace_, Int _aiCount_)**

-   Places x copies of the passed in form at this object's current position, returning the last one created.

**Bool [PlayAnimation](https://ck.uesp.net/wiki/PlayAnimation_-_ObjectReference "PlayAnimation - ObjectReference")(String _asAnimation_)**

-   Plays the specified animation on this object, returning immediately.

**Bool [PlayAnimationAndWait](https://ck.uesp.net/wiki/PlayAnimationAndWait_-_ObjectReference "PlayAnimationAndWait - ObjectReference")(String _asAnimation_, String _asEventName_)**

-   Plays the specified animation on this object and waits for the specified event before returning. (latent)

**Bool [PlayGamebryoAnimation](https://ck.uesp.net/wiki/PlayGamebryoAnimation_-_ObjectReference "PlayGamebryoAnimation - ObjectReference")(String _asAnimation_, Bool _abStartOver_, Float _afEaseInTime_)**

-   Plays a legacy nif file based animation

**Bool [PlayImpactEffect](https://ck.uesp.net/wiki/PlayImpactEffect_-_ObjectReference "PlayImpactEffect - ObjectReference")(ImpactDataSet _akImpactEffect_, String _asNodeName_, Float _afPickDirX_, Float _afPickDirY_, Float _afPickDirZ_, Float _afPickLength_, Bool _abApplyNodeRotation_, Bool _abUseNodeLocalRotation_)**

-   Plays an impact effect.

**Bool [PlaySyncedAnimationAndWaitSS](https://ck.uesp.net/wiki/PlaySyncedAnimationAndWaitSS_-_ObjectReference "PlaySyncedAnimationAndWaitSS - ObjectReference")(String _asAnimation1_, String _asEvent1_, ObjectReference _akObj2_, String _asAnimation2_, String _asEvent2_)**

-   Plays two animations simultaneously, waiting for events from both.

**Bool [PlaySyncedAnimationSS](https://ck.uesp.net/wiki/PlaySyncedAnimationSS_-_ObjectReference "PlaySyncedAnimationSS - ObjectReference")(String _asAnimation1_, ObjectReference _akObj2_, String _asAnimation2_)**

-   Plays two animations simultaneously.

**[PlayTerrainEffect](https://ck.uesp.net/wiki/PlayTerrainEffect_-_ObjectReference "PlayTerrainEffect - ObjectReference")(String _asEffectModelName_, String _asAttachBoneName_)**

-   Plays a terrain effect.

**[ProcessTrapHit](https://ck.uesp.net/wiki/ProcessTrapHit_-_ObjectReference "ProcessTrapHit - ObjectReference")(ObjectReference _akTrap_, Float _afDamage_, Float _afPushback_, Float _afXVel_, Float _afYVel_, Float _afZVel_, Float _afXPos_, Float _afYPos_, Float _afZPos_, Int _aeMaterial_, Float _afStagger_)**

-   Tells this object to handle the specified trap object hitting it.

**[PushActorAway](https://ck.uesp.net/wiki/PushActorAway_-_ObjectReference "PushActorAway - ObjectReference")(Actor _akActorToPush_, Int _aiKnockbackDamage_)**

-   Pushes the other actor away from this object as if hit by the specified amount of knockback damage.

**Bool [RampRumble](https://ck.uesp.net/wiki/RampRumble_-_ObjectReference "RampRumble - ObjectReference")(Float _power_, Float _duration_, Float _falloff_)**

-   Shakes cam/controller based on distance from player

**[RemoveAllInventoryEventFilters](https://ck.uesp.net/wiki/RemoveAllInventoryEventFilters_-_ObjectReference "RemoveAllInventoryEventFilters - ObjectReference")()**

-   Remove all inventory event filters on this reference.

**[RemoveAllItems](https://ck.uesp.net/wiki/RemoveAllItems_-_ObjectReference "RemoveAllItems - ObjectReference")(ObjectReference _akTransferTo_, Bool _abKeepOwnership_, Bool _abSilent_)**

-   Removes all items from this container, optionall transferring them to another one.

**[RemoveInventoryEventFilter](https://ck.uesp.net/wiki/RemoveInventoryEventFilter_-_ObjectReference "RemoveInventoryEventFilter - ObjectReference")(Form _akFilter_)**

-   Remove a specific inventory event filter.

**[RemoveItem](https://ck.uesp.net/wiki/RemoveItem_-_ObjectReference "RemoveItem - ObjectReference")(Form _akItemToRemove_, Int _aiCount_, Bool _abSilent_, ObjectReference _akOtherContainer_)**

-   Removes the passed in item from this object's inventory.

**[Reset](https://ck.uesp.net/wiki/Reset_-_ObjectReference "Reset - ObjectReference")(ObjectReference _akTarget_)**

-   Resets this object reference, optionally placing the object at the new target.

**[Say](https://ck.uesp.net/wiki/Say_-_ObjectReference "Say - ObjectReference")(Topic _akTopicToSay_, Actor _akActorToSpeakAs_, Bool _abSpeakInPlayersHead_)**

-   Causes this reference to speak a topic as if it were the specified actor.

**[SendStealAlarm](https://ck.uesp.net/wiki/SendStealAlarm_-_ObjectReference "SendStealAlarm - ObjectReference")(Actor _akThief_)**

-   Sends a steal alarm as if this reference had just been stolen by the actor.

**[SetActorCause](https://ck.uesp.net/wiki/SetActorCause_-_ObjectReference "SetActorCause - ObjectReference")(Actor _akActor_)**

-   Sets this actor as this object's actor cause.

**[SetActorOwner](https://ck.uesp.net/wiki/SetActorOwner_-_ObjectReference "SetActorOwner - ObjectReference")(ActorBase _akActorBase_)**

-   Sets this actor base as this object's owner.

**[SetAngle](https://ck.uesp.net/wiki/SetAngle_-_ObjectReference "SetAngle - ObjectReference")(Float _afXAngle_, Float _afYAngle_, Float _afZAngle_)**

-   Sets this object's rotation. Angles are in degrees.

**[SetAnimationVariableBool](https://ck.uesp.net/wiki/SetAnimationVariableBool_-_ObjectReference "SetAnimationVariableBool - ObjectReference")(String _asVariableName_, Bool _abNewValue_)**

-   Sets the value of a variable on the reference's animation graph (bool version).

**[SetAnimationVariableFloat](https://ck.uesp.net/wiki/SetAnimationVariableFloat_-_ObjectReference "SetAnimationVariableFloat - ObjectReference")(String _asVariableName_, Float _afNewValue_)**

-   Sets the value of a variable on the reference's animation graph (float version).

**[SetAnimationVariableInt](https://ck.uesp.net/wiki/SetAnimationVariableInt_-_ObjectReference "SetAnimationVariableInt - ObjectReference")(String _asVariableName_, Int _aiNewValue_)**

-   Sets the value of a variable on the reference's animation graph (int version).

**[SetDestroyed](https://ck.uesp.net/wiki/SetDestroyed_-_ObjectReference "SetDestroyed - ObjectReference")(Bool _abDestroyed_)**

-   Sets or clears this object's destroyed flag.

**[SetFactionOwner](https://ck.uesp.net/wiki/SetFactionOwner_-_ObjectReference "SetFactionOwner - ObjectReference")(Faction _akFaction_)**

-   Sets this faction as this object's owner.

**[SetLockLevel](https://ck.uesp.net/wiki/SetLockLevel_-_ObjectReference "SetLockLevel - ObjectReference")(Int _aiLockLevel_)**

-   Sets the lock level on this object.

**[SetMotionType](https://ck.uesp.net/wiki/SetMotionType_-_ObjectReference "SetMotionType - ObjectReference")(Int _aiMotionType_, Bool _abAllowActivate_)**

-   Sets the havok motion type on this object.

**[SetNoFavorAllowed](https://ck.uesp.net/wiki/SetNoFavorAllowed_-_ObjectReference "SetNoFavorAllowed - ObjectReference")(Bool _abNoFavor_)**

-   Sets or clears this object's ability to be not used by a teammate for a favor

**[SetOpen](https://ck.uesp.net/wiki/SetOpen_-_ObjectReference "SetOpen - ObjectReference")(Bool _abOpen_)**

-   Opens or closes this object.

**[SetPosition](https://ck.uesp.net/wiki/SetPosition_-_ObjectReference "SetPosition - ObjectReference")(Float _afX_, Float _afY_, Float _afZ_)**

-   Sets this object's position.

**[SetScale](https://ck.uesp.net/wiki/SetScale_-_ObjectReference "SetScale - ObjectReference")(Float _afScale_)**

-   Set the current scale of the object

**[SplineTranslateTo](https://ck.uesp.net/wiki/SplineTranslateTo_-_ObjectReference "SplineTranslateTo - ObjectReference")(Float _afX_, Float _afY_, Float _afZ_, Float _afAngleX_, Float _afAngleY_, Float _afAngleZ_, Float _afSplineCurve_, Float _afSpeed_)**

-   Makes the object translate to the given pos/orient on a spline.

**[SplineTranslateToRef](https://ck.uesp.net/wiki/SplineTranslateToRef_-_ObjectReference "SplineTranslateToRef - ObjectReference")(ObjectReference _arTarget_, Float _afTangentMagnitude_, Float _afSpeed_, Float _afMaxRotationSpeed_)**

-   Makes the reference translate to the target ref position/orient on a spline at the given speed

**[SplineTranslateToRefNode](https://ck.uesp.net/wiki/SplineTranslateToRefNode_-_ObjectReference "SplineTranslateToRefNode - ObjectReference")(ObjectReference _arTarget_, String _arNodeName_, Float _afTangentMagnitude_, Float _afSpeed_, Float _afMaxRotationSpeed_)**

-   Makes the reference translate to the target node's position/orient on a spline at the given speed

**[StopTranslation](https://ck.uesp.net/wiki/StopTranslation_-_ObjectReference "StopTranslation - ObjectReference")()**

-   Stops any translation on the object.

**[TetherToHorse](https://ck.uesp.net/wiki/TetherToHorse_-_ObjectReference "TetherToHorse - ObjectReference")(ObjectReference _akHorse_)**

-   Tether a prisoner cart to the given horse.

**[TranslateTo](https://ck.uesp.net/wiki/TranslateTo_-_ObjectReference "TranslateTo - ObjectReference")(Float _afX_, Float _afY_, Float _afZ_, Float _afAngleX_, Float _afAngleY_, Float _afAngleZ_, Float _afSpeed_, Float _afMaxRotationSpeed_)**

-   Makes the object translate to the given pos/orient.

**[TranslateToRef](https://ck.uesp.net/wiki/TranslateToRef_-_ObjectReference "TranslateToRef - ObjectReference")(ObjectReference _arTarget_, Float _afSpeed_, Float _afMaxRotationSpeed_)**

-   Makes the reference translate to the target ref position/orient at the given speed

**Bool [WaitForAnimationEvent](https://ck.uesp.net/wiki/WaitForAnimationEvent_-_ObjectReference "WaitForAnimationEvent - ObjectReference")(String _asEventName_)**

-   Waits for the animation graph to send the specified event.

## SKSE Member Functions

**Form\[\] [GetContainerForms](https://ck.uesp.net/wiki/GetContainerForms_-_ObjectReference "GetContainerForms - ObjectReference")()**

-   (Container only) Returns an array of the forms in a container. (Actor ObjectReferences are containers)

**Int [GetNumItems](https://ck.uesp.net/wiki/GetNumItems_-_ObjectReference "GetNumItems - ObjectReference")()**

-   (Container only) Returns the number of forms in the container. (Actor ObjectReferences are containers)

**Form [GetNthForm](https://ck.uesp.net/wiki/GetNthForm_-_ObjectReference "GetNthForm - ObjectReference")(Int _index_)**

-   (Container only) Returns the specified form from the container. (Actor ObjectReferences are containers)

**Float [GetTotalItemWeight](https://ck.uesp.net/wiki/GetTotalItemWeight_-_ObjectReference "GetTotalItemWeight - ObjectReference")()**

-   (Container only - perhaps Player only) Returns the total weight of all items held in the container.

**Float [GetTotalArmorWeight](https://ck.uesp.net/wiki/GetTotalArmorWeight_-_ObjectReference "GetTotalArmorWeight - ObjectReference")()**

-   (Container only - perhaps Player only) Returns the total weight of the armor in the container.

**Bool [IsHarvested](https://ck.uesp.net/wiki/IsHarvested_-_ObjectReference "IsHarvested - ObjectReference")()**

-   (Flora and Tree only) Returns whether the flora has been harvested or not.

**[SetHarvested](https://ck.uesp.net/w/index.php?title=SetHarvested_-_ObjectReference&action=edit&redlink=1 "SetHarvested - ObjectReference (page does not exist)")(Bool _harvested_)**

-   Sets whether the Reference has been harvested.

**[SetItemHealthPercent](https://ck.uesp.net/wiki/SetItemHealthPercent_-_ObjectReference "SetItemHealthPercent - ObjectReference")(Float _health_)**

-   Set the item's tempering. 1.0 is no tempering, 1.6 appears to be legendary. Values below 1.0 do nothing.

**[SetItemMaxCharge](https://ck.uesp.net/w/index.php?title=SetItemMaxCharge_-_ObjectReference&action=edit&redlink=1 "SetItemMaxCharge - ObjectReference (page does not exist)")(Float _maxCharge_)**

-   Sets the maximum charge of the item.(Only works on player enchants)

**Float [GetItemMaxCharge](https://ck.uesp.net/wiki/GetItemMaxCharge_-_ObjectReference "GetItemMaxCharge - ObjectReference")()**

-   Gets the maximum charge of the item.

**Float [GetItemCharge](https://ck.uesp.net/wiki/GetItemCharge_-_ObjectReference "GetItemCharge - ObjectReference")()**

-   Gets the current charge of the item.

**[SetItemCharge](https://ck.uesp.net/wiki/SetItemCharge_-_ObjectReference "SetItemCharge - ObjectReference")(Float _charge_)**

-   Sets the item's charge to the specified amount.

**[ResetInventory](https://ck.uesp.net/w/index.php?title=ResetInventory_-_ObjectReference&action=edit&redlink=1 "ResetInventory - ObjectReference (page does not exist)")()**

-   Resets the References inventory.

**Bool [IsOffLimits](https://ck.uesp.net/wiki/IsOffLimits_-_ObjectReference "IsOffLimits - ObjectReference")()**

**String [GetDisplayName](https://ck.uesp.net/w/index.php?title=GetDisplayName_-_ObjectReference&action=edit&redlink=1 "GetDisplayName - ObjectReference (page does not exist)")()**

-   Returns the name of the reference (This is the name that is displayed)

**Bool [SetDisplayName](https://ck.uesp.net/wiki/SetDisplayName_-_ObjectReference "SetDisplayName - ObjectReference")(String _name_, Bool _force_)**

-   Sets the reference's display name.

**ObjectReference [GetEnableParent](https://ck.uesp.net/w/index.php?title=GetEnableParent_-_ObjectReference&action=edit&redlink=1 "GetEnableParent - ObjectReference (page does not exist)")()**

-   Returns the enable parent of the object.

**Enchantment [GetEnchantment](https://ck.uesp.net/wiki/GetEnchantment-_ObjectReference "GetEnchantment- ObjectReference")()**

-   Returns the player-made enchantment of the object (if there is one)

**[SetEnchantment](https://ck.uesp.net/w/index.php?title=SetEnchantment_-_ObjectReference&action=edit&redlink=1 "SetEnchantment - ObjectReference (page does not exist)")(Enchantment _source_, Float _maxCharge_)**

-   Changes an item's player-made enchantment to another.

**[CreateEnchantment](https://ck.uesp.net/w/index.php?title=CreateEnchantment_-_ObjectReference&action=edit&redlink=1 "CreateEnchantment - ObjectReference (page does not exist)")(Float _maxCharge_, MagicEffect\[\] _effects_, Float\[\] _magnitudes_, Int\[\] _areas_, Int\[\] _durations_)**

-   Creates a new Enchantment on the item with the specified parameters.

**Int [GetNumReferenceAliases](https://ck.uesp.net/w/index.php?title=GetNumReferenceAliases_-_ObjectReference&action=edit&redlink=1 "GetNumReferenceAliases - ObjectReference (page does not exist)")()**

-   Returns the number of reference aliases holding this reference.

**ReferenceAlias [GetNthReferenceAlias](https://ck.uesp.net/w/index.php?title=GetNthReferenceAlias_-_ObjectReference&action=edit&redlink=1 "GetNthReferenceAlias - ObjectReference (page does not exist)")(Int _n_)**

-   Returns the nth Reference alias holding this reference.

## Events

**[OnActivate](https://ck.uesp.net/wiki/OnActivate_-_ObjectReference "OnActivate - ObjectReference")(ObjectReference _akActionRef_)** ^e1a952

-   Event received when this object is activated.

**[OnAttachedToCell](https://ck.uesp.net/wiki/OnAttachedToCell_-_ObjectReference "OnAttachedToCell - ObjectReference")()**

-   Event received when this reference moves from a detached cell to an attached one.

**[OnCellAttach](https://ck.uesp.net/wiki/OnCellAttach_-_ObjectReference "OnCellAttach - ObjectReference")()**

-   Event received when this reference's parent cell attaches.

**[OnCellDetach](https://ck.uesp.net/wiki/OnCellDetach_-_ObjectReference "OnCellDetach - ObjectReference")()**

-   Event received when this reference's parent cell detaches.

**[OnCellLoad](https://ck.uesp.net/wiki/OnCellLoad_-_ObjectReference "OnCellLoad - ObjectReference")()**

-   Event received when everything in the cell that holds this reference has loaded.

**[OnClose](https://ck.uesp.net/wiki/OnClose_-_ObjectReference "OnClose - ObjectReference")(ObjectReference _akActionRef_)**

-   Event received when this object is finished closing.

**[OnContainerChanged](https://ck.uesp.net/wiki/OnContainerChanged_-_ObjectReference "OnContainerChanged - ObjectReference")(ObjectReference _akNewContainer_, ObjectReference _akOldContainer_)**

-   Event received when an object moves into/out of/between containers.

**[OnDestructionStageChanged](https://ck.uesp.net/wiki/OnDestructionStageChanged_-_ObjectReference "OnDestructionStageChanged - ObjectReference")(Int _aiOldStage_, Int _aiCurrentStage_)**

-   Event received when this object's destruction stage has worsened.

**[OnDetachedFromCell](https://ck.uesp.net/wiki/OnDetachedFromCell_-_ObjectReference "OnDetachedFromCell - ObjectReference")()**

-   Event received when this object moves from an attached cell to a detached cell.

**[OnEquipped](https://ck.uesp.net/wiki/OnEquipped_-_ObjectReference "OnEquipped - ObjectReference")(Actor _akActor_)**

-   Event received when this object is equipped by an actor.

**[OnGrab](https://ck.uesp.net/wiki/OnGrab_-_ObjectReference "OnGrab - ObjectReference")()**

-   Event received when this object is grabbed (z-keyed) by the player.

**[OnHit](https://ck.uesp.net/wiki/OnHit_-_ObjectReference "OnHit - ObjectReference")(ObjectReference _akAggressor_, Form _akSource_, Projectile _akProjectile_, Bool _abPowerAttack_, Bool _abSneakAttack_, Bool _abBashAttack_, Bool _abHitBlocked_)**

-   Event received when this object is hit with a weapon or projectile.

**[OnItemAdded](https://ck.uesp.net/wiki/OnItemAdded_-_ObjectReference "OnItemAdded - ObjectReference")(Form _akBaseItem_, Int _aiItemCount_, ObjectReference _akItemReference_, ObjectReference _akSourceContainer_)**

-   Event received when an item is inserted into this object's container.

**[OnItemRemoved](https://ck.uesp.net/wiki/OnItemRemoved_-_ObjectReference "OnItemRemoved - ObjectReference")(Form _akBaseItem_, Int _aiItemCount_, ObjectReference _akItemReference_, ObjectReference _akDestContainer_)**

-   Event received when an item is removed from this object's container.

**[OnLoad](https://ck.uesp.net/wiki/OnLoad_-_ObjectReference "OnLoad - ObjectReference")()**

-   Event received when this object's 3d is loaded and ready.

**[OnLockStateChanged](https://ck.uesp.net/wiki/OnLockStateChanged_-_ObjectReference "OnLockStateChanged - ObjectReference")()**

-   Event received when the lock on this object changes its state.

**[OnMagicEffectApply](https://ck.uesp.net/wiki/OnMagicEffectApply_-_ObjectReference "OnMagicEffectApply - ObjectReference")(ObjectReference _akCaster_, MagicEffect _akEffect_)**

-   Event received when a magic effect is attempting to be applied to this reference.

**[OnOpen](https://ck.uesp.net/wiki/OnOpen_-_ObjectReference "OnOpen - ObjectReference")(ObjectReference _akActionRef_)**

-   Event received when this object is fully opened.

**[OnRead](https://ck.uesp.net/wiki/OnRead_-_ObjectReference "OnRead - ObjectReference")()**

-   Event received when this object is read. (Only applies to books)

**[OnRelease](https://ck.uesp.net/wiki/OnRelease_-_ObjectReference "OnRelease - ObjectReference")()**

-   Event received when this object is released by the player (stopped z-keying).

**[OnReset](https://ck.uesp.net/wiki/OnReset_-_ObjectReference "OnReset - ObjectReference")()**

-   Event received when this object is reset.

**[OnSell](https://ck.uesp.net/wiki/OnSell_-_ObjectReference "OnSell - ObjectReference")(Actor _akSeller_)**

-   Event received when this object is sold by someone.

**[OnSpellCast](https://ck.uesp.net/wiki/OnSpellCast_-_ObjectReference "OnSpellCast - ObjectReference")(Form _akSpell_)**

-   Event received when this object casts a spell.

**[OnTrapHit](https://ck.uesp.net/wiki/OnTrapHit_-_ObjectReference "OnTrapHit - ObjectReference")(ObjectReference _akTarget_, Float _afXVel_, Float _afYVel_, Float _afZVel_, Float _afXPos_, Float _afYPos_, Float _afZPos_, Int _aeMaterial_, Bool _abInitialHit_, Int _aeMotionType_)**

-   Event received when this trap object hits a target.

**[OnTrapHitStart](https://ck.uesp.net/wiki/OnTrapHitStart_-_ObjectReference "OnTrapHitStart - ObjectReference")(ObjectReference _akTarget_, Float _afXVel_, Float _afYVel_, Float _afZVel_, Float _afXPos_, Float _afYPos_, Float _afZPos_, Int _aeMaterial_, Bool _abInitialHit_, Int _aeMotionType_)**

-   Event received when this trap object starts colliding with a target.

**[OnTrapHitStop](https://ck.uesp.net/wiki/OnTrapHitStop_-_ObjectReference "OnTrapHitStop - ObjectReference")(ObjectReference _akTarget_)**

-   Event received when this trap object stops colliding with a target.

**[OnTranslationAlmostComplete](https://ck.uesp.net/wiki/OnTranslationAlmostComplete_-_ObjectReference "OnTranslationAlmostComplete - ObjectReference")()**

-   Event received when a translation request is almost complete.

**[OnTranslationComplete](https://ck.uesp.net/wiki/OnTranslationComplete_-_ObjectReference "OnTranslationComplete - ObjectReference")()**

-   Event received when a translation request is complete.

**[OnTranslationFailed](https://ck.uesp.net/wiki/OnTranslationFailed_-_ObjectReference "OnTranslationFailed - ObjectReference")()**

-   Event received when a translation request has failed.

**[OnTrigger](https://ck.uesp.net/wiki/OnTrigger_-_ObjectReference "OnTrigger - ObjectReference")(ObjectReference _akActionRef_)**

-   Event received when this object is triggered.

**[OnTriggerEnter](https://ck.uesp.net/wiki/OnTriggerEnter_-_ObjectReference "OnTriggerEnter - ObjectReference")(ObjectReference _akActionRef_)**

-   Event received when this object's volume is entered.

**[OnTriggerLeave](https://ck.uesp.net/wiki/OnTriggerLeave_-_ObjectReference "OnTriggerLeave - ObjectReference")(ObjectReference _akActionRef_)**

-   Event received when this object's volume is left.

**[OnUnequipped](https://ck.uesp.net/wiki/OnUnequipped_-_ObjectReference "OnUnequipped - ObjectReference")(Actor _akActor_)**

-   Event received when this object is unequipped by an actor.

**[OnUnload](https://ck.uesp.net/wiki/OnUnload_-_ObjectReference "OnUnload - ObjectReference")()**

-   Event received when this object's 3d has been unloaded.

**[OnWardHit](https://ck.uesp.net/wiki/OnWardHit_-_ObjectReference "OnWardHit - ObjectReference")(ObjectReference _akCaster_, Spell _akSpell_, Int _aiStatus_)**

-   Event called when the object reference is using a ward that is hit by a spell.