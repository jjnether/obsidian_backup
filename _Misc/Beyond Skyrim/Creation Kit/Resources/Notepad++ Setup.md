Notepad++ is a freeware text editor that can be used to edit and compile Papyrus scripts. It can be downloaded from the [official Notepad++ site](http://notepad-plus-plus.org/download/). Notepad++ supports user-defined syntax highlighting autocomplete, folding, and can be set up to quickly compile Papyrus scripts, making it a more robust option than using the basic in-editor text editor.

## Setting up a quick compile

1.  Open Notepad++
2.  Hit F5 (run)
3.  Paste the following line into the input in the "Run..." dialogue window in Notepad++:
    
    ```
    "C:\Program Files (x86)\Steam\steamapps\common\skyrim\Papyrus Compiler\ScriptCompile.bat" "$(FILE_NAME)" "$(CURRENT_DIRECTORY)"
    ```
    
    NOTE: Inside the first quotes, paste in the equivalent path on your PC that points to the ScriptCompile.bat file.
4.  Select Save...
5.  Name it something useful like "Compile Papyrus"
6.  Set up a keyboard shortcut if you want, such as CTRL+F5.

-   You can find the new shortcut under the Run menu option, or just use your keyboard shortcut if you defined one. (If you attempt to use the shortcut and nothing happens, double check that you have linked the shortcut to the ScriptCompile.bat file, and not the PapyrusCompiler.exe)
-   You can change the keyboard shortcut under Run -> Modify Shortcut/Delete Command
-   This will compile the script you are currently tabbed to while in Notepad++.
-   NOTE: By default and after any Creation Kit updates, you'll find the batch file will not work initially as it's pointed to Bethesda's developer directory. To set it up for your Skyrim installation, Right-Click > Edit "Skyrim\\Papyrus Compiler\\ScriptCompile.bat" and make sure its filepaths are pointed to your Skyrim. For a default installation, the following should work

```
cd %2
"%~dp0PapyrusCompiler" %1 -f="TESV_Papyrus_Flags.flg" -i="%~dp0..\Data\Scripts\Source" -o="%~dp0..\Data\Scripts"
pause

```

-   See the [Papyrus Compiler Reference](https://ck.uesp.net/wiki/Papyrus_Compiler_Reference "Papyrus Compiler Reference") for more information on using the compiler.

### Advanced Compiler

There is also a more advanced compiler script avaiable that offers the feature of defining additional import directories and some more comfort.

```
@ECHO OFF
mode 100,50
VERIFY > nul
CLS
:: read Skyrim path from registry and write the line containing the result to a temporary file
if %PROCESSOR_ARCHITECTURE%==x86 (
  REG QUERY "HKEY_LOCAL_MACHINE\SOFTWARE\Bethesda Softworks\Skyrim" /v "Installed Path" | FINDSTR /R "\<.:">"%Temp%\SkyrimPath.txt"
) else (
  REG QUERY "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Bethesda Softworks\Skyrim" /v "Installed Path" | FINDSTR /R "\<.:">"%Temp%\SkyrimPath.txt"
)

::The "\<.:" means a line with any characters containing a colon. However key name and key type are included

:: read Skyrim path from the temporary file and save it to a variable
SET /P Skyrim=<"%Temp%\SkyrimPath.txt"

:: Remove Spaces
set TempSkyrim=%Skyrim: =%

:: Trim keyname and keytype and save Skyrim directory path
set Skyrim=%TempSkyrim:InstalledPathREG_SZ=%


:: delete the temporary file
DEL /F "%Temp%\SkyrimPath.txt"

cd \

:: detect 64 bit H/W see http://ss64.com/nt/syntax-64bit.html

IF NOT %PROCESSOR_ARCHITECTURE% == x86 (
Pushd %Skyrim:~64%
GOTO SIXTYFOUR
)
IF DEFINED PROCESSOR_ARCHITEW6432 (
Pushd %Skyrim:~64%
) else (
Pushd %Skyrim:~32%
)
:SIXTYFOUR


:: retrieved path is invalid
IF NOT %ErrorLevel%==0 (
    echo(
ECHO I hope you saved this script in the Skyrim directory or at least a subdirectory.
echo(
:: script in Skyrim directory?
IF EXIST "%~dp0\TESV.exe" (
CD /D "%~dp0"
) ELSE (
:: script in Skyrim subdirectory?
IF EXIST "%~dp0\..\TESV.exe" (
CD /D "%~dp0\.."
) ELSE (
:: failed to retrieve the path of the Skyrim directory
echo(
ECHO Failed to retrieve the Skyrim directory.
echo(
GOTO Finish
)
)
)


:: retrieve script directory (output)


SET "Output=%Skyrim%Data\Scripts"

CD %Output%


:: retrieve script source directory (import)
SET "Import=%Output%\Source"
CD %Import%

IF [%2]==[] GOTO NOADDITIONALIMPORTS

    IF [%2]==[ADDITIONAL IMPORTS] (
echo(
    @echo Valid import directory not specified in Notepad++ "Papyrus Compiler.bat" Command line.
GOTO NOADDITIONALIMPORTS
    )

SET "AdditionalImports"="%2"

SET Import=%Import%\;%AdditionalImports:~1,-1%

:NOADDITIONALIMPORTS
:: log paths
echo(
ECHO %%Skyrim%%=%Skyrim%
ECHO %%Import%%=%Import%
ECHO %%Output%%=%Output%

Popd
echo(
echo(
echo(
:: run the compiler

start "PapyrusCompiler" /B "%Skyrim%Papyrus Compiler\PapyrusCompiler.exe" %1 -f="TESV_Papyrus_Flags.flg" -import="%Import%" -output="%Output%"

:LOOP
timeout /t 1 /nobreak > nul
tasklist /fi "IMAGENAME eq PapyrusCompiler.exe" | find /i "PapyrusCompiler.exe" > nul
if errorlevel 1 goto Finish
if errorlevel 0 goto LOOP
ECHO ________________________________________________________________________________
:Finish
ECHO Press any key to exit.
PAUSE>NUL
goto :EOF

```

Save the script anywhere (If an error occurs move this script to the Skyrim directory or a subdirectory e. g. "\\Papyrus Compiler".) and configure Notepad++ to run this:

```
cmd /c ""<SCRIPT DIR>\Papyrus Compiler.bat" "$(FULL_CURRENT_PATH)" "<ADDITIONAL IMPORTS>""

```

(Replace <SCRIPT DIR> with the path name that contains "Papyrus Compiler.bat". You can remove the second parameter which defines additional import directories but if you use it you must put this parameter in quotes for this script to work.)

### Fully Integrated Compiler with NppExec (Best Choice)

The best way to integrate any compiler into Notepad++ is to use the NppExec plugin. Your compile output will appear in a window in Notepad++, you can easily copy-paste from it, it will be in color, and you can double-click on any error and it will jump you right to the line and column with the error in the editor. So, it will work like many modern IDEs do when working with compilation and errors.

The best way to use Notepad++ plugins is to to use the Plugin Manager. Unfortunately, as of Notepad++ version 7.5 and later the Plugin Manager was not shipped as part of the default plugins. At that time Notepad++ added an 64-bit build, and the Plugin Manager and many other plugins were not available for x64, so they removed it. However, that problem has since been fixed, and the Plugin Manager and many of the plugins now have x64 versions. In order to check if you have the 32-bit or 64-bit version installed, open Notepad++ and press "F1". If it shows (32-bit) you should uninstall that and install the 64-bit version. You can download the latest version here: [https://notepad-plus-plus.org/downloads/](https://notepad-plus-plus.org/downloads/). The latest version as of this writing is 8.7.1.

Then download and install the [Plugin Manager](https://github.com/bruderstein/nppPluginManager/releases/tag/v1.4.9). The latest version of of this writing is version 1.4.9. Just download the PluginManager\_v1.4.9\_x64.zip, and unzip it to your C:\\Program Files\\Notepad++. It will add one file to the plugins directory, and one file to the updater directory.

Then, launch Notepad++ and go to the Plugins->Plugins Admin... menu. Under the 'Available' tab find NppExec in the list and select the checkbox next to it and select Install. The latest version as of this writing was 0.9. (0.8.8. installed). You may need to restart Notepad++ for the Plugin to take effect.

Now, select Plugins->NppExec->Execute... or press F6. Type the following into the execute dialog box, and press Save... and save it with the name "Papyrus Compiler (Debug)". NOTE: you can also add (Release) and (Release Final) versions of this exec too by adding the -r -op and -r -op -final to the end of the last command. Adjust any of the paths here to your preference, this is for Fallout 4 in the default install location with all the DLC, and working on scripts out of the Data\\Scripts\\Source\\User directory. NOTE: this does not require any changes to the ScriptCompile.bat file (or the others), since they is not used. This invokes the compiler directly.

```
npe_console -- m-
npp_save
set local fo4 = C:\Program Files (x86)\Steam\steamapps\common\Fallout 4\
set local scripts = $(fo4)\Data\Scripts
set local source = $(scripts)\Source
npp_console -
cd $(CURRENT_DIRECTORY)
npp_console +
"$(fo4)Papyrus Compiler\PapyrusCompiler.exe" "$(FILE_NAME)" -f="Institute_Papyrus_Flags.flg" -i="$(source)\user;$(source)\DLC06;$(source)\DLC05;$(source)\DLC04;$(source)\DLC03;$(source)\DLC02;$(source)\DLC01;$(source)\Base" -o="$(scripts)"

```

The Papyrus Compiler may require the full path/filename instead of just the filename to deal with namespaces in code:

```
npe_console -- m-
npp_save
set local fo4 = C:\Program Files (x86)\Steam\steamapps\common\Fallout 4\
set local papyrus = $(fo4)\Papyrus Compiler\PapyrusCompiler.exe
set local scripts = $(fo4)\Data\Scripts
set local source = $(scripts)\Source
set local include = $(source)\user;$(source)\base;$(source)
"$(papyrus)" "$(CURRENT_DIRECTORY)\$(FILE_NAME)" -f="Institute_Papyrus_Flags.flg" -i="$(include)" -o="$(scripts)"

```

For Skyrim Special Edition use the following code instead:

```
npe_console -- m-
npp_save
set local sse = C:\Program Files (x86)\Steam\steamapps\common\Skyrim Special Edition\
set local scripts = $(sse)\Data\Scripts
set local source = $(sse)\Data\Source\Scripts
npp_console -
cd $(CURRENT_DIRECTORY)
npp_console +
"$(sse)Papyrus Compiler\PapyrusCompiler.exe" "$(FILE_NAME)" -f="TESV_Papyrus_Flags.flg" -i="$(source)" -o="$(scripts)"

```

Then select Plugins->NppExec->Console Output Filters... and under the Highlight tab add these values as a place to start, then customize to your liking:

```
%FILE%(%LINE%,%CHAR%)*                             select color red      
Compiling "*"*                                     select color blue
No output generated for*                           select color dark red    | select bold
Compilation succeeded.                             select color green

```

Toggle the checkbox in front of each line to activate each filter.

  
And finally, setup the menu item and keyboard shortcut: Plugins->NppExec->Advanced Options... and find the Menu Item section (bottom left of the dialog), give the Menu Item a name "Papyrus Compiler (Debug)" and select the script "Papyrus Compiler (Debug)". Click Add/Modify and it will tell you to restart Notepad++ for the change to take effect, so do that. Now you will have a new menu item Plugins->NppExec->Papyrus Compiler (Debug). To bind a shortcut key to that, go to Settings->Shortcut Mapper...->Plugin Commands->Papyrus Compiler (Debug) and select a shortcut. I use Ctrl-F9 since I've been doing a lot of xEdit Scripting in Object Pascal using Delphi, and that's Delphi's default compile key. But use whatever key you'd like, Notepad++ will tell you if there is a conflict.

In the end, it should look like this:

[![Notepad++ Papyrus Compiler Integration.png](https://ck.uesp.net/w/images/f/f3/Notepad%2B%2B_Papyrus_Compiler_Integration.png)](https://ck.uesp.net/wiki/File:Notepad%2B%2B_Papyrus_Compiler_Integration.png)

## Setting up Papyrus Language Definitions

Notepad++ supports both autocomplete and syntax highlighting for custom language. The following two sections describe the steps you need to take to enable each of these features for Papyrus.

### Autocomplete

1.  Open up Notepad++
2.  Copy the content from this page into a new file: [Papyrus Autocomplete Language Definitions](https://ck.uesp.net/wiki/Papyrus_Autocomplete "Papyrus Autocomplete")
3.  Save the new file as **papyrus.xml** in your _Notepad++\\plugins\\APIs_ directory (for example, _C:\\Program Files (x86)\\Notepad++\\plugins\\APIs_)
4.  In the Backup/Auto-Completion tab of the Preferences window of Notepad++ (under Settings), tick the "Enable auto-completion on each input" and configure the feature to work how you want.  
    Currently, a portion of the functions have parameter information defined, so if you tick "Function parameters hint on input" you will see more information when typing these functions.

### Syntax Highlighting

\[Updated on 23.11.2024, Entries below regarding Syntax Highlighting may be obsolete\]

1.  Create an XML file with the following content (you can call it whatever you like and save it anywhere you like):
    
    \[If you name the file Papyrus.xml and save it under %appdata%\\Roaming\\Notepad++\\UserDefineLangs you can skip steps 2. to 6.\]
    
    ```
    <NotepadPlus>
        <UserLang name="Papyrus" ext="psc" udlVersion="2.1">
            <Settings>
                <Global caseIgnored="yes" allowFoldOfComments="no" foldCompact="no" forcePureLC="2" decimalSeparator="0" />
                <Prefix Keywords1="no" Keywords2="no" Keywords3="no" Keywords4="no" Keywords5="no" Keywords6="no" Keywords7="no" Keywords8="no" />
            </Settings>
            <KeywordLists>
                <Keywords name="Comments">00 01 02 03{ 04}</Keywords>
                <Keywords name="Numbers, prefix1">0x</Keywords>
                <Keywords name="Numbers, prefix2"></Keywords>
                <Keywords name="Numbers, extras1"></Keywords>
                <Keywords name="Numbers, extras2"></Keywords>
                <Keywords name="Numbers, suffix1"></Keywords>
                <Keywords name="Numbers, suffix2"></Keywords>
                <Keywords name="Numbers, range"></Keywords>
                <Keywords name="Operators1">- ! % &amp; ( ) * , . / [ ] | + &lt; = &gt;</Keywords>
                <Keywords name="Operators2"></Keywords>
                <Keywords name="Folders in code1, open"></Keywords>
                <Keywords name="Folders in code1, middle"></Keywords>
                <Keywords name="Folders in code1, close"></Keywords>
                <Keywords name="Folders in code2, open">Event Function Group If Property State Struct While</Keywords>
                <Keywords name="Folders in code2, middle">Else ElseIf</Keywords>
                <Keywords name="Folders in code2, close">Auto Const EndEvent EndFunction EndGroup EndIf EndProperty EndState EndStruct EndWhile Hidden Mandatory Native</Keywords>
                <Keywords name="Folders in comment, open"></Keywords>
                <Keywords name="Folders in comment, middle"></Keywords>
                <Keywords name="Folders in comment, close"></Keywords>
                <Keywords name="Keywords1">As Auto AutoReadOnly BetaOnly Bool Conditional Const DebugOnly Default Extends False Float Global Hidden Import Int Length New None Parent Return ScriptName Self String True Var</Keywords>
                <Keywords name="Keywords2">Action Activator ActiveMagicEffect Actor ActorBase ActorValue Alias Ammo Armor AssociationType Book CameraShot Cell Class CombatStyle Component ConstructibleObject Container Debug Door EffectShader Enchantment EncounterZone Explosion Faction Flora Form FormList Furniture Game GlobalVariable Hazard HeadPart Holotape Idle IdleMarker ImageSpaceModifier ImpactDataSet Ingredient InputEnableLayer InstanceNamingRules Key Keyword LeveledActor LeveledItem LeveledSpell Light Location LocationAlias LocationRefType MagicEffect Math Message MiscObject MovableStatic MusicType ObjectMod ObjectReference Outfit OutputModel Package Perk Potion Projectile Quest Race RefCollectionAlias ReferenceAlias Scene ScriptObject Scroll ShaderParticleGeometry Shout SoulGem Sound SoundCategory SoundCategorySnapshot Spell Static TalkingActivator Terminal Topic TopicInfo Utility VisualEffect VoiceType Weapon Weather WordOfPower WorldSpace</Keywords>
                <Keywords name="Keywords3">abs acos Activate Add AddAchievement AddDependentAnimatedObjectReference AddForm AddInventoryEventFilter AddItem AddKeyword AddLinkedLocation AddPerk AddPerkPoints AddRef AddShout AddSpell AddTextReplacementData AddToMap AdvanceSkill AllowBleedoutDialogue AllowPCDialogue Apply ApplyConveyorBelt ApplyCrossFade ApplyFanMotor ApplyHavokImpulse ApplyToRef asin atan AttachAshPile AttachMod AttachModToInventoryItem AttachTo AttemptAnimationSetSwitch BlockActivation CalculateEncounterLevel CallFunction CallFunctionNoWait CallGlobalFunction CallGlobalFunctionNoWait CancelTimer CancelTimerGameTime CanFastTravelToMarker CanFlyHere CanMoveVertical CanPayCrimeGold CanProduceForWorkshop CanStrafe CaptureFrameRate Cast CastAs Ceiling CenterOnCell CenterOnCellAndWait ChangeAnimArchetype ChangeAnimFaceArchetype ChangeAnimFlavor ChangeHeadPart Clear ClearArrested ClearDestruction ClearExpressionOverride ClearExtraArrows ClearForcedMovement ClearFromOldLocations ClearHelpMessages ClearKeepOffsetFromActor ClearLookAt ClearPrison ClearTempEffects CloseUserLog CompleteAllObjectives CompleteQuest ConveyorBeltOn cos CountActors CountActorsLinkedToMe CountLinkedRefChain CountRefsLinkedToMe Create CreateDetectionEvent DamageActorValue DamageAV DamageObject DamageValue DBSendPlayerPosition DegreesToRadians Delete Disable DisableLinkChain DisableNoWait Dismember Dismount Dispel DispelAllSpells DispelSpell DoCombatSpellApply DogDropItems DogPlaceInMouth DrawWeapon Drop DropFirstObject DropObject DumpAliasData DumpEventRegistrations Enable EnableActivate EnableAI EnableAmbientParticles EnableCamSwitch EnableCollisions EnableDetection EnableFastTravel EnableFavorites EnableFighting EnableJournal EnableJumping EnableLinkChain EnableLooking EnableMenu EnableMenus EnableMovement EnableNoWait EnablePipboyHDRMask EnableRunning EnableSneaking EnableSprinting EnableVATS EnableZKey EndDeferredKill EndFrameRateCapture EnterTestData EquipItem EquipShout EquipSpell Error EvaluatePackage FadeOutGame FailAllObjectives FanMotorOn FastTravel Find FindAllReferencesOfType FindAllReferencesWithKeyword FindClosestActor FindClosestReferenceOfAnyTypeInList FindClosestReferenceOfType FindRandomActor FindRandomReferenceOfAnyTypeInList FindRandomReferenceOfType FindWeather Fire Floor ForceActive ForceActorValue ForceAV ForceAddRagdollToWorld ForceDisableSSRGodraysDirLight ForceFirstPerson ForceLocationTo ForceMovementDirection ForceMovementDirectionRamp ForceMovementRotationSpeed ForceMovementRotationSpeedRamp ForceMovementSpeed ForceMovementSpeedRamp ForceRefTo ForceRemoveRagdollFromWorld ForceStart ForceTargetAngle ForceTargetDirection ForceTargetSpeed ForceThirdPerson GameTimeToString GetActorOwner GetActorRefOwner GetActors GetActorsLinkedToMe GetActorValue GetActorValueMax GetActorValuePercentage GetAV GetAVMax GetAVPercentage GetAggressionAV GetAgilityAV GetAlias GetAllCombatTargets GetAllItemsCount GetAllLinkedLocations GetAmmo GetAngleX GetAngleY GetAngleZ GetAnimationVariableBool GetAnimationVariableFloat GetAnimationVariableInt GetAssociatedForm GetAssociatedSkill GetAt GetAverageFrameRate GetBaseActorValue GetBaseAV GetBaseObject GetBaseValue GetBribeAmount GetBudgetCount GetBudgetLimit GetBudgetName GetCasterActor GetCharismaAV GetClass GetClassification GetCombatState GetCombatTarget GetComponentCount GetConfidenceAV GetConfigName GetContainer GetCount GetCrimeFaction GetCrimeGold GetCrimeGoldNonViolent GetCrimeGoldViolent GetCurrentBudget GetCurrentDestructionStage GetCurrentGameTime GetCurrentLocation GetCurrentMemory GetCurrentPackage GetCurrentRealTime GetCurrentScene GetCurrentStackID GetCurrentStageID GetCurrentWeather GetCurrentWeatherTransition GetDeadCount GetDialogueTarget GetDifficulty GetDistance GetDuration GetEditorLocation GetEncounterZone GetEnduranceAV GetEquippedArmorInSlot GetEquippedItemType GetEquippedShield GetEquippedShout GetEquippedSpell GetEquippedWeapon GetFactionOwner GetFactionRank GetFactionReaction GetFlyingState GetForcedLandingMarker GetForm GetFormFromFile GetFormID GetGameSettingFloat GetGameSettingInt GetGameSettingString GetGiftFilter GetGoldAmount GetGoldValue GetHeadingAngle GetHealthAV GetHeight GetHighestRelationshipRank GetInfamy GetInfamyNonViolent GetInfamyViolent GetIntelligenceAV GetInventoryValue GetItemCount GetItemHealthPercent GetKey GetKeywordData GetKiller GetLength GetLevel GetLeveledActorBase GetLevelExact GetLightLevel GetLinkedRef GetLinkedRefChain GetLinkedRefChildren GetLocation GetLockLevel GetLocRefTypes GetLowestRelationshipRank GetLuckAV GetMass GetMaxFrameRate GetMinFrameRate GetNoBleedoutRecovery GetNthLinkedRef GetObjectComponentCount GetOpenState GetOutgoingWeather GetOwningQuest GetParentCell GetPerceptionAV GetPlatformName GetPlayer GetPlayerControls GetPlayerFollowers GetPlayerGrabbedRef GetPlayerRadioFrequency GetPlayersLastRiddenHorse GetPositionX GetPositionY GetPositionZ GetPropertyValue GetRace GetRadioFrequency GetRadioVolume GetReaction GetRealHoursPassed GetReference GetRefsLinkedToMe GetRefTypeAliveCount GetRefTypeDeadCount GetRelationshipRank GetResourceDamage GetSafePosition GetScale GetSex GetSitState GetSize GetSkyMode GetSleepState GetStolenItemValueCrime GetStolenItemValueNoCrime GetStrengthAV GetSuspiciousAV GetTargetActor GetTeleportCell GetTemplate GetTimeElapsed GetTransitionCell GetTransmitterDistance GetTriggerObjectCount GetUniqueActor GetValue GetValuePercentage GetVersionNumber GetVoiceRecoveryTime GetVoiceType GetWarmthRating GetWidth GetWorkshopOwnedObjects GetWorkshopResourceDamage GetWorkshopResourceObjects GetWorldSpace GetXPForLevel HasActorRefOwner HasAssociation HasBeenSaid HasCommonParent HasDetectionLOS HasDirectLOS HasEffectKeyword HasEverBeenCleared HasFamilyRelationship HasForm HasKeyword HasKeywordInFormList HasLocRefType HasLOS HasMagicEffect HasMagicEffectWithKeyword HasNode HasObjective HasParentRelationship HasPerk HasRefType HasSharedPowerGrid HasSpell HideTitleSequenceMenu IgnoreFriendlyHits IncrementSkill IncrementStat InitializeMarkerDistances InterruptCast Is3DLoaded IsActionComplete IsActivateChild IsActivateControlsEnabled IsActivateEnabled IsActivationBlocked IsActive IsAIEnabled IsAlarmed IsAlerted IsAllowedToFly IsArrested IsArrestingTarget IsAttached IsBeingRidden IsBeingRiddenBy IsBleedingOut IsBoundGameObjectAvailable IsBribed IsCamSwitchControlsEnabled IsCamSwitchEnabled IsChild IsCleared IsCommandedActor IsCompleted IsContainerEmpty IsConveyorBeltOn IsCreated IsDead IsDeleted IsDestroyed IsDetectedBy IsDisabled IsDismembered IsDoingFavor IsEquipped IsEssential IsFactionInCrimeGroup IsFanMotorOn IsFastTravelControlsEnabled IsFastTravelEnabled IsFavoritesControlsEnabled IsFavoritesEnabled IsFightingControlsEnabled IsFightingEnabled IsFlying IsFurnitureInUse IsFurnitureMarkerInUse IsGhost IsGuard IsHostile IsHostileToActor IsIgnoringFriendlyHits IsInCombat IsInDialogueWithPlayer IsInFaction IsInIronSights IsInKillMove IsInMenuMode IsInScene IsInterior IsIntimidated IsInvulnerable IsJournalControlsEnabled IsJournalEnabled IsJumpingControlsEnabled IsJumpingEnabled IsLinkedLocation IsLoaded IsLockBroken IsLocked IsLookingControlsEnabled IsLookingEnabled IsMapMarkerVisible IsMenuControlsEnabled IsMenuEnabled IsMovementControlsEnabled IsMovementEnabled IsObjectiveCompleted IsObjectiveDisplayed IsObjectiveFailed IsOnMount IsOverEncumbered IsOwnedBy IsPlayerEnemy IsPlayerExpelled IsPlayerInRadioRange IsPlayerListening IsPlayerRadioOn IsPlayersLastRiddenHorse IsPlayerTeammate IsPlaying IsPluginInstalled IsPowered IsProtected IsQuestItem IsRadio IsRadioOn IsRefInTransitionCell IsRunning IsRunningEnabled IsSeatOccupied IsSneaking IsSneakingControlsEnabled IsSneakingEnabled IsSprinting IsSprintingEnabled IsStageDone IsStarting IsStopped IsStopping IsTalking IsTargetInTrigger IsTeleportAreaLoaded IsTrespassing IsUnconscious IsUnique IsVATSControlsEnabled IsVATSEnabled IsVATSPlaybackActive IsWeaponDrawn IsWithinBuildableArea IsZKeyEnabled Kill KillSilent KeepOffsetFromActor KnockAreaEffect LearnAllEffects LearnEffect LearnNextEffect Lock MakeRadioReceiver MakeTransmitterRepeater MarkItemAsFavorite MergeWith MessageBox ModCrimeGold ModFactionRank ModActorValue ModAV ModReaction ModValue MoveTo MoveToInteractionLocation MoveToMyEditorLocation MoveToNearestNavmeshLocation MoveToNode MoveToPackageLocation Mute Notification OpenInventory OpenUserLog OpenWorkshopSettlementMenu OpenWorkshopSettlementMenuEx OverBudget PassTime PathToReference Pause PauseAudio PlaceActorAtMe PlaceAtMe PlaceAtNode Play PlayAndWait PlayAnimation PlayAnimationAndWait PlayerKnows PlayerMoveToAndWait PlayerPayCrimeGold PlayEventCamera PlayGamebryoAnimation PlayIdle PlayIdleAction PlayIdleWithTarget PlayImpactEffect PlaySubGraphAnimation PlaySyncedAnimationAndWaitSS PlaySyncedAnimationSS PlayTerrainEffect PopTo PostStartUpTimes pow PrecacheCharGen PrecacheCharGenClear PreloadExteriorCell PreloadTargetArea ProcessTrapHit Push PushActorAway QueryStat QuitGame QuitToMainMenu RadiansToDegrees RaidTargetsAvailable RandomFloat RandomInt RecalculateResources RegisterForActorAction RegisterForAnimationEvent RegisterForCameraState RegisterForControl RegisterForCrosshairRef RegisterForCustomEvent RegisterForDetectionLOSGain RegisterForDetectionLOSLost RegisterForDirectLOSGain RegisterForDirectLOSLost RegisterForDistanceGreaterThanEvent RegisterForDistanceLessThanEvent RegisterForHitEvent RegisterForKey RegisterForLooksMenuEvent RegisterForLOS RegisterForMagicEffectApplyEvent RegisterForMenu RegisterForMenuOpenCloseEvent RegisterForModEvent RegisterForNiNodeUpdate RegisterForPlayerSleep RegisterForPlayerTeleport RegisterForPlayerWait RegisterForRadiationDamageEvent RegisterForRemoteEvent RegisterForSingleLOSGain RegisterForSingleLOSLost RegisterForSingleUpdate RegisterForSingleUpdateGameTime RegisterForSleep RegisterForTrackedStatsEvent RegisterForTutorialEvent RegisterForUpdate RegisterForUpdateGameTime ReleaseOverride RemoteCast Remove RemoveAddedForm RemoveAll RemoveAllInventoryEventFilters RemoveAllItems RemoveAllMods RemoveAllModsFromInventoryItem RemoveAllStolenItems RemoveComponents RemoveCrossFade RemoveDependentAnimatedObjectReference RemoveFromAllFactions RemoveFromFaction RemoveFromRef RemoveInventoryEventFilter RemoveItem RemoveItemByComponent RemoveKeyword RemoveLinkedLocation RemoveMod RemoveModFromInventoryItem RemovePerk RemoveRef RemoveShout RemoveSpell Repair RequestAutoSave RequestModel RequestSave Reset ResetHealthAndLimbs ResetHelpMessage ResetKeyword ResetSpeechChallenges RestoreActorValue RestoreAV RestoreValue ResumeAudio Resurrect ReverseConveyorBelt Revert RewardPlayerXP Say SayCustom SendAnimationEvent SendAssaultAlarm SendCustomEvent SendLycanthropyStateChanged SendPlayerToJail SendStealAlarm SendTrespassAlarm SendVampirismStateChanged ServeTime SetActivateTextOverride SetActive SetActorCause SetActorOwner SetActorRefOwner SetActorValue SetAlert SetAllowFlying SetAllowFlyingEx SetAlly SetAlpha SetAngle SetAnimationVariableBool SetAnimationVariableFloat SetAnimationVariableInt SetAttackActorOnSight SetAttractionActive SetAV SetAvoidPlayer SetBribed SetCameraTarget SetCanDoCommand SetCharGenHUDMode SetCleared SetCombatStyle SetCommandState SetContainerAllowStolenItems SetConveyorBeltVelocity SetCrimeFaction SetCrimeGold SetCrimeGoldViolent SetCriticalStage SetCurrentStageID SetDestroyed SetDirectAtTarget SetDoingFavor SetDontMove SetEnemy SetEssential SetExpressionOverride SetEyeTexture SetFactionOwner SetFactionRank SetFogPlanes SetFogPower SetFootIK SetForcedLandingMarker SetFrequency SetGhost SetGodMode SetHarvested SetHasCharGenSkeleton SetHeadTracking SetInChargen SetINIBool SetINIFloat SetINIInt SetINIString SetInsideMemoryHUDMode SetInstanceVolume SetIntimidated SetInvulnerable SetKeywordData SetLinkedRef SetLockLevel SetLocRefType SetLookAt SetMotionType SetNoBleedoutRecovery SetNoFavorAllowed SetNotShowOnStealthMeter SetObjectiveCompleted SetObjectiveDisplayed SetObjectiveFailed SetOpen SetOutfit SetOverrideVoiceType SetPersistLoc SetPlayerAIDriven SetPlayerControls SetPlayerEnemy SetPlayerExpelled SetPlayerHasTaken SetPlayerOnElevator SetPlayerRadioFrequency SetPlayerReportCrime SetPlayerResistingArrest SetPlayerTeammate SetPosition SetPropertyValue SetPropertyValueNoWait SetProtected SetPublic SetRace SetRadioFrequency SetRadioOn SetRadioVolume SetReaction SetRelationshipRank SetRestrained SetScale SetSittingRotation SetSubGraphFloatVariable SetTargetInTrigger SetUnconscious SetValue SetVehicle SetVoiceRecoveryTime SetVolume ShakeCamera ShakeController Show ShowAllMapMarkers ShowAsHelpMessage ShowBarterMenu ShowFatigueWarningOnHUD ShowFirstPersonGeometry ShowGiftMenu ShowOnPipboy ShowPerkVaultBoyOnHUD ShowPipboyBootSequence ShowPipboyPlugin ShowRaceMenu ShowRefPosition ShowSPECIALMenu ShowTitleSequenceMenu ShowTrainingMenu sin SnapIntoInteraction SplineTranslateTo SplineTranslateToRefNode sqrt Start StartCannibal StartCombat StartDeferredKill StartDialogueCameraOrCenterOnTarget StartFrameRateCapture StartFrenzyAttack StartObjectProfiling StartScriptProfiling StartSneaking StartStackProfiling StartStackRootProfiling StartTimer StartTimerGameTime StartTitleSequence StartVampireFeed StartWorkshop Stop StopCombat StopCombatAlarm StopDialogueCamera StopInstance StopObjectProfiling StopScriptProfiling StopStackProfiling StopStackRootProfiling StopTranslation StoreInWorkshop SwitchToPowerArmor tan TetherToHorse Trace TraceFunction TraceStack TraceUser TranslateTo TrapSoul TriggerScreenBlood TurnPlayerRadioOn UnequipAll UnequipItem UnequipItemSlot UnequipShout UnequipSpell UnLockOwnedDoorsInCell UnMute UnPause UnregisterForActorAction UnregisterForAllControls UnregisterForAllCustomEvents UnregisterForAllEvents UnregisterForAllHitEvents UnregisterForAllKeys UnregisterForAllMagicEffectApplyEvents UnregisterForAllMenuOpenCloseEvents UnregisterForAllMenus UnregisterForAllModEvents UnregisterForAllRadiationDamageEvents UnregisterForAllRemoteEvents UnregisterForAllTrackedStatsEvents UnregisterForAnimationEvent UnregisterForCameraState UnregisterForControl UnregisterForCrosshairRef UnregisterForCustomEvent UnregisterForDistanceEvents UnregisterForHitEvent UnregisterForKey UnregisterForLooksMenuEvent UnregisterForLOS UnregisterForMagicEffectApplyEvent UnregisterForMenu UnregisterForMenuOpenCloseEvent UnregisterForModEvent UnregisterForNiNodeUpdate UnregisterForPlayerSleep UnregisterForPlayerTeleport UnregisterForPlayerWait UnregisterForRadiationDamageEvent UnregisterForRemoteEvent UnregisterForSleep UnregisterForTrackedStatsEvent UnregisterForTutorialEvent UnregisterForUpdate UnregisterForUpdateGameTime UnshowAsHelpMessage UpdateCurrentInstanceGlobal UsingGamepad Wait WaitFor3DLoad WaitForAnimationEvent WaitForWorkshopResourceRecalc WaitGameTime WaitMenuMode Warning WillIntimidateSucceed WornHasKeyword WouldBeStealing WouldRefuseCommand</Keywords>
                <Keywords name="Keywords4">AddArray AddKeyIfNeeded AddRefCollection AddToFaction AllowCompanion BlockActivation ClearForcedLandingMarker DebugChannelNotify DeleteWhenAble DisableAll DisablePlayerControls DisallowCompanion EnableAll EnablePlayerControls EvaluateAll FindClosestActorFromRef FindClosestReferenceOfAnyTypeInListFromRef FindClosestReferenceOfTypeFromRef FindRandomActorFromRef FindRandomReferenceOfAnyTypeInListFromRef FindRandomReferenceOfTypeFromRef FollowerFollow FollowerSetDistanceFar FollowerSetDistanceMedium FollowerSetDistanceNear FollowerWait ForceRefIfEmpty get GetActorAt GetActorBase GetActorRef GetActorReference GetCaps GetCommonProperties GetFirstOwnedObject GetMagnitude getLinkedRefArray GetPlayerLevel GetQuestStageDone GetRef GetSelfAsActor GetStage GetStageDone GetState GetValueInt GivePlayerCaps GotoState HasOwner HasRefType is running IsEnabled IsInInterior IsInLocation IsInPowerArmor IsNearPlayer IsOwnedObjectInList IsOwner IsSameLocation KillAll KillEssential LinkCollectionTo MakePlayerFriend Max Min Mod ModFavorPoints ModFavorPointsWithGlobal ModifyKeywordData ModObjectiveGlobal MoveAllTo MoveToIfUnloaded MoveToWhenUnloaded PlayBink rampRumble RemoveFromAllFactions RemoveFromFaction RemovePlayerCaps ResetAll SellItem SendModEvent SendStoryEvent SendStoryEventAndWait set SetAllStages SetAnimArchetypeConfident SetAnimArchetypeDepressed SetAnimArchetypeElderly SetAnimArchetypeFriendly SetAnimArchetypeIrritated SetAnimArchetypeNervous SetAnimArchetypeNeutral SetAvailableToBeCompanion SetCompanion SetDogAnimArchetypeAgitated SetDogAnimArchetypeAlert SetDogAnimArchetypeNeutral SetDogAnimArchetypePlayful SetEssential SetFogColor SetObjectiveSkipped SetProtected SetQuestStage SetStage SetValue SetValueInt SplineTranslateToRef StartCombatAll TakeAllShots TakeScreenshot TakeShot ToggleAI ToggleCollisions ToggleMenus TraceAndBox TraceConditional TraceConditionalGlobal TraceSelf TranslateToRef TryToAddToFaction TryToClear TryToDisable TryToDisableNoWait TryToEnable TryToEnableNoWait TryToEvaluatePackage TryToGetActorValue TryToGetValue TryToKill TryToMoveTo TryToRemoveFromFaction TryToReset TryToSetActorValue TryToSetValue TryToStopCombat Unlock</Keywords>
                <Keywords name="Keywords5">OnAction OnActivate OnActorAction OnAliasInit OnAliasReset OnAliasShutdown OnAnimationEvent OnAnimationEventUnregistered OnAttachedToCell OnBegin OnBeginState OnCellAttach OnCellDetach OnCellLoad OnChange OnClose OnCombatStateChanged OnCommandModeCompleteCommand OnCommandModeEnter OnCommandModeExit OnCommandModeGiveCommand OnCompanionDismiss OnConsciousnessStateChanged OnContainerChanged OnControlDown OnControlUp OnCripple OnCrosshairRefChange OnDeath OnDeferredKill OnDestructionStageChanged OnDetachedFromCell OnDifficultyChanged OnDistanceGreaterThan OnDistanceLessThan OnDying OnEffectFinish OnEffectStart OnEnd OnEndState OnEnterBleedout OnEnterSneaking OnEntryRun OnEquipped OnEscortWaitStart OnEscortWaitStop OnExitFurniture OnGainLOS OnGetUp OnGrab OnHit OnHolotapeChatter OnHolotapePlay OnInit OnItemAdded OnItemEquipped OnItemRemoved OnItemUnequipped OnKeyDown OnKeyUp OnKill OnLoad OnLocationChange OnLocationCleared OnLocationLoaded OnLockStateChanged OnLooksMenuEvent OnLostLOS OnLycanthropyStateChanged OnMagicEffectApply OnMenuClose OnMenuItemRun OnMenuOpen OnMenuOpenCloseEvent OnNiNodeUpdate OnObjectEquipped OnObjectUnequipped OnOpen OnPackageChange OnPackageEnd OnPackageStart OnPartialCripple OnPhaseBegin OnPhaseEnd OnPickpocketFailed OnPipboyRadioDetection OnPlayerBowShot OnPlayerCameraState OnPlayerCreateRobot OnPlayerDialogueTarget OnPlayerEnterVertibird OnPlayerFallLongDistance OnPlayerFastTravelEnd OnPlayerFireWeapon OnPlayerHealTeammate OnPlayerLoadGame OnPlayerModArmorWeapon OnPlayerModRobot OnPlayerSleepStart OnPlayerSleepStop OnPlayerSwimming OnPlayerTeleport OnPlayerUseWorkBench OnPlayerWaitStart OnPlayerWaitStop OnPowerOff OnPowerOn OnQuestInit OnQuestShutdown OnRaceSwitchComplete OnRadiationDamage OnRead OnRelease OnReset OnSell OnSit OnSleepStart OnSleepStop OnSpeechChallengeAvailable OnSpellCast OnStageSet OnStart OnStoryActivateActor OnStoryActorAttach OnStoryAddToPlayer OnStoryArrest OnStoryAssaultActor OnStoryAttractionObject OnStoryBribeNPC OnStoryCastMagic OnStoryChangeLocation OnStoryClearLocation OnStoryCraftItem OnStoryCrimeGold OnStoryCure OnStoryDialogue OnStoryDiscoverDeadBody OnStoryEscapeJail OnStoryFlatterNPC OnStoryHackTerminal OnStoryHello OnStoryIncreaseLevel OnStoryIncreaseSkill OnStoryInfection OnStoryIntimidateNPC OnStoryIronSights OnStoryJail OnStoryKillActor OnStoryLocationLoaded OnStoryMineExplosion OnStoryNewVoicePower OnStoryPayFine OnStoryPickLock OnStoryPickPocket OnStoryPlayerGetsFavor OnStoryRelationshipChange OnStoryRemoveFromPlayer OnStoryScript OnStoryServedTime OnStoryTrespass OnTimer OnTimerGameTime OnTrackedStatsEvent OnTranslationAlmostComplete OnTranslationComplete OnTranslationFailed OnTrapHit OnTrapHitStart OnTrapHitStop OnTrigger OnTriggerEnter OnTriggerLeave OnTutorialEvent OnUnequipped OnUnload OnUpdate OnUpdateGameTime OnVampireFeed OnVampirismStateChanged OnWardHit OnWorkshopMode OnWorkshopNPCTransfer OnWorkshopObjectDestroyed OnWorkshopObjectGrabbed OnWorkshopObjectMoved OnWorkshopObjectPlaced OnWorkshopObjectRepaired</Keywords>
                <Keywords name="Keywords6"></Keywords>
                <Keywords name="Keywords7"></Keywords>
                <Keywords name="Keywords8"></Keywords>
                <Keywords name="Delimiters">00&quot; 01\ 02&quot; 03;/ 04 05/; 06; 07 08((EOL)) 09 10 11 12 13 14 15 16 17 18 19 20 21 22 23</Keywords>
            </KeywordLists>
            <Styles>
                <WordsStyle name="DEFAULT" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="COMMENTS" fgColor="008080" bgColor="FFFFFF" fontStyle="2" nesting="0" />
                <WordsStyle name="LINE COMMENTS" fgColor="008000" bgColor="FFFFFF" fontStyle="2" nesting="0" />
                <WordsStyle name="NUMBERS" fgColor="FF8000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="KEYWORDS1" fgColor="0000FF" bgColor="FFFFFF" fontStyle="1" nesting="0" />
                <WordsStyle name="KEYWORDS2" fgColor="8000FF" bgColor="FFFFFF" fontStyle="1" nesting="0" />
                <WordsStyle name="KEYWORDS3" fgColor="000000" bgColor="FFFFFF" fontStyle="1" nesting="0" />
                <WordsStyle name="KEYWORDS4" fgColor="000000" bgColor="FFFFFF" fontStyle="1" nesting="0" />
                <WordsStyle name="KEYWORDS5" fgColor="800000" bgColor="FFFFFF" fontStyle="1" nesting="0" />
                <WordsStyle name="KEYWORDS6" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="KEYWORDS7" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="KEYWORDS8" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="OPERATORS" fgColor="000000" bgColor="FFFFFF" fontStyle="1" nesting="0" />
                <WordsStyle name="FOLDER IN CODE1" fgColor="0000FF" bgColor="FFFFFF" fontStyle="1" nesting="0" />
                <WordsStyle name="FOLDER IN CODE2" fgColor="0000FF" bgColor="FFFFFF" fontStyle="1" nesting="0" />
                <WordsStyle name="FOLDER IN COMMENT" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="DELIMITERS1" fgColor="808080" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="DELIMITERS2" fgColor="008000" bgColor="FFFFFF" fontStyle="2" nesting="0" />
                <WordsStyle name="DELIMITERS3" fgColor="008000" bgColor="FFFFFF" fontStyle="2" nesting="0" />
                <WordsStyle name="DELIMITERS4" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="DELIMITERS5" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="DELIMITERS6" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="DELIMITERS7" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
                <WordsStyle name="DELIMITERS8" fgColor="000000" bgColor="FFFFFF" fontStyle="0" nesting="0" />
            </Styles>
        </UserLang>
    </NotepadPlus>
    
    ```
    
2.  Open Notepad++
3.  Open the "User Defined Language" window via Language -> Define Your Language...
4.  Select "Import..."
5.  Select the XML file you created earlier.
6.  If the import was successful, you should see a notification saying "Import successful."

Now, when you open up Papyrus source files (with the extension .psc) Notepad++ will automatically highlight them for you.

If you are creating your own script from scratch, you'll need to select the language manually. "Papyrus" should be available near the bottom of the Language menu in Notepad++.

### Darker Syntax Highlighting

If the above is too bright for your eyes then you can try a darker approach which can be found here [User:PROXiCiDE/Notepad++\_Dark.xml](https://ck.uesp.net/wiki/User:PROXiCiDE/Notepad%2B%2B_Dark.xml "User:PROXiCiDE/Notepad++ Dark.xml")

An updated version of the above can be found here [User:SilentSpike/Notepad++\_Dark.xml](https://ck.uesp.net/wiki/User:SilentSpike/Notepad%2B%2B_Dark.xml "User:SilentSpike/Notepad++ Dark.xml")

### More Default Syntax Highlighting

If you prefer syntax highlighting that fits better in the default colors used by Notepad++ you can find an alternative at [User:Schnusch/Notepad++/Syntax Highlighting](https://ck.uesp.net/wiki/User:Schnusch/Notepad%2B%2B/Syntax_Highlighting "User:Schnusch/Notepad++/Syntax Highlighting").

### Fixed Syntax Highlighting for Notepad++ v6.4

This alternative highlighting is compatible with Notepad++ v6.4 and corrects several bugs in the above:

-   hexadecimal literals (i.e. "0x1") are now recognized correctly
-   foldable blocks ("If", "Function", etc.) are now handled correctly, without misidentifying middles of words (i.e. the "if" in "notification")
-   full properties ("Property ... EndProperty") are now also foldable
-   non-documentation block comments (";/ ... /;") are now recognized correctly
-   the escape character in strings ("this \\"is\\" all one string") is now handled correctly
-   highlight colors match those used in code examples on this wiki

```
<NotepadPlus>
    <UserLang name="Papyrus" ext="psc" udlVersion="2.1">
        <Settings>
            <Global caseIgnored="yes" allowFoldOfComments="no" foldCompact="no" forcePureLC="0" decimalSeparator="0" />
            <Prefix Keywords1="no" Keywords2="no" Keywords3="no" Keywords4="no" Keywords5="no" Keywords6="no" Keywords7="no" Keywords8="no" />
        </Settings>
        <KeywordLists>
            <Keywords name="Comments">00 01 02 03 04</Keywords>
            <Keywords name="Numbers, prefix1">0x</Keywords>
            <Keywords name="Numbers, prefix2"></Keywords>
            <Keywords name="Numbers, extras1"></Keywords>
            <Keywords name="Numbers, extras2"></Keywords>
            <Keywords name="Numbers, suffix1"></Keywords>
            <Keywords name="Numbers, suffix2"></Keywords>
            <Keywords name="Numbers, range"></Keywords>
            <Keywords name="Operators1">( ) [ ] , = + - * / % . ! &gt; &lt; | &amp;</Keywords>
            <Keywords name="Operators2">as</Keywords>
            <Keywords name="Folders in code1, open"></Keywords>
            <Keywords name="Folders in code1, middle"></Keywords>
            <Keywords name="Folders in code1, close"></Keywords>
            <Keywords name="Folders in code2, open">Event Function If Property State While</Keywords>
            <Keywords name="Folders in code2, middle">ElseIf Else</Keywords>
            <Keywords name="Folders in code2, close">Auto AutoReadOnly EndEvent EndFunction EndIf EndProperty EndState EndWhile</Keywords>
            <Keywords name="Folders in comment, open"></Keywords>
            <Keywords name="Folders in comment, middle"></Keywords>
            <Keywords name="Folders in comment, close"></Keywords>
            <Keywords name="Keywords1">As Auto AutoReadOnly Conditional Else ElseIf EndEvent EndFunction EndIf EndProperty EndState EndWhile Event Extends False Function Global Hidden If Import Length Native New None Parent Property Return ScriptName Self State True While</Keywords>
            <Keywords name="Keywords2">Bool Float Int String</Keywords>
            <Keywords name="Keywords3">Action Activator ActiveMagicEffect Actor ActorBase Alias Ammo Apparatus Armor AssociationType Book Cell Class ConstructibleObject Container Debug Door EffectShader Enchantment EncounterZone Explosion Faction Flora Form FormList Furniture Game GlobalVariable Hazard Idle ImageSpaceModifier ImpactDataSet Ingredient Key Keyword LeveledActor LeveledItem LeveledSpell Light Location LocationAlias LocationRefType MagicEffect Math Message MiscObject MusicType ObjectReference Outfit Package Perk Potion Projectile Quest Race ReferenceAlias Scene Scroll Shout SoulGem Sound SoundCategory Spell Static TalkingActivator Topic TopicInfo Utility VisualEffect VoiceType Weapon Weather WordOfPower WorldSpace</Keywords>
            <Keywords name="Keywords4">abs acos Activate Add AddAchievement AddDependentAnimatedObjectReference AddForm AddHavokBallAndSocketConstraint AddInventoryEventFilter AddItem AddPerk AddShout AddSpell AddToFaction AddToMap AdvanceSkill AllowBleedoutDialogue AllowPCDialogue Apply ApplyCrossFade ApplyHavokImpulse asin atan AttachAshPile BlockActivation CalculateEncounterLevel CalculateFavorCost CanFastTravelToMarker CanPayCrimeGold CaptureFrameRate Cast Ceiling CenterOnCell CenterOnCellAndWait Clear ClearArrested ClearDestruction ClearExtraArrows ClearForcedMovement ClearKeepOffsetFromActor ClearLookAt ClearPrison ClearTempEffects CloseUserLog CompleteAllObjectives CompleteQuest cos CreateDetectionEvent DamageActorValue DamageAV DamageObject DBSendPlayerPosition DebugChannelNotify DegreesToRadians Delete DeleteWhenAble Disable DisableNoWait DisablePlayerControls Dispel DispelAllSpells DispelSpell DoCombatSpellApply DropObject DumpAliasData Enable EnableAI ENableFastTravel EnableFastTravel EnableNoWait EnablePlayerControls EndFrameRateCapture EquipItem EquipShout EquipSpell EvaluatePackage FadeOutGame FailAllObjectives FastTravel FindClosestActor FindClosestReferenceOfAnyTypeInList FindClosestReferenceOfType FindRandomActor FindRandomReferenceOfAnyTypeInList FindRandomReferenceOfType FindWeather Fire Floor ForceActive ForceActorValue ForceAddRagdollToWorld ForceAV ForceFirstPerson ForceLocationTo ForceMovementDirection ForceMovementDirectionRamp ForceMovementRotationSpeed ForceMovementRotationSpeedRamp ForceMovementSpeed ForceMovementSpeedRamp ForceRefTo ForceRemoveRagdollFromWorld ForceStart ForceTargetAngle ForceTargetDirection ForceTargetSpeed ForceThirdPerson GameTimeToString Get GetActorBase GetActorOwner GetActorReference GetActorValue GetActorValuePercentage GetAlias GetAngleX GetAngleY GetAngleZ GetAnimationVariableBool GetAnimationVariableFloat GetAnimationVariableInt GetAssociatedSkill GetAt GetAV GetAverageFrameRate GetAVPercentage GetBaseActorValue GetBaseAV GetBaseObject GetBribeAmount GetBudgetCount GetBudgetName GetCasterActor GetClass GetClassification GetCombatState GetCombatTarget GetConfigName GetCrimeFaction GetCrimeGold GetCrimeGoldNonViolent GetCrimeGoldViolent GetCurrentBudget GetCurrentDestructionStage GetCurrentGameTime GetCurrentLocation GetCurrentMemory GetCurrentPackage GetCurrentRealTime GetCurrentScene GetCurrentStageID GetCurrentWeather GetCurrentWeatherTransition GetDeadCount GetDialogueTarget GetDistance GetEditorLocation GetEquippedItemType GetEquippedShield GetEquippedShout GetEquippedSpell GetEquippedWeapon GetFactionOwner GetFactionRank GetFactionReaction GetFavorPoints GetFlyingState GetForcedLandingMarker GetForm GetFormID GetGameSettingFloat GetGameSettingInt GetGameSettingString GetGiftFilter GetGoldAmount GetGoldValue GetHeadingAngle GetHeight GetHigestRelationshipRank GetHighestRelationshipRank GetInfamy GetInfamyNonViolent GetInfamyViolent GetItemCount GetItemHealthPercent GetKey GetKeywordData GetKiller GetLength GetLevel GetLeveledActorBase GetLightLevel GetLinkedRef GetLocation GetLockLevel GetLowestRelationshipRank GetMass GetMaxFrameRate GetMinFrameRate GetNoBleedoutRecovery GetNthLinkedRef GetOpenState GetOutgoingWeather GetOwningQuest GetParentCell GetPlatformName GetPlayer GetPlayerControls GetPlayerGrabbedRef GetPlayersLastRiddenHorse GetPositionX GetPositionY GetPositionZ GetRace GetReaction GetRealHoursPassed GetReference GetRefTypeAliveCount GetRefTypeDeadCount GetRegard GetRelationshipRank GetReputation GetScale GetSex GetSitState GetSize GetSkyMode GetSleepState GetStage GetStageDone GetState GetStolenItemValueCrime GetStolenItemValueNoCrime GetTargetActor GetTemplate GetTriggerObjectCount GetValue GetVersionNumber GetVoiceRecoveryTime GetVoiceType GetWidth GetWorldSpace GoToState GtLockLevel HasAssociation HasCommonParent HasEffectKeyword HasFamilyRelationship HasForm HasKeyword HasLOS HasMagicEffect HasMagicEffectWithKeyword HasNode HasParentRelationship HasPerk HasRefType HasSpell HideTitleSequenceMenu IgnoreFriendlyHits IncrementSkill IncrementSkillBy IncrementStat InterruptCast Is3DLoaded IsActionComplete IsActivateChild IsActivateControlsEnabled IsActivationBlocked IsActive IsAlarmed IsAlerted IsAllowedToFly IsArrested IsArrestingTarget IsAttached IsBleedingOut IsBribed IsCamSwitchControlsEnabled IsChild IsCleared IsCommandedActor IsCompleted IsDead IsDetectedBy IsDisabled IsDoingFavor IsEquipped IsEssential IsEuiped IsFactionInCrimeGroup IsFastTravelEnabled IsFightingControlsEnabled IsFlying IsFurnitureInUse IsFurnitureMarkerInUse IsGhost IsGuard IsHostile IsHostileToActor IsIgnoringFriendlyHits IsInCombat IsInDialogueWithPlayer IsInFaction IsInInterior IsInKillMove IsInMenuMode IsInterior IsIntimidated IsInvulnerable IsJournalControlsEnabled IsLoaded IsLockBroken IsLocked IsLookingControlsEnabled IsMapMarkerVisible IsMenuControlsEnabled IsMovementControlsEnabled IsObjectiveCompleted IsObjectiveDisplayed IsObjectiveFailed IsPlayerExpelled IsPlayersLastRiddenHorse IsPlayerTeammate IsPlaying IsProtected IsRunning IsSameLocation IsSneaking IsSneakingControlsEnabled IsSprinting IsStageDone IsStartin IsStarting IsStopped IsStopping IsTrespassing IsUnconscious IsUnique IsWeaponDrawn IsWordUnlocked KeepOffsetFromActor Kill KillSilent KnockAreaEffect LearnAllEffects LearnEffect LearnNextEffect Lock MessageBox ModActorValue ModAV ModCrimeGold ModFactionRank ModFavorPoints ModFavorPointsWithGlobal ModReaction ModRegard MoveTo MoveToInteractionLocation MoveToMyEditorLocation MoveToNode MoveToPackageLocation MoveToWhenUnloaded Mute Notification OpenInventory OpenUserLog OverBudget PathToReference Pause PlaceActorAtMe PlaceAtMe Play PlayAndWait PlayAnimation PlayAnimationAndWait PlayerKnows PlayerMoveToAndWait PlayerPayCrimeGold PlayGamebryoAnimation PlayIdle PlayIdleWithTarget PlayImpactEffect PlaySubGraphAnimation PlaySyncedAnimationAndWaitSS PlaySyncedAnimationSS PlayTerrainEffect PopTo pow PrecacheCharGen PrecacheCharGenClear ProcessTrapHit PushActorAway QueryStat QuitGame QuitToMainMenu RadiansToDegrees RandomFloat RandomInt RegisterForAnimationEvent RegisterForLOS RegisterForSingleLOSGain RegisterForSingleLOSLost RegisterForSingleUpdate RegisterForSingleUpdateGameTime RegisterForSleep RegisterForTrackedStatsEvent RegisterForUpdate RegisterForUpdateGameTime ReleaseOverride RemoteCast Remove RemoveAddedForm RemoveAllInventoryEventFilters RemoveAllItems RemoveCrossFade RemoveDependentAnimatedObjectReference RemoveFromAllFactions RemoveFromFaction RemoveHavokConstraints RemoveInventoryEventFilter RemoveItem RemovePerk RemoveShout RemoveSpell RequestAutoSave RequestModel RequestSave Reset ResetHealthAndLimbs ResetHelpMessage RestoreActorValue RestoreAV Resurrect Revert Say SendAnimationEvent SendAssaultAlarm SendPlayerToJail SendStealAlarm SendStoryEvent SendStoryEventAndWait SendTrespassAlarm SendWereWolfTransformation ServeTime Set SetActive SetActorCause SetActorOwner SetActorValue SetAlert SetAllowFlying SetAlly SetAlpha SetAngle SetAnimationVariableBool SetAnimationVariableFloat SetAnimationVariableInt SetAttackActorOnSight SetAV SetBeastForm SetBribed SetCameraTarget SetCleared SetCrimeFaction SetCrimeGold SetCrimeGoldViolent SetCriticalStage SetCurrentStageID SetDestroyed SetDoingFavor SetEnemy SetEssential SetFactionOwner SetFactionRank SetFogPlanes SetFogPower SetFootIK SetForcedLandingMarker SetFrequency SetGhost SetGodMode SetHeadTracking SetHudCartMode SetInChargen SetINIBool SetINIFloat SetINIInt SetINIString SetInstanceVolume SetIntimidated SetInvulnerable SetKeywordData SetLockLevel SetLookAt SetMotionType SetNoBleedoutRecovery SetNoFavorAllowed SetNotShowOnStealthMeter SetObjectiveCompleted SetObjectiveDisplayed SetObjectiveFailed SetOpen SetOutfit SetPlayerAIDriven SetPlayerControls SetPlayerEnemy SetPlayerExpelled SetPlayerReportCrime SetPlayerResistingArrest SetPlayerTeammate SetPosition SetProtected SetPublic SetRace SetRaction SetReaction SetRelationshipRank SetRestrained SetScale SetSittingRotation SetStage SetUnconscious SetValue SetVehicle SetVoiceRecoveryTime SetVolume ShakeCamera ShakeController Show ShowAsHelpMessage ShowBarterMenu ShowFirstPersonGeometry ShowGiftMenu ShowRaceMenu ShowRefPosition ShowTitleSequenceMenu ShowTrainingMenu sin SplineTranslateTo SplineTranslateToRefNode sqrt Start StartCannibal StartCombat StartFrameRateCapture StartObjectProfiling StartScriptProfiling StartStackProfiling StartTitleSequence StartVampireFeed Stop StopCombat StopCombatAlarm StopInstance StopObjectProfiling StopScriptProfiling StopStackProfiling StopTranslation TakeScreenshot tan TeachWord TetherToHorse ToggleAI ToggleCollisions ToggleMenus Trace TraceConditional TraceStack TraceUser TranslateTo TrapSoul TriggerScreenBlood TryoEnable TryToAddToFaction TryToDisable TryToKill TryToMoveTo TryToRemoveFromFaction TryToReset TryToStopCombat UnequipAll UnEquipItem UnequipItem UnequipShout UnequipSpell UnLockOwnedDoorsInCell UnlockWord UnMute UnPause UnregisterForAnimationEvent UnregisterForLOS UnregisterForSleep UnregisterForTrackedStatsEvent UnregisterForUpdate UnregisterForUpdateGameTime UpdateCurrentInstanceGlobal UsingGamepad Wait WaitForAnimationEvent WaitGameTime WaitMenuMode WillIntimidateSucceed WornHasKeyword</Keywords>
            <Keywords name="Keywords5">OnActivate OnAnimationEvent OnAttachedToCell OnBeginState OnCellAttach OnCellDetach OnCellLoad OnClose OnCombatStateChanged OnContainerChanged OnDeath OnDying OnDestructionStageChanged OnDetachedFromCell OnEffectFinish OnEffectStart OnEndState OnEnterBleedout OnEquipped OnGainLOS OnGetUp OnGrab OnHit OnInit OnItemAdded OnItemRemoved OnLoad OnLocationChange OnLockStateChanged OnLostLOS OnMagicEffectApply OnObjectEquipped OnObjectUnequipped OnOpen OnPackageChange OnPackageEnd OnPackageStart OnRaceSwitchComplete OnRead OnRelease OnReset OnSell OnSleepStart OnSleepStop OnStoryActivateActor OnStoryAddToPlayer OnStoryArrest OnStoryAssaultActor OnStoryBribeNPC OnStoryCastMagic OnStoryChangeLocation OnStoryCraftItem OnStoryCrimeGold OnStoryCure OnStoryDialogue OnStoryDiscoverDeadBody OnStoryEscapeJail OnStoryFlatterNPC OnStoryHello OnStoryIncreaseLevel OnStoryIncreaseSkill OnStoryInfection OnStoryIntimidateNPC OnStoryJail OnStoryKillActor OnStoryNewVoicePower OnStoryPayFine OnStoryPickLock OnStoryPlayerGetsFavor OnStoryRelationshipChange OnStoryRemoveFromPlayer OnStoryScript OnStoryServedTime OnStoryTrespass OnTrackedStatsEvent OnTranslationAlmostComplete OnTranslationComplete OnTranslationFailed OnTrapHit OnTrapHitStart OnTrapHitStop OnTrigger OnTriggerEnter OnTriggerLeave OnUnequipped OnUnload OnUpdate OnUpdateGameTime OnWardHit</Keywords>
            <Keywords name="Keywords6"></Keywords>
            <Keywords name="Keywords7"></Keywords>
            <Keywords name="Keywords8"></Keywords>
            <Keywords name="Delimiters">00;/ 01 02/; 03{ 04 05} 06; 07 08((EOL)) 09&quot; 10\ 11&quot; 12 13 14 15 16 17 18 19 20 21 22 23</Keywords>
        </KeywordLists>
        <Styles>
            <WordsStyle name="DEFAULT" fgColor="000000" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="COMMENTS" fgColor="8E8E8E" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="LINE COMMENTS" fgColor="8E8E8E" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="NUMBERS" fgColor="FF0080" bgColor="FFFFFF" fontName="" fontStyle="1" nesting="0" />
            <WordsStyle name="KEYWORDS1" fgColor="0000FF" bgColor="FFFFFF" fontName="" fontStyle="1" nesting="0" />
            <WordsStyle name="KEYWORDS2" fgColor="008040" bgColor="FFFFFF" fontName="" fontStyle="1" nesting="0" />
            <WordsStyle name="KEYWORDS3" fgColor="008040" bgColor="FFFFFF" fontName="" fontStyle="1" nesting="0" />
            <WordsStyle name="KEYWORDS4" fgColor="6565C6" bgColor="FFFFFF" fontName="" fontStyle="1" nesting="0" />
            <WordsStyle name="KEYWORDS5" fgColor="6565C6" bgColor="FFFFFF" fontName="" fontStyle="1" nesting="0" />
            <WordsStyle name="KEYWORDS6" fgColor="000000" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="KEYWORDS7" fgColor="000000" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="KEYWORDS8" fgColor="000000" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="OPERATORS" fgColor="0080FF" bgColor="FFFFFF" fontName="" fontStyle="1" nesting="0" />
            <WordsStyle name="FOLDER IN CODE1" fgColor="0000FF" bgColor="FFFFFF" fontName="" fontStyle="1" nesting="0" />
            <WordsStyle name="FOLDER IN CODE2" fgColor="0000FF" bgColor="FFFFFF" fontName="" fontStyle="1" nesting="0" />
            <WordsStyle name="FOLDER IN COMMENT" fgColor="8E8E8E" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="DELIMITERS1" fgColor="8E8E8E" bgColor="FFFFFF" fontName="" fontStyle="2" nesting="0" />
            <WordsStyle name="DELIMITERS2" fgColor="8E8E8E" bgColor="FFFFFF" fontName="" fontStyle="2" nesting="0" />
            <WordsStyle name="DELIMITERS3" fgColor="8E8E8E" bgColor="FFFFFF" fontName="" fontStyle="2" nesting="0" />
            <WordsStyle name="DELIMITERS4" fgColor="A82800" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="DELIMITERS5" fgColor="000000" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="DELIMITERS6" fgColor="000000" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="DELIMITERS7" fgColor="000000" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
            <WordsStyle name="DELIMITERS8" fgColor="000000" bgColor="FFFFFF" fontName="" fontStyle="0" nesting="0" />
        </Styles>
    </UserLang>
</NotepadPlus>

```

### Improved Syntax Highlighting

For syntax highlighting that includes some fixes from the above styles, and includes _all_ classes/types found in the native scripts, get it [here](https://ck.uesp.net/wiki/User:Fireboyd78/Papyrus.xml "User:Fireboyd78/Papyrus.xml").

Notable changes:

-   Proper support for multi-line comments
-   Clean color scheme similar to languages like C# and Lua
-   Added all valid types (**Var** being one of the ones that were missing)
-   Added all _native_ Fallout 4 classes/functions/events (from scripts marked as Native & Hidden)

Basically, this is how the syntax highlighting for Papyrus should be (in a non-IDE environment, anyways). This is strictly for vanilla Fallout 4 and does not include any DLC scripts.

### Syntax Highlighting with SKSE 1.7.3 functions

I work on some mods that use SKSE and others that don't so knowing when I'm using an SKSE function is important to me. My [User:Cdcooley/Notepad++ Papyrus Syntax Highlighting](https://ck.uesp.net/wiki/User:Cdcooley/Notepad%2B%2B_Papyrus_Syntax_Highlighting "User:Cdcooley/Notepad++ Papyrus Syntax Highlighting") rules allow me to know which kind of function, event, or script type I'm accessing. The custom color scheme focuses on distinguishing functions with various shades of blue and brown but should be easy enough to change if you prefer something more colorful.

### Papyrus Source code Beautifier

1.  Can be found here [User:PROXiCiDE/SkyIndent.lua](https://ck.uesp.net/wiki/User:PROXiCiDE/SkyIndent.lua "User:PROXiCiDE/SkyIndent.lua")
2.  This script requires LUA to be installed for it to work [http://code.google.com/p/luaforwindows/](http://code.google.com/p/luaforwindows/)

Expand

Installation instructions for **binaries only**.

4.  To get this to work with Notepad++ just press F5 then type
5.  Copy & Paste the following below in the RUN box

```
lua "[install path]\skyindent.lua" -b "$(FULL_CURRENT_PATH)"

```

7.  **\[install path\]** is the directory where you placed the SkyIndent.lua example "C:\\SkyIndent\\"
8.  Select Save
9.  Name it: **SkyIndent**
10.  Select a keyboard shortcut example: **CTRL+F6**

```
Usage skyindent.lua [options] [script.psc]
Available options are:
        -s[number]  Spacing to indent, TAB spacing is default
        -b          Backup the Papyrus Script

```

### Papyrus plugin for Notepad++

There is a plugin available that supports extended highlighting for properties and highlighting of custom script names. It also has a interface to view compile output in a list:[Papyrus++](http://www.nexusmods.com/skyrim/mods/64895/?)

### Papyrus Function List for Notepad++

In Notepad++, the Function List Panel is a zone to display all the functions (or methods) found in the current file. Users can use the Function List Panel to quickly access a function definition by double clicking the function item on the list. You can customize the Function List to recognize Papyrus by adding a new **papyrus.xml** file in the **functionList** folder of the Notepad++ install directory, containing the following content:

```
<?xml version="1.0" encoding="UTF-8" ?>
<NotepadPlus>
<functionList>
<parser displayName="Papyrus"
id="papyrus_function"
commentExpr="(;.*?$)"
>
<function mainExpr="^[\t ]*([\w\[\]]+[\t ]+)?(function|event)[\t ]+\w+[\t ]*\(.*?\)"
  displayMode="$functionName">
                <functionName>
<nameExpr expr="\w+[\t ]*\(.*?\)"/>
                </functionName>
                </function>
</parser>
</functionList>
</NotepadPlus>

```

Then add the following line to the User Defined Languages section of the **overrideMap.xml** file found in the same folder.

```
<association id= "papyrus.xml"userDefinedLangName="Papyrus"/>

```

This code assumes your Papyrus custom-defined language is named "Papyrus" in Notepad++. If you chose a different name, replace the line with

```
<association id= "papyrus.xml"userDefinedLangName="YOUR_LANGUAGE_NAME"/>

```

where YOUR\_LANGUAGE\_NAME is the name of your custom-defined language.