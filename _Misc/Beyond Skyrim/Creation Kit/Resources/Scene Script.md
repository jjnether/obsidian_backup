Script for the manipulation of scenes.

## Definition

```
ScriptName Scene extends Form
```

## Properties

None

## Global Functions

None

## Member Functions

**[ForceStart](https://ck.uesp.net/wiki/ForceStart_-_Scene "ForceStart - Scene")()**

-   Forces the scene to start playing and kills any other scenes running on actors this scene needs.

**Quest [GetOwningQuest](https://ck.uesp.net/wiki/GetOwningQuest_-_Scene "GetOwningQuest - Scene")()**

-   Returns the [Quest](https://ck.uesp.net/wiki/Quest_Script "Quest Script") that owns this scene.

**Bool [IsActionComplete](https://ck.uesp.net/wiki/IsActionComplete_-_Scene "IsActionComplete - Scene")(Int _aiActionID_)**

-   Returns whether the specified action is complete or not.

**Bool [IsPlaying](https://ck.uesp.net/wiki/IsPlaying_-_Scene "IsPlaying - Scene")()**

-   Returns whether the scene is currently playing or not.

**[Start](https://ck.uesp.net/wiki/Start_-_Scene "Start - Scene")()** ^6626b5

-   Starts the scene.

**[Stop](https://ck.uesp.net/wiki/Stop_-_Scene "Stop - Scene")()**

-   Stops the scene.

## Events

None

## Related Fragments

-   [Scene Fragments](https://ck.uesp.net/wiki/Scene_Fragments "Scene Fragments")
-   [Scene Phase Fragments](https://ck.uesp.net/wiki/Scene_Phase_Fragments "Scene Phase Fragments")
-   [Scene Timer Action Fragments](https://ck.uesp.net/wiki/Scene_Timer_Action_Fragments "Scene Timer Action Fragments")