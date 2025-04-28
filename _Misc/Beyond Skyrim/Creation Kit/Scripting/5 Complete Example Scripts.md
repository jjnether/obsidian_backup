## Complete Example Scripts

### Script Instantiation

Please remember that few example scripts will be complete by themselves, you must attach a script to an object in the Creation Kit before it will run. The exception is for "library" scripts, such as the [Utility Script](https://ck.uesp.net/wiki/Utility_Script "Utility Script"), which contain definitions of global functions for use in other scripts.

### Property Setting

And if the script has any properties, those properties must be set on the object to which the script is attached in the Creation Kit before the script will work correctly.

### Script Name

If you use any of these example scripts, you can change the name to anything else, but if you're creating the file outside of the Creation Kit you must make sure it also matches the name of your file.

## Creating a Simple Toggle

```
ScriptName SimpleToggle Extends ObjectReference

Bool bToggle

Event OnActivate(ObjectReference akActionRef)
bToggle = !bToggle ; Set Bool to whatever it's not
If bToggle ; True
; Do stuff
Else ; False
; Undo stuff
Endif
EndEvent
```

**To make this script work**: Attach this script to an activator such as a button, lever, or container.

## A Quest item you can drop and pick up again and set or reset objectives and Stages.

```
ScriptName DroppableQuestObject Extends ObjectReference

Event OnContainerChanged(ObjectReference NewContainer, ObjectReference OldContainer)
If FromQuest.GetStage() < StageToStopQuestItem ; Are we a quest item at the current stage?
If OldContainer == PlayerREF
FromQuest.SetObjectiveDisplayed(ObjectiveToDisplayOnDrop, True, True)
FromQuest.SetObjectiveDisplayed(ObjectiveToHideOnDrop, False) ; Uncomplete the objective completed on pickup.
If UncompleteEnable
FromQuest.SetObjectiveCompleted(ObjectiveToCompleteOnPickup, False)
EndIf
If StageToSetOnDrop >= 0
FromQuest.SetStage(StageToSetOnDrop)
EndIf
ElseIf NewContainer == PlayerREF
FromQuest.SetObjectiveDisplayed(ObjectiveToDisplayOnPickup, True, True)
FromQuest.SetObjectiveCompleted(ObjectiveToCompleteOnPickup)
If StageToSetOnPickup >= 0
FromQuest.SetStage(StageToSetOnPickup)
EndIf
EndIf
Else ; Nope, we're not a quest item at this stage.
EndIf
EndEvent

Actor Property PlayerREF Auto
Quest Property FromQuest  Auto  ; Set this to the quest the item is a quest item for.
Bool Property UncompleteEnable Auto ; If true, "uncomplete" the objective completed on pickup when dropped.
Int Property StageToStopQuestItem = 99999 Auto ; At this stage or later, it effectively ceases to be a quest item anymore.
Int Property StageToSetOnPickup = -1 Auto ; When item is picked up, set this stage in the quest (Defaults to No Stage)
Int Property ObjectiveToDisplayOnPickup Auto ; What objective should be displayed when item is picked up by the player?
Int Property ObjectiveToCompleteOnPickup Auto ; Usually the "Get this item" objective.
Int Property StageToSetOnDrop = -1 Auto  ; If player drops the item, what stage do we "go back" to?
Int Property ObjectiveToDisplayOnDrop  Auto  ; Re-display the objective to "get" the object.
Int Property ObjectiveToHideOnDrop  = -1 Auto ; Should be the same as ObjectiveToDisplayOnPickup, ideally.
```

To use this script: attach it to the item you want to use, and set the properties accordingly, assigning the quest, Objectives, and Stages involved. For example, let's say that in the quest "StarsAndGarters", the garter belt of Wootazootamootagoota The Tense is set in stage 10 as Objective 10, and Displays Objective 20 "Place the belt on the statue", and sets stage 20 when picked up, and you want to go back to stage 10 if the player drops it. And after stage 30 (Player has put the belt on the statue) it no longer matters what happens to it. You would set your properties as follows:

FromQuest: StarsAndGarters UncompleteEnable: True StageToStopQuestItem: 30 StageToSetOnPickup: 20 StageToSetOnDrop: 10 ObjectiveToDisplayOnPickup: 20 ObjectiveToCompleteOnPickup: 10 ObjectiveToDisplayOnDrop: 10 ObjectiveToHideOnDrop: 20

## A Trigger That Detects When The Player Enters

```
ScriptName ExampleTrigger Extends ObjectReference

Actor Property PlayerREF Auto ; Least 'costly' way to refer to the player

Event OnTriggerEnter(ObjectReference akActionRef)
If akActionRef == PlayerREF ; This condition ensures that only the player will trigger this code
Debug.MessageBox("Yippee!")
EndIf
EndEvent
```

**To Make This Script Work**

Select an existing object in your cell

Click on the Trigger Volume button, the box with a T inside of it.

-   A orange box should appear around the object you selected.

-   Now edit the new orange box you created and add the script above.

-   Then go in-game and walk into the space where this invisible box is.

**Uses:**

-   Create events that depend on player positioning

-   You could eliminate the player if statement above and have other actors like draugr or companions activate things as well

-   Non-player triggers can be used by changing the == to a != in the script above, to do things to other actors like restoring their health or moving them around (but not affecting player if player walks through the trigger)

## Cycle Through a List of Objects and Perform an Action on Each Object(FormLists)

This example script cycles through a List of objects, known as a [Formlist](https://ck.uesp.net/wiki/Formlist "Formlist"), and enables them all if they are disabled, and disables them if they are enabled, each time the player character walks through a chosen trigger volume. If you use a [Formlist](https://ck.uesp.net/wiki/Formlist "Formlist") of special effects, this would cause all the many special effects you have in the formlist to disappear or reappear each time you walk through the trigger volume.

```
ScriptName RamaFormListExampleScript extends ObjectReference

Actor Property PlayerREF Auto ; Least 'expensive' way to refer to the player
FormList Property ListOfObjectsFLST Auto ; see notes after script for more info on this property

Event OnTriggerEnter(ObjectReference akActionRef)
If akActionRef == PlayerREF
Int iIndex = ListOfObjectsFLST.GetSize() ; Indices are offset by 1 relative to size
While iIndex
iIndex -= 1
ObjectReference kReference = ListOfObjectsFLST.GetAt(iIndex) As ObjectReference ; Note that you must typecast the entry from the formlist using 'As'.
If kReference.IsEnabled()
kReference.Disable()
Else ; If kReference.IsDisabled() 
kReference.Enable()
EndIf
EndWhile
EndIf
EndEvent
```

**To Make This Script Work**

-   This script runs on a OnTriggerEnter event, so you must create a trigger volume. See the [script example above](https://ck.uesp.net/wiki/Complete_Example_Scripts#A_Trigger_That_Detects_When_The_Player_Enters "Complete Example Scripts") for details on this.
-   Remember to add this example script to the trigger volume object that you create, so you have an actual instance of this script in your level.
-   You must create a formlist of the objects you want to cycle through in this script example.

[![Formlist populating.png](https://ck.uesp.net/w/images/1/17/Formlist_populating.png)](https://ck.uesp.net/wiki/File:Formlist_populating.png)

1\. Go to the miscellaneous section of the Object Window and click on FormLists, 2. then right click to make a new FormList 3. In your cell view, hold shift and select all of the forms you want to add to the formlist, these could be actors or special effects, activators, or any other kind of form. Name all the forms you want to include from your cell in a similar way so they can be easily selected as a group using shift. 4. Drag the selected forms into the window containing your new formlist information. 5. Make sure to only add forms to your formlist that are all of the same type. Do not mix actors and activators for example.

-   Now you must modify the property of this script example instance, which is present on your trigger volume.

Edit the property so that it points to EditorID of your formlist that you just created.

-   For this script example, I was simply enabling or disabling the objects in the list, so make sure that your formlist contains forms that will react when you enable/disable them. Actors or special effects (look up FX in the \*All section of the Object Window) are good forms to start with.

**Uses:**

-   Any time you have a long list of script properties you want to perform an action on, you can make a formlist instead, and use the while loop to make your coding life Heavenly.
-   Systematically add a certain amount of health or other characteristic to 10 or 2000 actors / creatures to make then stronger or weaker or give them a certain skill (use setAV actor function)
-   Use enable/disable to make a whole bunch of special effect objects (they start with FX in editor) appear or disappear

Enjoy!

## Cycle Through a List of Objects and Perform an Action on Each Object(Linked Ref Chain)

This script will cycle through all the references in a linked ref chain and perform an action on each of them. In this example, the action would be to move each reference up by 16 units when you activate any one of them. Basically, it's the same thing as the FormList version, except you create a linked ref chain instead of a FormList.

```
ScriptName LinkRefChainExample Extends ObjectReference

Actor Property PlayerREF Auto ; Most efficient way to refer to the player

Event OnActivate(ObjectReference akActionRef)
if akActionRef == PlayerREF
PerformActionOn(Self)
ObjectReference TempRef = GetLinkedRef()
while (TempRef && TempRef != Self)
PerformActionOn(TempRef)
TempRef = TempRef.GetLinkedRef()
endwhile
endif
EndEvent

Function PerformActionOn(ObjectReference Target)
Target.MoveTo(Target, 0, 0, 16)
EndFunction
```

**To Make This Script Work**

-   This script runs off an OnActivate event, so you must be able to activate the object this script is attached to.
    -   You can change the OnActivate to whatever you wish to fire off the action.
-   You need to create a linked ref chain.
    -   If you don't know how to create a linked ref to another object, read [this](https://ck.uesp.net/wiki/Bethesda_Tutorial_Encounters#Default_Master_Package_and_Linked-Refs "Bethesda Tutorial Encounters").
    -   A linked ref chain is basically an object that has a linked ref, which has its own linked ref, which also has its own linked ref, etc.
-   Remember to attach this script to the first object in the linked ref chain
    -   If your linked ref chain links back to itself, then you could put this script on each of the objects

## Move an Object to a Specific Location Without Fade

You can use this script to make an activator or actor move without fading out in any way (moveTo and setPosition cause fading to occur). Use this to make objects fly around or make the player move continuously to a destination without fade.

_This example moves the player, for your entertainment._

-   To move something other than player, add a property of type ObjectReference and set it to the actor or activator that you want to move (I have not succeeded in moving statics, only activators and actors)
-   Use different Events freely, this event is used for simplicity and easy demonstration.

```
ScriptName MoveObjExample extends ObjectReference  

Actor Property PlayerREF Auto
ObjectReference Property kDest Auto

Event OnTriggerEnter(ObjectReference akActionRef)
If akActionRef == PlayerREF
akActionRef.TranslateToRef(kDest, 500.0) ; 500 is the speed value, it's pretty fast
EndIf
EndEvent
```

**To Make This Script Work**

-   Make an XMarkerHeading object (search \*All with "xmarker" filter), place it where you want the player to be moved to.
-   Click on an object in your cell and select the Trigger Volume button, the T with a box around it
-   Move the orange box to where you want the player to start their controlled movement to the XMarkerHeading destination.
-   Add this script above to the orange box/trigger volume that you created.
-   SET THE PROPERTY of the script instance, dest, to be your XMarkerHeading that you just made.

This example will not work if you do not set the property as I mention just above, this is an easy thing to forget in this new and wonderful language. Get used to these basics and you will find Papyrus much more powerful than prior scripting languages.

## A Fully Functional Dwemer Button

```
Scriptname DwemerButtonExampleScript extends ObjectReference  

Actor Property PlayerREF Auto
Sound Property QSTAstrolabeButtonPressX Auto

Event OnCellAttach() ; this event runs when cell is loaded containing this scripted object
PlayAnimation("Open")
EndEvent

Event OnActivate(ObjectReference akActionRef)
If akActionRef == PlayerREF
PlayAnimationAndWait("Trigger01", "done") ; sound and animation
        If QSTAstrolabeButtonPressX
     QSTAstrolabeButtonPressX.Play(Self)
        EndIf
        Debug.MessageBox("Joy!") ; actual code for what button should do
EndIf
EndEvent
```

**To Make This Script Work**

-   You must create this script on an Activator object, probably a dwemer button :)
-   You must then set the property for the QST sound effect property, the sound file has the same name as the property in the script above.

**To make your own dwemer button and avoid messing with the original Skyrim scripts/activators:**

-   Find a dwemer button in the object window and change the ID.
-   Create the changed button as a new form when prompted.
-   Edit the new button to remove the original script(s) and attach you own.

## Set Quest Stage When Picked Up By Player

```
ScriptName SetStageOnPlayerPickUp Extends ObjectReference

Actor Property PlayerREF Auto
Quest property QuestToSet Auto
Int Property iStageToSet Auto

Event OnContainerChanged(ObjectReference akNewContainer, ObjectReference akOldContainer)
If akNewContainer == PlayerREF
QuestToSet.SetStage(iStageToSet)
GoToState("Taken")
EndIf
EndEvent

State Taken
; Do nothing
EndState
```

## Usage of Arrays to Make Scripts Compact

In this example you can see how to use a simple script property to reduce the number of scripts you need to write and thus the amount of properties you need to set, which can be time-consuming. Below I was having to do things to about 30 different draugrs:

-   turn their AI on and make them visible
-   turn their AI off and make them invisible

I have different conditions within my level for when each of these two actions should occur. I could divide this into two scripts, but instead I wrote one script and passed a property to the script with each instance of the script to determine which aspect of the script would run.

```
Actor Property PlayerREF Auto
Actor[] Property DraugrArray Auto ; Contains 30 elements filled in CK with the 30 Draugr
Bool Property bEnableBeasts Auto ; Can be set from another script and/or initialized true or false

Event OnTriggerEnter(ObjectReference akActionRef)
If akActionRef == PlayerREF
Int iIndex = DraugrArray.Length ; Will return 30
While iIndex
iIndex -= 1 ; 29'th element is 30'th Draugr
Actor kDraugr = DraugrArray[iIndex]
kDraugr.EnableAI(bEnableBeasts)
kDraugr.SetAlpha(bEnableBeasts As Float)
EndWhile
EndIf
EndEvent
```

Note that bEnableBeasts is a property so one can decide with each instance which way the script should work. One could use a FormList rather than an array or simply set one Draugr as the enable parent of the other 29 and enable/disable him, and thus all the children refs simultaneously.

**How to Make This Script Work**

-   You will need to fill the array elements in the Creation Kit with the chosen creatures.
-   Then you will need to choose for each instance of the script whether the boolean property should be false or true, this setting process shows up a simple checkmark box in the editor.

## A helper script with functions to get the current moonphase, sync between the two moons and day of the week

```
Scriptname ExtendedUtility

Import Utility
Import Math

;/++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+
+GetPassedGameDays() returns the number of fully passed ingame days
+as int.
+
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++/;

Int Function GetPassedGameDays() Global
Float GameDaysPassed

GameDaysPassed = GetCurrentGameTime()
Return GameDaysPassed As Int
EndFunction

;/++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+
+GetPassedGameHours() returns the number of passed ingame hours of
+the current day as int.
+
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++/;

Int Function GetPassedGameHours() Global
Float GameTime
Float GameHoursPassed
 
GameTime = GetCurrentGameTime()
GameHoursPassed = ((GameTime - (GameTime As Int)) * 24)
Return GameHoursPassed As Int
EndFunction

;/++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+
+GetCurrentMoonPhase() returns an integer representing the current
+phase of the moons Masser and Secunda based on "SkyrimClimate".
+Between 12:00 AM and 11:59 AM the phase during the night from last
+day to this day is returned. Between 12:00 PM and 11:59 PM the
+phase for the night from this day to next day is returned. Thus
+a call to the function at night (between 8:00 PM and 6:00 AM) all-
+ways returns the currently visible phase.
+
+The returncodes are as follows:
+0 - Full Moon
+1 - Decreasing Moon 3/4
+2 - Decreasing Moon 1/2
+3 - Decreasing Moon 1/4
+4 - New Moon
+5 - Increasing Moon 1/4
+6 - Increasing Moon 1/2
+7 - Increasing Moon 3/4
+
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++/;

Int Function GetCurrentMoonphase() Global
Int GameDaysPassed
Int GameHoursPassed
Int PhaseTest
GameDaysPassed = GetPassedGameDays()
GameHoursPassed = GetPassedGameHours()

If (GameHoursPassed >= 12.0)
GameDaysPassed += 1
EndIf

PhaseTest = GameDaysPassed % 24 ;A full cycle through the moon phases lasts 24 days
If PhaseTest >= 22 || PhaseTest == 0
Return 7
ElseIf PhaseTest < 4
Return 0
ElseIf PhaseTest < 7
Return 1
ElseIf PhaseTest < 10
Return 2
ElseIF PhaseTest < 13
Return 3
ElseIf PhaseTest < 16
Return 4
ElseIf PhaseTest < 19
Return 5
ElseIf PhaseTest < 22
Return 6
EndIf

EndFunction

;/++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+
+GetCurrentMoonSync() returns an integer that resembles where we are
+in the 5 day cycle of the Snychronisation between the moons.
+
+   Returncodes:
+0 - Moons appear at the same time
+1 - not yet determined how far ahead/behind Secunda is
+2 - not yet determined how far ahead/behind Secunda is
+3 - not yet determined how far ahead/behind Secunda is
+4 - not yet determined how far ahead/behind Secunda is
+
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++/;

Int Function GetCurrentMoonSync() Global
Int GameDaysPassed
Int GameHoursPassed
Int SyncTest

GameDaysPassed = GetPassedGameDays()
GameHoursPassed = GetPassedGameHours()
If (GameHoursPassed >= 12)
GameDaysPassed += 1
EndIf
SyncTest = GameDaysPassed % 5
return SyncTest
EndFunction

;/++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+
+GetDayOfWeek() returns the current ingame day of the week as int.
+
+Returncodes:
+0 - Sundas
+1 - Morndas
+2 - Tirdas
+3 - Middas
+4 - Turdas
+5 - Fredas
+6 - Loredas
+
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++/;

Int Function GetDayOfWeek() Global
Int GameDaysPassed

GameDaysPassed = GetPassedGameDays()
return GameDaysPassed % 7
EndFunction
```

**How to make this script work**

-   Put it to your "Data/Scripts/Source" Folder and compile.
-   Call it's functions in other scripts either by import and call by function name or by using ExtendedUtility.<FunctionName>()

## Script to make an item cast a spell

```
Scriptname SpellZapScript extends ObjectReference  

import Utility
Actor Property PlayerREF Auto
Float Property xOffset Auto ; Relative X position for the target
Float Property yOffset Auto ; Y Offset for Target
Float Property zOffset Auto ; Z offset for Target
Float Property RandomOffsetX Auto ; Randomness applied to X Offset. Initializes at 0.
Float Property RandomOffsetY Auto ;Randomness applied to Y Offset. Initializes at 0.
Float Property RandomOffsetZ Auto ; Randomness applied to Z Offset. Initializes at 0.
Float Property PulseRate = 1.0 Auto ; How often do we shoot?
Float Property RandomRate Auto ; Add random delay to pulse rate, capped at this value
Activator Property TargetType Auto ; What type of object are we zapping if we're spawning a node?
ObjectReference Property CurrentTarget Auto ; The actual target we're shooting at
Bool Property SpawnNode Auto ; Do we spawn a target? If not, zap the nearest valid target. Initializes 'False'
Spell Property Zap Auto ; What spell shall we use for the effect?
FormList Property TargetTypeList Auto ; List of potential targets
Float Property SeekRange = 1000.0 Auto ; The range it will "Lock into" a target if not making a node.

Event OnInit()
    if CurrentTarget ;!= None
    elseIf SpawnNode
        float newXOffset = XOffSet + RandomFloat(-RandomOffsetX, RandomOffsetX)
        float newYOffset = YOffSet + RandomFloat(-RandomOffsetY, RandomOffsetY)
        float newZOffset = ZOffSet + RandomFloat(-RandomOffsetZ, RandomOffsetZ)
        CurrentTarget = PlaceAtme(TargetType)
        CurrentTarget.MoveTo(Self, newXOffSet, newYOffSet, newZOffSet)
    endif
    RegisterForSingleUpdate(PulseRate)
EndEvent

Event OnUpdate()
    ; find something nearby to shoot at if we're not making our own target.
    if !SpawnNode && !TargetTypeList && GetDistance(PlayerREF) < SeekRange ; No list given, Default to the player if he is in range.
CurrentTarget = PlayerREF
    elseif TargetTypeList
        CurrentTarget = Game.FindClosestReferenceOfAnyTypeInListfromRef(TargetTypeList, Self, SeekRange)
    endif
    if CurrentTarget ; it's possible that there is no target 
        Zap.Cast(Self,CurrentTarget)
    endif
    RegisterForSingleUpdate(PulseRate + RandomFloat(0.0, RandomRate))
EndEvent
```

How to make this script work:

-   Put it on the object you want the spells to originate from, and set the properties to define its exact desired behavior.

-   Pick any spell you want for the property Zap (needs to be of the Aimed spell type)

-   If you want it to just shoot at a specific spot, define the Spawn Node Type as an xmarker, set SpawnNode to "True", and enter the relative coordinates you want the spell to be aimed at.

-   If you want it to look for targets nearby, set SpawnNode to false and put a formlist of the valid targets in the TargetTypeList. If no Formlist is given, it will default to trying to shoot the player.

## Script for a quest with time limit

```
Scriptname LH_TimeLimitedQuest extends Quest  

GlobalVariable Property GlobalDays auto ;initial days to complete
GlobalVariable Property GlobalTime auto ;counter for hours left
Quest Property TimedQuest auto ;the quest (I used two scripts on same quest while cause I modified a vanilla one)
int Property FailObjective auto ;objective that will fail when hours left reaches 0, it is the one to display the time left and will be refreshed
int Property FailStage auto ;stage to set the quest to, fail whole quest from it's fragment or whatever

Float endTime

Event OnInit()
if (TGRDays.GetValue() > 0)
;Debug.Notification("Starting countdown")
GlobalTime.SetValue(GlobalDays.GetValue() * 24)
endTime = Utility.GetCurrentGameTime()+GlobalDays.GetValue()
TimedQuest.UpdateCurrentInstanceGlobal(GlobalTime)
RegisterForUpdateGameTime(0.10)
EndIf
EndEvent

Event OnUpdateGameTime()
if (!TimedQuest.IsRunning())
UnregisterForUpdateGameTime()
EndIf
float step = Math.Ceiling((endTime - Utility.GetCurrentGameTime()) * 24) - GlobalTime.GetValue()
if (step != 0)
if (0-step > GlobalTime.GetValue()) ;avoid displaying less then 0
step = 0 - GlobalTime.GetValue()
EndIf
if TimedQuest.ModObjectiveGlobal(step, GlobalTime, FailObjective, 0, false, false)
GlobalTime.SetValue(0.0)
TimedQuest.UpdateCurrentInstanceGlobal(GlobalTime)
TimedQuest.SetStage(FailStage)
UnregisterForUpdateGameTime()
EndIf
EndIf
EndEvent
```

## Making a Cool Cut-Scene

```
ScriptName Cutscene Extends ObjectReference

Actor Property PlayerREF Auto
ObjectReference Property Point1 Auto
ObjectReference Property Point2 Auto
ObjectReference Property Point3 Auto

Event OnTriggerEnter(ObjectReference akActionRef)
If akActionRef == PlayerREF ; Limit this trigger to the player only.
PlayerREF.SetAlpha(0.0)
PlayerREF.SetGhost(True)
Game.DisablePlayerControls(True, True, True, False, True, False, True) ; Disable all controls except looking.
Utility.Wait(0.1) ; Give the script time...
PlayerREF.TranslateToRef(Point1, 100.0)
Utility.Wait(5.0) ; After 5 seconds, proceed to next point.
PlayerREF.TranslateToRef(Point2, 50.0)
Utility.Wait(10.0) ; After 10 seconds, go to next area
PlayerREF.TranslateToRef(Point3, 200.0)
Utility.Wait(20.0) ; Watch the final scene, and then...
PlayerREF.SetAlpha(1.0)
PlayerREF.SetGhost(False)
Game.EnablePlayerControls()
EndIf
EndEvent
```

**How to use this script**: Make a new trigger box, and then add this script to it. Make 3 XMarkers, and define them in the Properties Window. Enter your new trigger, and see your cool cut-scene!

## Script a container that only accepts certain types of items

**How to use this script**: Fill the FormList, AcceptedItemFLST, with only the item(s) you want the container to accept.

```
ScriptName ExampleContainerScript Extends ObjectReference

Actor Property PlayerREF Auto
FormList Property AcceptedItemFLST Auto

Event OnItemAdded(Form akBaseItem, int aiItemCount, ObjectReference akItemReference, ObjectReference akSourceContainer)
If akSourceContainer == PlayerREF
If !AcceptedItemFLST.HasForm(akBaseItem)
RemoveItem(akBaseItem, aiItemCount, True, akSourceContainer)
Debug.Trace("Invalid Item")
EndIf
Endif
EndEvent
```

## Maintenance/update code which runs once per save load and shows a message when a mod is updated or first loaded

-   Requires Skyrim v1.6+: All event based, so no polling is necessary. For this method to work, two scripts are needed as [OnPlayerLoadGame](https://ck.uesp.net/wiki/OnPlayerLoadGame_-_Actor "OnPlayerLoadGame - Actor") will not fire from a Quest script.

```
ScriptName YourQuestScript extends Quest

Float fVersion

Event OnInit()
Maintenance() ; OnPlayerLoadGame will not fire the first time
EndEvent

Function Maintenance()
If fVersion < 1.01 ; <--- Edit this value when updating
fVersion = 1.01 ; and this
Debug.Notification("Now running YourModName version: " + fVersion)
; Update Code
EndIf
; Other maintenance code that only needs to run once per save load
EndFunction
;******************************************************
ScriptName YourPlayerAliasScript extends ReferenceAlias

YourQuestScript Property QuestScript Auto

Event OnPlayerLoadGame()
QuestScript.Maintenance()
EndEvent
```

-   Does not require Skyrim v1.6+: Has to poll, but will work reliably and can be fit in with existing, reiterating code.

```
ScriptName YourQuestScript extends Quest

Float fVersion
Actor Property ActorFromYourMod Auto

Event OnInit()
RegisterForUpdate(10)
EndEvent

Event OnUpdate()
If bGetGameLoaded(ActorFromYourMod, "BrainCondition")
If fVersion < 1.01
fVersion = 1.01
Debug.Notification("Now running YourModName version: " + fVersion)
; Update Code
EndIf
; Maintenance code
Else
; Other, reiterating code if needed
EndIf
EndEvent

Bool Function bGetGameLoaded(Actor akActor, String asActorValue = "")
If akActor.GetActorValue(asActorValue)
akActor.SetActorValue(asActorValue, 0)
Return True ; Will have reverted to 100 upon save load since BrainCondition is obsolete and not stored in saves
Else
Return False
EndIf
EndFunction
```

## Summon Spell

-   The below will summon YourSummonREF from wherever they are to the player. In this example, it's dealt with by a spell, but the function could be placed and/or called elsewhere. If as a spell, be sure to set the cooldown time to about 3.0 seconds so the caster can't cast it again until it's worked itself out.

```
ScriptName RepeatableSummonEffectScript extends ActiveMagicEffect

Actor Property YourSummonREF Auto ; An ObjectReference will also work with the summon function

Event OnEffectStart(Actor akTarget, Actor akCaster)
        Summon(akCaster, YourSummonREF)
EndEvent

; GetFormFromFile below to enable 'Global' flag
Function Summon(ObjectReference akSummoner = None, ObjectReference akSummon = None, Float afDistance = 150.0, Float afZOffset = 0.0, ObjectReference arPortal = None, Int aiStage = 0) Global 
        While aiStage < 6
                aiStage += 1
                If aiStage == 1 ; Shroud summon with portal
                        arPortal = akSummon.PlaceAtMe(Game.GetFormFromFile(0x0007CD55, "Skyrim.ESM")) ; SummonTargetFXActivator disables and deletes itself shortly after stage 5
                ElseIf aiStage == 2 ; Disable Summon
                        akSummon.Disable()
                ElseIf aiStage == 3 ; Move portal in front of summoner
                        arPortal.MoveTo(akSummoner, Math.Sin(akSummoner.GetAngleZ()) * afDistance, Math.Cos(akSummoner.GetAngleZ()) * afDistance, afZOffset)
                ElseIf aiStage == 4 ; Move summon to portal
                        akSummon.MoveTo(arPortal)
                ElseIf aiStage == 5 ; Enable summon as the portal dissipates
                        akSummon.Enable()
                EndIf
                Utility.Wait(0.6)
        EndWhile
EndFunction
```

## Show Gift Inventory and Identify Items Given

This is used for the Player to feed his animal companion. The FormList is created in the CK and includes all the food (Potion & Ingredient) items I want to consider food for the animal.

```
Actor Property PlayerREF Auto
FormList Property FoodList Auto
Bool hasBeenFedToday = False

Function FeedCompanion()
AddInventoryEventFilter(FoodList)
ShowGiftMenu(True, FoodList, False, False)
RemoveAllInventoryEventFilters()
EndFunction

Event OnItemAdded(Form akBaseItem, int aiItemCount, ObjectReference akItemReference, ObjectReference akSourceContainer)
If akSourceContainer == PlayerREF
RemoveItem(akBaseItem,aiItemCount)
If !hasBeenFedToday
hasBeenFedToday = True
EndIf
EndIf
EndEvent
```

## Enable/Disable an object on a schedule

Say you have a pedestal with a magical statue placed on it which is to enable at 6am every morning and disable at 6pm every evening. Glue the below to the pedestal which must always be enabled, filling the properties in the Creation Kit ensuring kYourObject is either renamed to match the EditorID of your statue upon auto-fill or manually pointed to it. If the pedestal is not applicable, use an L\_LOS collision marker.

```
ScriptName YourScript Extends ObjectReference

Actor Property PlayerREF Auto ; <-- Imperative for expedience
Bool Property bEnableStuff Auto ; Leave as default or 'False'
Float Property fHourToDisable Auto ; Desired enable time/18.0 for example's sake
Float Property fHourToEnable Auto ; Desired enable time/6.0 for example's sake
Float Property fUpdateInterval Auto ; 15.0 works well and isn't too frantic.
GlobalVariable Property GameHour Auto ; Pointed to engine maintained, special GlobalVariable
ObjectReference Property kYourObject Auto ; Pointed to your statue or object that is to enable

Event OnInit()
RegisterForSingleLOSGain(PlayerREF, Self)
bEnableStuff = !kYourObject.IsDisabled()
ToggleEnableStateIfApplicable()
EndEvent

Event OnGainLOS(Actor akViewer, ObjectReference akTarget)
RegisterForSingleLOSLost(PlayerREF, Self)
RegisterForSingleUpdate(fUpdateInterval)
ToggleEnableStateIfApplicable()
EndEvent

Event OnLostLOS(Actor akViewer, ObjectReference akTarget)
RegisterForSingleLOSGain(PlayerREF, Self)
UnregisterForUpdate() ; Stop polling
ToggleEnableStateIfApplicable()
EndEvent

Event OnUpdate()
ToggleEnableStateIfApplicable()
RegisterForSingleUpdate(fUpdateInterval)
EndEvent

Function ToggleEnableStateIfApplicable()
Float fTime = GameHour.GetValue()
If bEnableStuff != (fTime > fHourToEnable && fTime < fHourToDisable)
bEnableStuff = !bEnableStuff
If bEnableStuff
kYourObject.Enable()
Else
kYourObject.Disable()
EndIf
EndIf
EndFunction
```

If the statue is only to enable on Thursdays, add a check to the above like so:

```
Function ToggleEnableStateIfApplicable()
Float fTime = GameHour.GetValue()
If bEnableStuff != (fTime > fHourToEnable && fTime < fHourToDisable)
bEnableStuff = GetDayOfWeek() == 5 ; Turdas
If bEnableStuff
kYourObject.Enable()
Else
kYourObject.Disable()
EndIf
EndIf
EndFunction

Int Function GetDayOfWeek() Global ; 0 : Sundas :: 5 : Turdas, etc.
Return ((Game.GetFormFromFile(0x00000039, "Skyrim.ESM") As GlobalVariable).GetValue() As Int) % 7
EndFunction
```

## Enable/Disable Lock on object based on hours of day

Say you have a door or treasure chest you want to have a timed lock on it, here you can. You can also send a Message to the users when it Enables/Disables. Similar to above. You could use it for a template for a variety of things not just a lock Mechanism, however this is a straight-forward basic example. This script section now uses a new Timed Object Reference which no longer performs polling in order to check the times. Instead it make use of the WaitGameTime function which means less overhead and more accurate timing.

**To make this work**: Download and copy the [TimedObjRef2.psc](https://gist.github.com/Langerz82/976c172ce04f074bea91) file to your Skyrim/Data folder. The following is an example of the script in action.

```
ScriptName jlTimedLock2 extends TimedObjRef2

String Property sEnabledMessage Auto ; Optional Message when enabled.
String Property sDisabledMessage Auto ; Optional Message when disabled.


; Override the original function
Function ObjectActive()
if (sEnabledMessage != "")
Debug.MessageBox(sEnabledMessage)
EndIf

; Insert Custom Code.
; Example - Timed Locking.
Self.Lock(TRUE, TRUE)
; End Custom Code.

EndFunction

; Override the original function
Function ObjectInactive()
If (sDisabledMessage != "")
Debug.MessageBox(sDisabledMessage)
EndIf

; Insert Custom Code.
; Example - Timed Unlocking.
Self.Lock(FALSE, TRUE)
; End Custom Code.
EndFunction
```

Don't forget to set the properties once you have attached the script to an Object Reference.

For more examples like this see [Using Activated Object Reference](https://ck.uesp.net/wiki/Using_Activated_Object_Reference "Using Activated Object Reference") for advanced functionality.

## Adding a spell when you shout

The way this works, is when you use a shout, an ability is added. This will work while in combat or outside of it.

```
Scriptname DSerFireBreathMonitorScript extends activemagiceffect  

Spell Property YourAbility Auto

Event OnEffectStart(Actor akTarget, Actor akCaster)
RegisterForAnimationEvent(Game.GetPlayer(), "BeginCastVoice")
Debug.Notification("Waiting on Shout")
 EndEvent

Event OnAnimationEvent(ObjectReference akSource, string asEventName)
 if (akSource == Game.GetPlayer()) && (asEventName == "BeginCastVoice")
Debug.Notification("Fire Breath Shout Cast")
Game.GetPlayer().AddSpell(YourAbility,false)
Utility.Wait(10)
Game.GetPlayer().RemoveSpell(YourAbility)
EndIf
EndEvent
```

## Enabling ReferenceAliases using an array

**Requires basic knowledge in Quest creation.** Say you want to enable currently disabled ReferenceAliases in the quest but you don't feel like a ton of typing and need more than one to be enabled. That's easy to do with an array.

```
Function EnableActorsArray(ReferenceAlias[] myAliasArray, Bool abSpecifyQuest=false, Quest akQuest=none, int aiStage=0) 
; Enable aliases when needed. Make sure "ALLOW DISABLED" box checked, and the REFERENCE's "Initially Disabled" box is checked!
; Can optionally have them enable on a specific quest stage of a quest that is different from the alias' parent quest. Requires that abSpecificQuest is set to the true.


int MyArrayLength = myAliasArray.length

if abSpecifyQuest == false
While (myArraylength)
                myArrayLength -= 1
myAliasArray[myArrayLength].GetReference().Enable()

debug.trace("References that have been enabled:" !myAliasArray[myArrayLength].GetReference().IsDisabled())

EndWhile
else
if (akQuest.GetCurrentStageID() == aiStage)
    While (myArrayLength)
                myArrayLength -= 1
        myAliasArray[myArrayLength].GetReference().Enable()
        
debug.trace("References that have been disabled:" !myAliasArray[myArrayLength].GetReference().IsDisabled())
    EndWhile
endif
endif
EndFunction
```

## Resurrect an Enemy on Death Script

This is a script that will resurrect an enemy for a defined amount of times.

```
Scriptname ResurrectEnemySCRIPT Extends Actor
import game
import utility
import debug

Actor Property PlayerREF Auto
int Property MaxDeathCount auto
Int Property CurrentDeathCount Auto ;DO NOT Change

Event OnDeath(Actor akKiller)
AddToCurrentDeathCount()
If (CurrentDeathCount <= MaxDeathCount) ;If Death count is lower than MaxDeathCount do the next bit of code
wait(2); Wait 2 Seconds real time
Self.PlaceAtMe(GetFormFromFile(0x0007CD55, "Skyrim.ESM"));Place Summon FX at dead NPC
Self.Resurrect() ;Resurrect Dead NPC
EndIf
EndEvent

Function AddToCurrentDeathCount()
    CurrentDeathCount += 1 ;CurrentDeathCount = CurrentDeathCountValue + 1
EndFunction
```

Once you compile the script just attach the script to an enemy actor and set the value of MaxDeathCount to the desired max amount of deaths.