An Actor is a type of object that runs AI routines. Actors move in the world, can engage in combat, and can interact with other objects such as doors, containers, activators (levers, buttons, etc.), and other actors.

## Actor Form

Actors have the following properties:

-   **ID:** The Form ID of the object.
-   **Name:** The display name for the object. If blank, the Actor cannot be activated (spoken to, looted, etc.) by the player in game.
-   **Short Name:** Optionally, a shorter name used in the HUD and for text replacement fields that specify the Short Name. If blank, the full Name is used.

## Flags

| Flag | Function |
| --- | --- |
| Is CharGen Face Preset | If checked, the face created for this actor is available for the player to choose in Character Gen. |
| Essential | Essential actors cannot be killed. When they reach 0 health, they go into a special "bleedout" state and recover over time. |
| Protected | Protected actors are treated as essential to all damage except that delivered by the player. The player is the only one allowed to kill a Protected actor. |
| Respawn | References of this actor in the world will resurrect and reset when their [cell is reset](https://ck.uesp.net/wiki/Cell_Reset "Cell Reset"). |
| Unique | Only one reference of this actor is allowed to exist. Unique actors mainly exist so that the [Story Manager](https://ck.uesp.net/wiki/Story_Manager "Story Manager") can find them even when they are not currently persisting. |
| Summonable | This actor can be associated with a Summon Actor magic effect. |
| Is Ghost | This actor is immune to all damage, and all weapons pass through them without playing hit effects or triggering hit events. |
| Invulnerable | This actor is immune to all damage, although weapons and projectiles appear to hit them normally. |
| Doesn't Bleed | When the actor is struck by a weapon, blood effects are disabled. |
| Simple Actor | Disables face animations and morphing. Also disables the [Story Manager's](https://ck.uesp.net/wiki/Story_Manager "Story Manager") Death and Assault events. |
| Doesn't affect Stealth Meter | When this actor detects the player, the stealth meter does not react. Typically used for non-hostile actors such as foxes, rabbits, deer, etc. |

## Reference Buttons

-   **Add Destruction Data:** The [Destructible Object](https://ck.uesp.net/w/index.php?title=Destructible_Object&action=edit&redlink=1 "Destructible Object (page does not exist)") form associated with the Actor, if any. Almost always disabled.
-   **Dialogue:** Brings up the [Dialogue](https://ck.uesp.net/wiki/Dialogue "Dialogue") window, with this Actor as the filter criteria.

## Scripts

Allows you to Add, Remove, and set the [Properties](https://ck.uesp.net/w/index.php?title=Properties&action=edit&redlink=1 "Properties (page does not exist)") for [Papyrus Scripts](https://ck.uesp.net/wiki/Category:Papyrus "Category:Papyrus") on this actor. Scripts placed on an Actor Form will be used by all instances of the Actor, although their properties can be overridden on each individual reference. See [Scripts](https://ck.uesp.net/wiki/Scripts "Scripts") for a more detailed description of the user interface.

## [Template Data](https://ck.uesp.net/wiki/Template_Data "Template Data")

**ActorBase** allows you to select an Actor or Leveled Actor that this actor will be based on.

Each of the following checkboxes corresponds to a tab on the actor. If checked, the actor inherits (gets) the data for that tab from the actor specified in the ActorBase field. If unchecked, you can manually set the values on that tab instead. See [Template Data](https://ck.uesp.net/wiki/Template_Data "Template Data") for more information.

## Tabs

For a description of the tabs to the right, select from below:

-   [Traits](https://ck.uesp.net/wiki/Traits_Tab_-_NPC "Traits Tab - NPC")
-   [Stats](https://ck.uesp.net/wiki/Stats_Tab_-_NPC "Stats Tab - NPC")
-   [Factions](https://ck.uesp.net/wiki/Factions_Tab "Factions Tab")
-   [Relationships](https://ck.uesp.net/wiki/Relationships_Tab "Relationships Tab")
-   [Keywords](https://ck.uesp.net/w/index.php?title=Keywords_Tab&action=edit&redlink=1 "Keywords Tab (page does not exist)")
-   [AI Data](https://ck.uesp.net/wiki/AI_Data_Tab "AI Data Tab")
-   [AI Packages](https://ck.uesp.net/wiki/AI_Packages_Tab "AI Packages Tab")
-   [Inventory](https://ck.uesp.net/wiki/Inventory_Tab "Inventory Tab")
-   [SpellList](https://ck.uesp.net/w/index.php?title=SpellList_Tab&action=edit&redlink=1 "SpellList Tab (page does not exist)")
-   [Sounds](https://ck.uesp.net/wiki/Sounds_Tab "Sounds Tab")
-   [Animation](https://ck.uesp.net/wiki/Animation_Tab "Animation Tab")
-   [Attack Data](https://ck.uesp.net/wiki/Attack_Data_Tab "Attack Data Tab")
-   [Character Gen Parts](https://ck.uesp.net/wiki/Character_Gen_Parts_Tab "Character Gen Parts Tab")
-   [Character Gen Morphs](https://ck.uesp.net/w/index.php?title=Character_Gen_Morphs_Tab&action=edit&redlink=1 "Character Gen Morphs Tab (page does not exist)")
-   [Face Anim Preview](https://ck.uesp.net/wiki/Face_Anim_Preview_Tab "Face Anim Preview Tab")

## Checkboxes

-   **Preview:** Allows you to view a preview of the Actor in the Preview panel on the right side of the Actor form.
-   **Head:** Allows you to preview changes to the Actor's face morphs.