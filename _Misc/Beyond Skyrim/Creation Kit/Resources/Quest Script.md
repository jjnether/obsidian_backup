Script for the manipulation of quests.
## Definition

```
ScriptName Quest extends Form
```

## Member Functions

**[CompleteAllObjectives](https://ck.uesp.net/wiki/CompleteAllObjectives_-_Quest "CompleteAllObjectives - Quest")()**

-   Completes all a quests objectives.

**[CompleteQuest](https://ck.uesp.net/wiki/CompleteQuest_-_Quest "CompleteQuest - Quest")()**

-   Flags this quest as completed.

**[FailAllObjectives](https://ck.uesp.net/wiki/FailAllObjectives_-_Quest "FailAllObjectives - Quest")()**

-   Flags all quest objects as failed.

**Alias [GetAlias](https://ck.uesp.net/wiki/GetAlias_-_Quest "GetAlias - Quest")(Int _aiAliasID_)**

-   Obtains the [Alias](https://ck.uesp.net/wiki/Alias_Script "Alias Script") attached to this quest associated with the specified ID.

**Int [GetCurrentStageID](https://ck.uesp.net/wiki/GetCurrentStageID_-_Quest "GetCurrentStageID - Quest")()**

-   Obtains the highest completed stage on this quest.

**Int [GetStage](https://ck.uesp.net/wiki/GetStage_-_Quest "GetStage - Quest")()**

-   Alias for GetCurrentStageID().

**Bool [GetStageDone](https://ck.uesp.net/wiki/GetStageDone_-_Quest "GetStageDone - Quest")(Int _aiStage_)**

-   Alias for IsStageDone().

**Bool [IsActive](https://ck.uesp.net/wiki/IsActive_-_Quest "IsActive - Quest")()**

-   Is this quest "active"? (Tracked by the player).

**Bool [IsCompleted](https://ck.uesp.net/wiki/IsCompleted_-_Quest "IsCompleted - Quest")()**

-   Returns whether this quest is completed or not.

**Bool [IsObjectiveCompleted](https://ck.uesp.net/wiki/IsObjectiveCompleted_-_Quest "IsObjectiveCompleted - Quest")(Int _aiObjective_)**

-   Obtains whether the specified objective is completed or not.

**Bool [IsObjectiveDisplayed](https://ck.uesp.net/wiki/IsObjectiveDisplayed_-_Quest "IsObjectiveDisplayed - Quest")(Int _aiObjective_)**

-   Obtains whether the specified objective is displayed or not.

**Bool [IsObjectiveFailed](https://ck.uesp.net/wiki/IsObjectiveFailed_-_Quest "IsObjectiveFailed - Quest")(Int _aiObjective_)**

-   Obtains whether the specified objective is failed or not.

**Bool [IsRunning](https://ck.uesp.net/wiki/IsRunning_-_Quest "IsRunning - Quest")()**

-   Returns whether this quest is currently running or not.

**Bool [IsStageDone](https://ck.uesp.net/wiki/IsStageDone_-_Quest "IsStageDone - Quest")(Int _aiStage_)**

-   Checks to see if the specified stage is done or not.

**Bool [IsStarting](https://ck.uesp.net/wiki/IsStarting_-_Quest "IsStarting - Quest")()**

-   Returns whether this quest is currently enabled but not running yet.

**Bool [IsStopping](https://ck.uesp.net/wiki/IsStopping-_Quest "IsStopping- Quest")()**

-   Returns whether this quest is currently not enabled anymore but still shutting down.

**Bool [IsStopped](https://ck.uesp.net/wiki/IsStopped-_Quest "IsStopped- Quest")()**

-   Returns whether this quest is currently fully stopped.

**Bool [ModObjectiveGlobal](https://ck.uesp.net/wiki/ModObjectiveGlobal_-_Quest "ModObjectiveGlobal - Quest")(Float _afModValue_, GlobalVariable _aModGlobal_, Int _aiObjectiveID_, Float _afTargetValue_, Bool _abCountingUp_, Bool _abCompleteObjective_, Bool _abRedisplayObjective_)**

-   Mods a global variable in a threadsafe way. Optional parameters allow automatic redisplay and completion (or failure) of a quest objective using this global variable.

**[Reset](https://ck.uesp.net/wiki/Reset_-_Quest "Reset - Quest")()**

-   Resets this quest.

**[SetActive](https://ck.uesp.net/wiki/SetActive_-_Quest "SetActive - Quest")(Bool _abActive_)**

-   Sets or clears this quest as "active". (Tracked by the player)

**Bool [SetCurrentStageID](https://ck.uesp.net/wiki/SetCurrentStageID_-_Quest "SetCurrentStageID - Quest")(Int _aiStageID_)**

-   Sets the quest to the requested stage, returning true if it succeeded.

**[SetObjectiveCompleted](https://ck.uesp.net/wiki/SetObjectiveCompleted_-_Quest "SetObjectiveCompleted - Quest")(Int _aiObjective_, Bool _abCompleted_)**

-   Sets whether the specified objective is completed or not.

**[SetObjectiveDisplayed](https://ck.uesp.net/wiki/SetObjectiveDisplayed_-_Quest "SetObjectiveDisplayed - Quest")(Int _aiObjective_, Bool _abDisplayed_)**

-   Sets whether the specified objective is displayed or not.

**[SetObjectiveFailed](https://ck.uesp.net/wiki/SetObjectiveFailed_-_Quest "SetObjectiveFailed - Quest")(Int _aiObjective_, Bool _abFailed_)**

-   Sets whether the specified objective is failed or not.

**Bool [SetStage](https://ck.uesp.net/wiki/SetCurrentStageID_-_Quest "SetCurrentStageID - Quest")(Int _aiStage_)**

-   Alias of SetCurrentStageID().

**Bool [Start](https://ck.uesp.net/wiki/Start_-_Quest "Start - Quest")()**

-   Starts this quest.

**[Stop](https://ck.uesp.net/wiki/Stop_-_Quest "Stop - Quest")()**

-   Stops the quest.

**Bool [UpdateCurrentInstanceGlobal](https://ck.uesp.net/wiki/UpdateCurrentInstanceGlobal_-_Quest "UpdateCurrentInstanceGlobal - Quest")(GlobalVariable _aUpdateGlobal_)**

-   Updates the value for the given global for the quest's current instance.

## SKSE Global Functions

**Quest [GetQuest](https://ck.uesp.net/wiki/GetQuest_-_Quest "GetQuest - Quest")(String _editorID_)**

-   Returns the Quest with the specified editor id.

## SKSE Functions

**String [GetID](https://ck.uesp.net/wiki/GetID_-_Quest "GetID - Quest")()**

-   Returns the editor ID of the Quest.

**Int [GetPriority](https://ck.uesp.net/wiki/GetPriority_-_Quest "GetPriority - Quest")()**

-   Returns the priority of the Quest.

**Int [GetNumAliases](https://ck.uesp.net/w/index.php?title=GetNumAliases_-_Quest&action=edit&redlink=1 "GetNumAliases - Quest (page does not exist)")()**

-   Returns the number of aliases associated with the Quest.

**Alias [GetNthAlias](https://ck.uesp.net/wiki/GetNthAlias_-_Quest "GetNthAlias - Quest")(Int _index_)**

-   Returns the specified alias associated with the Quest.

**Alias [GetAliasByName](https://ck.uesp.net/wiki/GetAliasByName_-_Quest "GetAliasByName - Quest")(String _name_)**

-   Returns the specified alias associated with the Quest.

## Events

**[OnStoryActivateActor](https://ck.uesp.net/wiki/OnStoryActivateActor_-_Quest "OnStoryActivateActor - Quest")(Location _akLocation_, ObjectReference _akActor_)**

-   Sent when this quest is started by an activate actor story manager event.

**[OnStoryAddToPlayer](https://ck.uesp.net/wiki/OnStoryAddToPlayer_-_Quest "OnStoryAddToPlayer - Quest")(ObjectReference _akOwner_, ObjectReference _akContainer_, Location _akLocation_, Form _akItemBase_, Int _aiAcquireType_)**

-   Sent when this quest is started by an add to player story manager event.

**[OnStoryArrest](https://ck.uesp.net/wiki/OnStoryArrest_-_Quest "OnStoryArrest - Quest")(ObjectReference _akArrestingGuard_, ObjectReference _akCriminal_, Location _akLocation_, Int _aiCrime_)**

-   Sent when this quest is started by an arrest story manager event.

**[OnStoryAssaultActor](https://ck.uesp.net/wiki/OnStoryAssaultActor_-_Quest "OnStoryAssaultActor - Quest")(ObjectReference _akVictim_, ObjectReference _akAttacker_, Location _akLocation_, Int _aiCrime_)**

-   Sent when this quest is started by an assault actor story manager event.

**[OnStoryBribeNPC](https://ck.uesp.net/wiki/OnStoryBribeNPC_-_Quest "OnStoryBribeNPC - Quest")(ObjectReference _akActor_)**

-   Sent when this quest is started by a bribe NPC story manager event.

**[OnStoryCastMagic](https://ck.uesp.net/wiki/OnStoryCastMagic_-_Quest "OnStoryCastMagic - Quest")(ObjectReference _akCastingActor_, ObjectReference _akSpellTarget_, Location _akLocation_, Form _akSpell_)**

-   Sent when this quest is started by a cast magic story manager event.

**[OnStoryChangeLocation](https://ck.uesp.net/wiki/OnStoryChangeLocation_-_Quest "OnStoryChangeLocation - Quest")(ObjectReference _akActor_, Location _akOldLocation_, Location _akNewLocation_)**

-   Sent when this quest is started by a change location story manager event.

**[OnStoryCraftItem](https://ck.uesp.net/wiki/OnStoryCraftItem_-_Quest "OnStoryCraftItem - Quest")(ObjectReference _akBench_, Location _akLocation_, Form _akCreatedItem_)**

-   Sent when this quest is started by a craft item story manager event.

**[OnStoryCrimeGold](https://ck.uesp.net/wiki/OnStoryCrimeGold_-_Quest "OnStoryCrimeGold - Quest")(ObjectReference _akVictim_, ObjectReference _akCriminal_, Faction _akFaction_, Int _aiGoldAmount_, Int _aiCrime_)**

-   Sent when this quest is started by a crime gold story manager event.

**[OnStoryCure](https://ck.uesp.net/wiki/OnStoryCure_-_Quest "OnStoryCure - Quest")(Form _akInfection_)**

-   Sent when this quest is started by a cure story manager event.

**[OnStoryDialogue](https://ck.uesp.net/wiki/OnStoryDialogue_-_Quest "OnStoryDialogue - Quest")(Location _akLocation_, ObjectReference _akActor1_, ObjectReference _akActor2_)**

-   Sent when this quest is started by a dialogue story manager event.

**[OnStoryDiscoverDeadBody](https://ck.uesp.net/wiki/OnStoryDiscoverDeadBody_-_Quest "OnStoryDiscoverDeadBody - Quest")(ObjectReference _akActor_, ObjectReference _akDeadActor_, Location _akLocation_)**

-   Sent when this quest is started by a discover dead body story manager event.

**[OnStoryEscapeJail](https://ck.uesp.net/wiki/OnStoryEscapeJail_-_Quest "OnStoryEscapeJail - Quest")(Location _akLocation_, Form _akCrimeGroup_)**

-   Sent when this quest is started by an escape jail story manager event.

**[OnStoryFlatterNPC](https://ck.uesp.net/wiki/OnStoryFlatterNPC_-_Quest "OnStoryFlatterNPC - Quest")(ObjectReference _akActor_)**

-   Sent when this quest is started by a flatter NPC story manager event.

**[OnStoryHello](https://ck.uesp.net/wiki/OnStoryHello_-_Quest "OnStoryHello - Quest")(Location _akLocation_, ObjectReference _akActor1_, ObjectReference _akActor2_)**

-   Sent when this quest is started by a hello story manager event.

**[OnStoryIncreaseLevel](https://ck.uesp.net/wiki/OnStoryIncreaseLevel_-_Quest "OnStoryIncreaseLevel - Quest")(Int _aiNewLevel_)**

-   Sent when this quest is started by an increase level story manager event.

**[OnStoryIncreaseSkill](https://ck.uesp.net/wiki/OnStoryIncreaseSkill_-_Quest "OnStoryIncreaseSkill - Quest")(String _asSkill_)**

-   Sent when this quest is started by an increase skill story manager event.

**[OnStoryInfection](https://ck.uesp.net/wiki/OnStoryInfection_-_Quest "OnStoryInfection - Quest")(ObjectReference _akTransmittingActor_, Form _akInfection_)**

-   Sent when this quest is started by an infection story manager event.

**[OnStoryIntimidateNPC](https://ck.uesp.net/wiki/OnStoryIntimidateNPC_-_Quest "OnStoryIntimidateNPC - Quest")(ObjectReference _akActor_)**

-   Sent when this quest is started by an intimidate NPC story manager event.

**[OnStoryJail](https://ck.uesp.net/wiki/OnStoryJail_-_Quest "OnStoryJail - Quest")(ObjectReference _akGuard_, Form _akCrimeGroup_, Location _akLocation_, Int _aiCrimeGold_)**

-   Sent when this quest is started by a jail story manager event.

**[OnStoryKillActor](https://ck.uesp.net/wiki/OnStoryKillActor_-_Quest "OnStoryKillActor - Quest")(ObjectReference _akVictim_, ObjectReference _akKiller_, Location _akLocation_, Int _aiCrimeStatus_, Int _aiRelationshipRank_)**

-   Sent when this quest is started by a kill actor story manager event.

**[OnStoryNewVoicePower](https://ck.uesp.net/wiki/OnStoryNewVoicePower_-_Quest "OnStoryNewVoicePower - Quest")(ObjectReference _akActor_, Form _akVoicePower_)**

-   Sent when this quest is started by a new voice power story manager event.

**[OnStoryPickLock](https://ck.uesp.net/wiki/OnStoryPickLock_-_Quest "OnStoryPickLock - Quest")(ObjectReference _akActor_, ObjectReference _akLock_)**

-   Sent when this quest is started by a pick lock story manager event.

**[OnStoryPayFine](https://ck.uesp.net/wiki/OnStoryPayFine_-_Quest "OnStoryPayFine - Quest")(ObjectReference _akCriminal_, ObjectReference _akGuard_, Form _akCrimeGroup_, Int _aiCrimeGold_)**

-   Sent when this quest is started by a pay fine story manager event.

**[OnStoryPlayerGetsFavor](https://ck.uesp.net/wiki/OnStoryPlayerGetsFavor_-_Quest "OnStoryPlayerGetsFavor - Quest")(ObjectReference _akActor_)**

-   Sent when this quest is started by a player gets favor story manager event.

**[OnStoryRelationshipChange](https://ck.uesp.net/wiki/OnStoryRelationshipChange_-_Quest "OnStoryRelationshipChange - Quest")(ObjectReference _akActor1_, ObjectReference _akActor2_, Int _aiOldRelationship_, Int _aiNewRelationship_)**

-   Sent when this quest is started by a relationship change story manager event.

**[OnStoryRemoveFromPlayer](https://ck.uesp.net/wiki/OnStoryRemoveFromPlayer_-_Quest "OnStoryRemoveFromPlayer - Quest")(ObjectReference _akOwner_, ObjectReference _akItem_, Location _akLocation_, Form _akItembase_, Int _aiRemoveType_)**

-   Sent when this quest is started by a remove from player story manager event.

**[OnStoryScript](https://ck.uesp.net/wiki/OnStoryScript_-_Quest "OnStoryScript - Quest")(Keyword _akKeyword_, Location _akLocation_, ObjectReference _akRef1_, ObjectReference _akRef2_, Int _aiValue1_, Int _aiValue2_)**

-   Sent when this quest is started by a script story manager event.

**[OnStoryServedTime](https://ck.uesp.net/wiki/OnStoryServedTime_-_Quest "OnStoryServedTime - Quest")(Location _akLocation_, Form _akCrimeGroup_, Int _aiCrimeGold_, Int _aiDaysJail_)**

-   Sent when this quest is started by a served time story manager event.

**[OnStoryTrespass](https://ck.uesp.net/wiki/OnStoryTrespass_-_Quest "OnStoryTrespass - Quest")(ObjectReference _akVictim_, ObjectReference _akTrespasser_, Location _akLocation_, Int _aiCrime_)**

-   Sent when this quest is started by a trespass story manager event.



-   [Quest Stage Fragments](https://ck.uesp.net/wiki/Quest_Stage_Fragments "Quest Stage Fragments")