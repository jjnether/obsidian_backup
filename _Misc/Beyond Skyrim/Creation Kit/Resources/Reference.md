A reference is an instance of an [Base Object](https://ck.uesp.net/wiki/Base_Object "Base Object"). Usually, this means that the object has been placed in the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window"), although references can also be created at runtime by scripts (for example, the [PlaceAtMe()](https://ck.uesp.net/wiki/PlaceAtMe_-_ObjectReference "PlaceAtMe - ObjectReference") function) or by other game systems (for example, many spells create [Explosions](https://ck.uesp.net/wiki/Explosion "Explosion")).

Each base object can have multiple references (the count of references is displayed in the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window")). If any of the properties of a base object are changed in the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window"), all its references are also changed in-game. However, references also hold some data that is unique to the reference. The simplest example is the reference's position: it's unique for each reference, and is not stored with the base object's data in the Object Window.

If you double-click on an object in the Render Window, you will see its reference data. Different types of objects have different reference data on their references. Different references of the same object can be set differently.

All References are treated as [ObjectReference Scripts](https://ck.uesp.net/wiki/ObjectReference_Script "ObjectReference Script"). References can also be cast to their specific subtype, so references of [Actors](https://ck.uesp.net/wiki/Actor "Actor") are _**also**_ [Actor Scripts](https://ck.uesp.net/wiki/Actor_Script "Actor Script").

## Reference Data

## Common Data

-   **Reference Editor ID:** An optional text name that makes it easier to refer to this object in scripts and from other places in the editor. If a name is assigned to this reference, it will appear with this name in the [Cell View Window](https://ck.uesp.net/wiki/Cell_View_Window "Cell View Window").
-   **Base Object:** The base object that this reference points to can be changed by clicking "Edit Base".
-   **Encounter Zone:** The [Encounter Zone](https://ck.uesp.net/wiki/Encounter_Zone "Encounter Zone") is this reference is attached to. If an encounter zone is not explicitly specified, the object will inherit the Encounter Zone of its [Cell](https://ck.uesp.net/wiki/Cell "Cell"), if any. The Encounter Zone is primarily used by [Leveled Lists](https://ck.uesp.net/wiki/Category:Leveled_Lists "Category:Leveled Lists") in determining the strength of their creatures or objects.
-   **Turn Off Fire:** Not used in Skyrim. Functionality may not be supported.
-   **No AI Acquire:** AI will not attempt to pick up containers or objects marked with this flag.
-   **Initially Disabled:** The reference starts [disabled](https://ck.uesp.net/wiki/Disabled "Disabled") ("not there") and must be [enabled](https://ck.uesp.net/wiki/Enabled "Enabled") through script or game events before it will appear.
-   **Hidden From Local Map:**The reference will not be displayed on the local map.
-   **Inaccessible:** Only available for [Doors](https://ck.uesp.net/wiki/Door "Door"). If checked, the door will be inoperable and will show "Inaccessible" when rolled over. This overrides any lock level setting on the door.
-   **Open by Default:** For [Doors](https://ck.uesp.net/wiki/Door "Door") and [Containers](https://ck.uesp.net/wiki/Container "Container"), if checked, the door or object will begin in the open state.
-   **Motion Blur:** Not used in Skyrim. Functionality may not be supported.
-   **High Priority LOD:** (?) Brings reference to the front of the LOD loading hierarchy. Object will fade out last and fade in first.
-   **Starts Dead:** For actors, a corpse is placed instead
-   **Respawns:** If unchecked (when possible) this object will not respawn even if the cell it is in should do so.
-   **Reflected by Auto Water:** Toggles whether the endless water plane in exterior cells reflects the reference. This was not used in Skyrim. Functionality
-   **Ignored by Sandbox:** Check this box to prevent [Sandboxing](https://ck.uesp.net/wiki/Sandbox_Package "Sandbox Package") NPCs from attempting to use this reference. Useful for furniture and idle markers.
-   **Is Full LOD:** Reference will not fade from a distance. Good to apply to very large objects or lighting where fading out would feel obvious and awkward. Warning: Can impact performance if over-used.
-   **Don't Havok Settle:** This object, if havokable, doesn't initially settle itself when the cell is finished loading. Note that if any objects near the object settle, this object will settle regardless of this flag. (For Arrows in targets, etc...)

## Reference Data Tabs

### 3D Data

The X, Y, and Z position and rotation values are displayed and can be directly edited. The scale of the reference relative to the base object can be adjusted as well. Note that objects cannot be scaled up more than 10x, or down by more than 100x.

-   **Test Radius:** Entering a value in this field will cause a radius to be displayed around the reference in the Render Window. This is useful when trying to estimate distances for packages and scripts. Set this field back to 0 to remove the radius.

### Patrol Data

Only available on [Idle Markers](https://ck.uesp.net/wiki/Idle_Markers "Idle Markers") and [Furniture](https://ck.uesp.net/wiki/Furniture "Furniture"). Allows you to specify how long a [patrolling actor](https://ck.uesp.net/wiki/Patrol_(Procedure) "Patrol (Procedure)") stays at this patrol point, and a dialogue topic to say when they arrive.

The **Result Script** field is no longer used.

### Teleport

Available on [Doors](https://ck.uesp.net/wiki/Door "Door"), this field allows you to link one door reference to another door reference anywhere in the world. All teleport links are bidirectional; the other door reference is automatically set to point back to this door. Setting a teleport also creates a yellow teleport marker at each door. This is where [Actors](https://ck.uesp.net/wiki/Category:Actor "Category:Actor") passing through the door will appear.

-   **No Alarm:** This checkbox was added with version 1.6.89 of the Creation Kit. It's purpose is currently unknown.

### Lock

Any References to [Door](https://ck.uesp.net/wiki/Door "Door") or [Container](https://ck.uesp.net/wiki/Container "Container") objects may specify if they are locked, the difficulty of the lock, and optionally any [Keys](https://ck.uesp.net/wiki/Key "Key") required for the lock.

| Lock Level | Skill to Pick Lock |
| --- | --- |
| Novice | 1 |
| Apprentice | 25 |
| Adept | 50 |
| Expert | 75 |
| Master | 100 |
| Requires Key | N/A |

Leveled Locks are not normally used in Skyrim. A leveled lock starts with the specified lock level when the player is level one, and becomes harder as the player's level increases.

### Persist Location

For [Actors](https://ck.uesp.net/wiki/Category:Actor "Category:Actor"), as long as the player is in this [Location](https://ck.uesp.net/wiki/Location "Location"), the object will be [Persistent](https://ck.uesp.net/wiki/Glossary#Persistent "Glossary").

If this is not set, Unique Actor [aliases](https://ck.uesp.net/wiki/Alias "Alias") may not fill correctly. Should be set to the Location where the actor resides.

### Ownership

The [Actor](https://ck.uesp.net/wiki/Category:Actor "Category:Actor") or [Faction](https://ck.uesp.net/wiki/Faction "Faction") that owns the object. If no owner is specified, the object will be owned by the [Actor](https://ck.uesp.net/wiki/Category:Actor "Category:Actor") or [Faction](https://ck.uesp.net/wiki/Faction "Faction") that owns its [Cell](https://ck.uesp.net/wiki/Cell "Cell"), if any.

If the object is owned by a Faction, you can also specify a minimum rank in the Faction needed for someone to own the object, although Skyrim's Factions do not use the rank system.

### Leveled Actor

This tab only appears for references that are [Actors](https://ck.uesp.net/wiki/Category:Actor "Category:Actor") templated (directly or indirectly) to a [LeveledCharacter List](https://ck.uesp.net/wiki/LeveledCharacter "LeveledCharacter"). Note again that LeveledCharacters cannot be placed into the world directly.

This tab allows you to set the relative difficulty of this particular Actor. In conjunction with the [LeveledCharacter List](https://ck.uesp.net/wiki/LeveledCharacter "LeveledCharacter") and the [Cell's](https://ck.uesp.net/wiki/Cell "Cell") [Encounter Zone](https://ck.uesp.net/wiki/Encounter_Zone "Encounter Zone"), this determines the actual level of the creature that will be produced. See [the LeveledCharacter page](https://ck.uesp.net/wiki/LeveledCharacter#Leveled_Character_References "LeveledCharacter") for more details.

### Extra

A collection of miscellaneous values used by a wide variety of object types.

-   **Count:** The number of objects represented by the reference. Like when the player drops multiple items of the same type, only one physical object will be shown in the world.
    -   As a special case, note that if you have an [Arrow](https://ck.uesp.net/wiki/Ammo "Ammo") reference, and specify a count greater than one, a quiver will appear to contain the arrows. The quiver is not an independent object, and this is the only way in which it can be created.
-   **Health:** Not used.
-   **Charge:** For enchanted [Weapons](https://ck.uesp.net/wiki/Weapons "Weapons"), the amount of Charge they begin with. If not specified, the object will begin fully charged.
-   **Time left:** Not used.
-   **Alpha cutoff:** For some objects, a numeric value used to determine how much of the object should be shown or hidden. This value is most often used for banners and carpets, allowing them to appear more or less tattered.
-   **Time left:** Not used.
-   **Soul:** Not used.
-   **Radiation:** Not used.
-   **Radius:** For [Map Markers](https://ck.uesp.net/wiki/Markers "Markers"), the radius around the marker at which the player discovers the location. Represented in the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window") by a yellow circle.
-   **Head-Tracking Weight:** Not used.
-   **Favor Cost:** Not used.
-   **Horse:** For [Actors](https://ck.uesp.net/wiki/Category:Actor "Category:Actor"), allows you to select the Horse this Actor will ride.
-   **Sky Marker:** For [XMarkerHeadings](https://ck.uesp.net/wiki/Markers "Markers"), flags this marker as a point in the air that can be used in a Dragon's flight path.

### Reflected By
Not used.

### Linked Ref

References can be connected to other references through a system of Linked Refs. Linked Refs can be 'named' (assigned an identifying keyword) or 'unnamed' (the default; effectively, they use the NONE keyword). Each Reference can have only one Linked Ref per keyword.

Chains of linked references are commonly used to set up patrols (see [Patrol Package](https://ck.uesp.net/wiki/Patrol_(Procedure) "Patrol (Procedure)")). They can also be useful for scripted purposes (see [GetLinkedRef](https://ck.uesp.net/wiki/GetLinkedRef "GetLinkedRef")).

### Activate Parents
A reference can be set up to have one or more Activate Parents. These are references which will "pass on" an activation event to this reference when they are activated.

-   **Delay:** The number of seconds to wait after the parent's activation before activating this reference.
-   **Parent Activate Only:** If this is checked, this reference can ONLY be activated by an Activate Parent- direct activation (e.g. by the player) will not be possible. Scripts can always activate the object, regardless of this flag.
-   Notes:
    -   Containers appear to be bugged and cannot be activated through any activate parent.
    -   For scripting purposes, this reference will be activated by the reference which acted as the activate parent, not the originally activating NPC.

### Enable Parent

A reference can have an Enable Parent reference, which is set in this tab. When the parent is [Enabled](https://ck.uesp.net/wiki/Enabled "Enabled") or [Disabled](https://ck.uesp.net/wiki/Disabled "Disabled"), so are all of its children. If **Set Enable State to Opposite of Parent** is checked, then the reference will be enabled when the parent is disabled, and vice versa.

This can be useful in instances where you are enabling or disabling a larger number of objects at once: you can simply enable or disable the parent, and simplify your code considerably.

Note that references with an Enable Parent cannot be enabled or disabled independently of their parent, even through script. Their disable/enable state is always determined by their enable parent.

### Emittance

Rarely used, Emittance refers to the color emitted by an object, such as glow effects that need to look a certain color.

If the Emittance is set using the **Interior Light** dropdown, then the color will not change. However, if it it set with the **Exterior Light** dropdown, the Emittance will change in accordance with the daylight of the region chosen. This can be used to turn off/dim light sources at specific times of the day.

### Multibound
By default, objects will be rendered in the [Room Bound](https://ck.uesp.net/wiki/Room_Bounds_and_Portal_Basics "Room Bounds and Portal Basics") that contains their center point. This tab allows you to override this default and specify a Room Bound in which the object should be rendered instead. This is useful for especially large objects (such as water planes) and when portalling complex or organic environments.

### Bound Data

Only room markers have this category. Allows you to have a custom [imagespace](https://ck.uesp.net/wiki/ImageSpace "ImageSpace") or [lighting template](https://ck.uesp.net/wiki/Lighting_Template "Lighting Template") for the area covered by the room marker, independent of the cell's settings.

### Navmesh Import Option

Allows you to accept the [Navmesh Generation](https://ck.uesp.net/wiki/Navmesh_Generation "Navmesh Generation") Import Option from the base object, or to override it for this reference.

### Attach Ref
Allows you to synchronize the motion of this reference to another reference with a specifically created animation. Not used.

### Location Ref Type
Allows you to select a [LocRefType](https://ck.uesp.net/wiki/LocRefType "LocRefType") for this object.

### Scripts

Allows you to add, remove, or set the properties of [ObjectReference Scripts](https://ck.uesp.net/wiki/ObjectReference_Script "ObjectReference Script") on this reference. See [Scripts](https://ck.uesp.net/wiki/Scripts "Scripts") for user interface details.