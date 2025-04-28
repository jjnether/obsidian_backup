## Behavior

**Description:**  
The **Sandbox** Procedure makes the actor look "active" by interacting with various things in his environment. It takes various parameters defining what activities it is allowed to perform while "sandboxing."

1.  **Procedures:** The actor moves around within a specified location and interacts with furniture, idle markers, and other NPCs, looking purposeful and intelligent (or, at least, active and engaged with its environment).
2.  **Activities:** If allowed to eat, it eats breakfast, lunch and dinner at times selected randomly from within an appropriate range of hours (specified by gamesettings). Likewise for sleeping, if allowed to sleep.

**The procedure completes:**  
Never completes.

## Parameters

-   **Location** (_[Location](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies the area that the actor will Sandbox within
-   **AllowEating** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies whether the actor is allowed to eat while Sandboxing
-   **AllowSleeping** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies whether the actor is allowed to sleep (in beds) while Sandboxing. (Occurs most often "at night")
-   **AllowConversation** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies if the actor should decide to talk to other actors while Sandboxing (see: [Random Conversations](https://ck.uesp.net/wiki/Category:Scenes#Controlling_Random_Conversations "Category:Scenes"))
-   **AllowIdleMarkers** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies whether the actor is allowed to use [Idle Markers](https://ck.uesp.net/wiki/Idle_Markers "Idle Markers") while Sandboxing.
-   **AllowFurniture** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies whether the actor is allowed to use furniture while Sandboxing.
-   **AllowSitting** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies whether the actor is allowed to use chairs (and other furniture whose markers are of type "Sit" or "Lean", but not "Sleep", and not furniture with the "Special" keyword) while Sandboxing.
-   **AllowWandering** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies whether the actor is allowed to aimlessly wander while Sandboxing. (Usually False)
-   **WanderPreferrefPath** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** If true, the actor will stay exclusively on preferred-path navmesh triangles when wandering.
-   **Energy** (_[Float](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Used in the formulas for how much time to spend on each type of sub-procedure. See "Procedure Duration Formulas" below.
-   **AllowSpecialFurniture** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies whether the actor is allowed to use furniture with the "Special" keyword (for instance: grindstones, forges, alchemy tables, arcane enchanters etc.) while Sandboxing.
-   **MinWanderDistance** (_[Float](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** The minimum distance away from his current position the actor will decide to wander to when picking a point on the navmesh within the sandbox distance when AllowWandering is true.

## Notes

-   If you are creating a new package, and you want it to include a Sandbox procedure that will end after a specified amount of time, put the Sandbox in a Simultaneous node along with a Wait procedure. (A Simultaneous node completes when any of its children complete, so it will end when the Wait runs out of time.)
-   **They don't eat real food:** When the Sandbox runs an Eat procedure, it never consumes real food items from the actor's inventory.
-   **Other NPCs can still talk to them:** Setting AllowConversations to false will not stop other NPCs from starting conversations with the sandboxing NPC. It only prevents the sandboxing NPC from choosing to start conversations with others.
-   **They stay in their sandbox location:** If a sandboxing actor chooses to talk with an NPC who then moves outside the Location, it will give up pursuit once the target leaves the Location.
-   **They check ownership:** A sandboxing actor will only use idle markers and furniture if they are not owned, or if they are owned by the NPC or its faction.
-   **They reserve their targets, and respect reservations:** Sandboxing actors place a reservation on the target ref with which they want to interact. No other sandboxing actor will attempt to use those refs.
-   **You can chain sandbox markers via LinkedRefs but this is kludgy:** If the Location is a ref with Patrol data and a linked ref, the actor will remain in that location for the duration specified by the Patrol data, and then move along to the LinkedRef, to continue sandboxing there. So, sandboxes can be chained, like they could in Fallout. _However_: it is now very easy to build (or to ask an expert to build) a specialized package that is a sequence of sandbox procedures, so this is only questionably relevant anymore.

## Action Selection

When a sandbox package starts up, it builds a list of nearby objects with which it could interact. To select an action, it computes a score for each object, based on the specifics of that object. That score will be set to zero if that object becomes an invalid target, or if it was the same object that the sandbox just selected previously. Each object's score is then weighted by a relative "probability" value based on the _type_ of the interaction (i.e. sleep, eat, use furniture, use idle markers, or dialogue). The sandbox maintains these probability values over time, adjusting them each time it choses a target object. It drops the probability to zero for the type that was just chosen, and increases the probability for the other types. This ensures that the actor will not select the same kind of action repeatedly (unless it has no other options). For example, after eating, the probability of eating again immediately will be zero, but will increase over time as the actor performs actions other than eating.

## Idle Markers

Much of the behavior of an NPC using the sandbox package results directly from data attached to objects in the world (idle markers, with collections of potential animation), or simply from the presence of objects in the word (furniture, food, other NPCs), with no extra data required.

See [Idle Markers](https://ck.uesp.net/wiki/Idle_Markers "Idle Markers") for more information about what can be specified on a marker.

## Sleeping

Sleep time and duration is calculated when the sandbox package starts, and then recalculated once per day as necessary.

Sleeping is based on the following gamesettings:

[iSandboxSleepStartMin](https://ck.uesp.net/wiki/ISandboxSleepStartMin "ISandboxSleepStartMin")

Min time to start sleeping. (Default = 19)

[iSandboxSleepStartMax](https://ck.uesp.net/wiki/ISandboxSleepStartMax "ISandboxSleepStartMax")

Max time to start sleeping. (Default = 1)

[iSandboxSleepDurationMin](https://ck.uesp.net/wiki/ISandboxSleepDurationMin "ISandboxSleepDurationMin")

Minimum duration for sleeping. (Default = 6)

[iSandboxSleepDurationMax](https://ck.uesp.net/wiki/ISandboxSleepDurationMax "ISandboxSleepDurationMax")

Maximum duration for sleeping. (Default = 10)

### Start Time

Rolls randomly for sleep start time between iSandboxSleepStartMin and iSandboxSleepStartMax.

So sandboxing actors can start sleeping between 19:00 and 1:00, using these gamesettings.

### Duration

Rolls randomly for sleep duration using iSandboxSleepDurationMin and iSandboxSleepDurationMax.

## Eating Meals

Sandboxing actors calculate their mealtimes when the sandbox package starts, and then recalculate them once per day as necessary.

The meal times are based on the following gamesettings:

[iSandboxBreakfastMin](https://ck.uesp.net/wiki/ISandboxBreakfastMin "ISandboxBreakfastMin")

Min time to start eating breakfast. (Default = 6)

[iSandboxBreakfastMax](https://ck.uesp.net/wiki/ISandboxBreakfastMax "ISandboxBreakfastMax")

Max time to start eating breakfast. (Default = 9)

[iSandboxLunchMin](https://ck.uesp.net/wiki/ISandboxLunchMin "ISandboxLunchMin")

Min time to start eating lunch. (Default = 11)

[iSandboxLunchMax](https://ck.uesp.net/wiki/ISandboxLunchMax "ISandboxLunchMax")

Max time to start eating lunch. (Default = 14)

[iSandboxDinnerMin](https://ck.uesp.net/wiki/ISandboxDinnerMin "ISandboxDinnerMin")

Min time to start eating dinner. (Default = 17)

[iSandboxDinnerMax](https://ck.uesp.net/wiki/ISandboxDinnerMax "ISandboxDinnerMax")

Max time to start eating dinner. (Default = 20)

[iSandboxMealDurationMin](https://ck.uesp.net/wiki/ISandboxMealDurationMin "ISandboxMealDurationMin")

Min duration for eating a meal. (Default = 0)

[iSandboxMealDurationMax](https://ck.uesp.net/wiki/ISandboxMealDurationMax "ISandboxMealDurationMax")

Max duration for eating a meal. (Default = 2)

## Other Behaviors

When not sleeping or eating a meal, the actor can engage in other activities -- if allowed by the package and available within the package radius.

## Procedure Duration Formulas

Let's work through the duration formulas, using Furniture as an example. Variable names in _italics_ are the names of gamesettings.

-   We start by computing a baseline duration value for using furniture:

```
BaseDuration = fSandboxDurationBase * fSandboxDurationMultFurniture

```

-   We then use the procedure's Energy parameter to modify that baseline:

```
EnergyDuration = BaseDuration * ( 1.0 + Energy * fSandboxEnergyMult * fSandboxEnergyMultFurniture )

```

-   Finally, we pick a random duration in a range around the baseline.

```
MinimumDuration = EnergyDuration * (1.0f - fSandboxDurationRangeMult);
MaximumDuration = EnergyDuration * (1.0f + fSandboxDurationRangeMult);
Duration = random value between MinimumDuration and MaximumDuration

```

## Semi-Scheduled Activities: Meals and Sleeping

(All units are in hours.)

-   **Sleeping:** Sandbox actors who are allowed to sleep will sleep automatically, based on gamesettings.

```
Bedtime:fSandboxSleepStartMin,  fSandboxSleepStartMax
Sleeping duration:fSandboxSleepDurationMin,fSandboxSleepDurationMax

```

-   **Eating:** Sandbox actors who are allowed to eat will have regular mealtimes three times per day All units are in hours.

```
Breakfast:fSandboxBreakfastMin,fSandboxBreakfastMax
Lunch:fSandboxLunchMin,fSandboxLunchMax
Dinner:fSandboxDinnerMin,fSandboxDinnerMax
Meal durations: fSandboxMealDurationMin, fSandboxMealDurationMax

```

## Relevant Gamesettings

-   **fMinSandboxRescanSeconds**: Min time (in seconds) before the sandbox re-scans the world for new stuff to interact with.
-   **fMaxSandboxRescanSeconds**: Max time (in seconds) before the sandbox re-scans the world for new stuff to interact with.
-   **fSandboxCylinderTop**: Truncate a spherical sandbox location to a cylinder at this height above the center point. Should be a positive number.
-   **fSandboxCylinderBottom**: Truncate a spherical sandbox location to a cylinder at this height below the center point. Should be a negative number.
-   **fAIWanderDefaultMinDist**: The default minimum wander distance; used if the procedure doesn't specify one.
-   **fSandBoxRadiusHysteresis**: Extra padding so we don't need to repath back into the sandbox when on the edge of it.
-   **fSandBoxDelayEvalSeconds**: Don't re-evaluate our package/procedure for atat // least this long after starting a new sandbox action.
-   **fSandBoxInterMarkerMinDist**: Don't go from one idle marker to another that's closer than this.