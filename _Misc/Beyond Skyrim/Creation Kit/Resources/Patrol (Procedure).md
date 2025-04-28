## Behavior

**Description:**  
Allows an actor to walk to a starting location, and then walk along a linked ref chain (link from starting point to another point, to another point, etc.).

-   The actor will move within PointRadius distance of the specified PathStart reference (or to the nearest point -see "startAtNearestPoint" param).
-   The actor will travel to each patrol point in succession.
-   The patrol is considered "done" if the actor gets to the last point in the patrol, and the "repeatable" flag is not checked.

**The procedure completes:**  
The patrol is considered "done" if the actor gets to the last point in the patrol, and the "repeatable" flag is not checked.

## Parameters

-   **PathStart** (_[Target](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies where to walk to when starting the patrol. (Usually a reference or linked ref)
-   **PointRadius** (_[Float](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** Specifies how close the actor must get to the starting point as well as each point along the patrol. It is recommended that this radius is greater than zero, as actors have difficulty standing exactly on a point. 32 is an acceptable small radius.
-   **Repeatable** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** If true, the actor will ping pong between the first and last points. This procedure would never be "done". If the flag is not true, then the patrol would go to the last point in the linked ref chain and then would be considered "done" upon arrival.
-   **StartAtNearestPoint** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** If true, the actor would go to the nearest point in the patrol and start from there. If it's not true, then the actor should travel to the beginning of the patrol and start from there.
-   **RideHorseIfPossible** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** If true, actor will ride horse if possible.
-   **StaticPathing** (_[Bool](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Parameter_Types "Category:Package Templates")_)**:** ???

## Notes

-   Patrol points get a special Patrol Data tab in their reference window. This will specify how long an actor will stay at a patrol point.
-   If a patrol point is an Idle Marker, the actor will do that idle animation, facing in the direction the marker is pointing.
-   If a patrol point is an xMarkerHeading, they will face in the direction of the xMarkerHeading when they reach the patrol point.
-   If a patrol point is a piece of furniture, they will currently **not** use the furniture.