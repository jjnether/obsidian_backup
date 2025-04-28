## Aliases

Aliases are names or tags assigned to actors, objects, and locations used by the quest. This allows various data elements (script, packages, dialogue) to be tagged to the alias rather than to a specific object in the world, allowing quests to specify their aliases at runtime instead of being predefined.

There are two kinds of aliases:

-   Reference Aliases (actors and objects)
-   Location Aliases

Aliases can be made dependent on other aliases, but because the aliases are filled in order, dependencies can only be to aliases higher in the list. For example: Questgiver is Victim's Brother; Treasure is Collector's Owned Item; etc. Aliases may be undefined by the quest (meaning they are defined by the Story Manager when an instance of the quest is created) or can be predefined in the editor.

Note that the aliases are not actually "filled" until the quest starts running - what is defined in the Quest Alias tab is how the alias will be filled when the quest starts.

For a more comprehensive overviews of aliases and how they are filled and used, see [Radiant Story](https://ck.uesp.net/wiki/Category:Radiant_Story "Category:Radiant Story").

## Quest Alias Tab

The Quest Alias Tab contains a list of aliases used by this quest. If the quest has a triggering Event (see [Quest Data Tab](https://ck.uesp.net/wiki/Quest_Data_Tab "Quest Data Tab")), it will be listed at the top of the tab.

The list of aliases is an ordered list - when the quest starts, aliases are filled in order, and the order can matter in the case of aliases which are directly or indirectly (through conditions referring to other aliases) dependent on each other.

[![QuestAliasesWindow.png](https://ck.uesp.net/w/images/thumb/4/41/QuestAliasesWindow.png/900px-QuestAliasesWindow.png)](https://ck.uesp.net/wiki/File:QuestAliasesWindow.png)

## Reference Aliases

A reference alias, which will be assigned to an [Object Reference](https://ck.uesp.net/wiki/Reference "Reference") when the quest starts.

Reference Aliases can be applied to any reference (invalid data like packages and factions are ignored when the alias is assigned to a non-actor reference).

## Reference Alias data:

-   **Alias Name**: used within the quest to refer to this alias. This is never displayed in the game. This also becomes part of the automatically generated [quest stage fragment property name](https://ck.uesp.net/wiki/Quest_Stage_Fragments "Quest Stage Fragments").
-   **Display Name**: (optional) Can be used to rename the reference when it is assigned to the alias. The dropdown is a list of Messages - the Message Title will replace the reference's name. Note that this change is permanent - the reference will retain the new Display Name even when it is removed from the alias.
-   **Force Into Alias When Filled**: (optional) The specified alias will also be filled with whatever fills this alias. This can be useful when you need to fill aliases in a "prioritized" manner (for example, pick NPC\_A if alive, otherwise pick NPC\_B).
    -   Be aware that the last "source" alias that is filled will be the one that determines the final value for the specified "target" alias. The quest does not stop performing the force fill on the first match. In the previous example of picking NPC\_A if alive, otherwise NPC\_B, the alias for NPC\_B should be _first_ in the alias list, followed by the alias for NPC\_A. If the NPC\_B alias appears after the NPC\_A alias and fills unconditionally, while the NPC\_A alias fills conditionally, the value of the target alias will _always_ be NPC\_B. If they are reversed in order, then NPC\_B will fill the target alias, but then NPC\_A will overwrite the target alias' value if its conditions allow it to be filled.
-   **Additional Valid Voice Types for Export**: This is used in cases where the alias's Fill Type (see below) does not give the editor enough information to determine what voice types are valid (for example, Location Alias Reference). Select a form list of voice types which the editor uses to limit any dialogue assigned to this alias (on scenes or through the [GetIsAliasRef](https://ck.uesp.net/wiki/GetIsAliasRef "GetIsAliasRef") condition).

### Checkboxes:\[[edit](https://ck.uesp.net/w/index.php?title=Quest_Alias_Tab&veaction=edit&section=5 "Edit section: Checkboxes:") | [edit source](https://ck.uesp.net/w/index.php?title=Quest_Alias_Tab&action=edit&section=5 "Edit section: Checkboxes:")\]

-   **Reserves Reference**: Once a reference is assigned to a "Reserved" alias by a quest, the game will not fill any other alias with this reference unless:
    -   A) The new alias is marked "Allow Reserved", or
    -   B) The new alias is a "From External" fill type.
    -   C) "Start Game Enabled" quests - all their aliases are treated as if "Allow Reserved" were checked (in order to avoid "race conditions" where the order that the "game start" quests actually fill their aliases matters). However, this may not be true for Start Game Enabled quests that are added to a saved game in progress. See the notes for the "Allow Reserved" checkbox.
-   **Optional**: If checked, the quest is not required to fill this in order to start. If unchecked, the quest will fail to start if it cannot fill this alias.
-   **Essential**: Make the actor in this alias Essential while in the alias.
-   **Protected**: Make the actor in this alias Protected while in the alias.
-   **Quest Object**: Make the reference in this alias a Quest Object while in the alias:
    -   Cannot be dropped or sold by the player. EXCEPTION: Player can place Quest Objects into a container in an alias on the same quest which is ALSO marked as a Quest Object.
    -   Any container containing a Quest Object cannot be cleaned up (deleted) by the game.
-   **Allow Reuse in Quest**: Normally, the game will not fill two aliases on the same quest with the same reference. If "Allow Reuse in Quest" is checked, the reference in this alias CAN be placed into another alias on this quest during the startup process.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>This option must be checked on any alias that can be filled with a reference that has already been used, not on the first alias that uses the reference. This option is not required for all <a href="https://ck.uesp.net/wiki/Quest_Alias_Tab#Fill_type">fill types</a>. For example, a Unique Actor fill can target a reference that's already been used even if this option isn't checked.</td></tr></tbody></table>

-   **Allow Dead**: Allows this alias to be filled with a dead actor. If unchecked, the alias will not fill if there are no living actors that match the fill requirements.
-   **Allow Disabled**: Allows the alias to be filled with a disabled reference. If unchecked, the alias will not fill if there are no enabled references that match the fill requirements.
-   **Allow Reserved**: Allows the alias to be filled with a reference which is already in a Reserved alias on another quest. Checking this will resolve some issues with quests failing to initialize because aliases could not be filled.
    -   This option is greyed out for Start Game Enabled quests, which consider their aliases to "Allow Reserved" by default when initialized at the beginning of a new game. However, ticking "Allow Reserved" may be required to avoid problems if the Start Game Enabled quest is added to a pre-existing save. To select this option on a Start Game Enabled quest:
        -   Highlight the alias's line in the main alias list for the quest, then press CTRL-SHIFT-R to set this flag, OR
        -   Temporarily disable the quest's Start Game Enabled status until you've ticked the box in the alias.
-   **Allow Destroyed**: Allows the alias to be filled with a Destroyed reference. (see [SetDestroyed](https://ck.uesp.net/wiki/SetDestroyed "SetDestroyed"))
-   **Uses Stored Text**: Check this if the alias requires text replacement (for example, a book with text replacement tags, or an alias which uses text replacement in an alternate Display Name).
-   **Stores Text**: Check this if the alias is used in text replacement. (see [Text Replacement](https://ck.uesp.net/wiki/Text_Replacement "Text Replacement"))
-   **Initially Disabled**: If checked, the reference will be automatically disabled when it is assigned to this alias.
-   **Clears Name When Removed**: If checked, any "Display Name" assigned by this alias (see above) will be removed from the reference when it is removed from this alias. If unchecked, the Display Name will be permanently changed.

### Fill Type:

There are 6 ways that an alias can be filled during the process of starting the quest.

Specific Reference

A specific reference is assigned to this alias.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td><p>Note that this will potentially make that reference <b>permanently</b> persistent (always loaded in memory), even when this quest is not running (see <a rel="nofollow" href="https://afkmods.iguanadons.net/index.php?/topic/3676-skyrim-information-baked-into-saves/">[1]</a>). This can eventually cause performance issues, particularly with actors.</p></td></tr></tbody></table>

Unique Actor

Pick a Unique actor to fill the alias. Note that this will only work if the specified actor's reference has been assigned a Persist Location. (see [Object Reference](https://ck.uesp.net/wiki/Object_Reference "Object Reference"))

Location Alias Reference

Pick a Location Alias from this quest (must be higher in the list than this alias), and pick a [Location Ref Type](https://ck.uesp.net/wiki/Location_Ref_Type "Location Ref Type"). When the quest starts, the Story Manager will attempt to find a matching loc ref type from that location to fill this alias.

External Alias Reference

Select another Quest, and then a Reference Alias from that quest. When this quest starts, it will fill this alias with whatever is currently in the selected alias.

-   -   An alias from a Kill Actor Event can fill this reference.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>If the selected quest isn't running, or the selected alias is empty, or if the alias reference is inside a container, this alias will fail to fill.</td></tr></tbody></table>

Create Reference to Object

When the quest starts, a reference will be created using the selected base object. The new reference can either be placed at the same location as another Reference Alias (usually a marker), or in the inventory of another Reference Alias (which must be a container of some kind).

**Note**: A reference that this fill option, must have the Reference that this reference will create and object to be higher in the Alias list.

Find Matching Reference

This option allows the Story Manager to find a reference from anywhere in the world (but only persistent references, or Unique actors, can be found this way outside the loaded area). The "Match Conditions" are used by the Story Manager to filter the potential choices. The optional checkboxes are as follows:

-   **In Loaded Area**: This limits the search to the loaded area (the player's current interior cell, or the 5x5 cells around the player in a worldspace). Useful when you want something near the player. You must set at least one Match Condition if you use this fill type. If you don't, your alias will instead be saved with an unset Specific Reference fill type. This would cause a non-optional alias to prevent the quest from starting at all.
-   **Closest**: Only available when searching "In Loaded Area", this will cause the Story Manager to prefer the closest matching reference. (Otherwise it picks randomly from all matching refs.)
-   **From Event**: This is only available for quests which are started from an Event through the Story Manager (see [Quest Data Tab](https://ck.uesp.net/wiki/Quest_Data_Tab "Quest Data Tab")). Select the event data to run the conditions against.
-   **Near Alias**: Select another Reference Alias on this quest - the Story Manager will run the conditions only on any references linked to that alias's ref. (NOTE: Only linked refs with NO keyword are considered.)

#### Fill Type Conditions

The conditions in the **Match Conditions** list can be applied to any of the fill types (it is always optional), but how the conditions are used depends on the fill type.

These fill types run the [condition](https://ck.uesp.net/wiki/Condition_Functions "Condition Functions") on the thing you are filling the alias with:

-   Specific Reference
-   External Alias Reference
-   Find Matching Reference
    -   If you use GetInCurrentLoc as a condition for Find Matching Reference, for major cities you may need to also restrict the search to exclude the worldspace associated with the city, if you specifically want to fill an alias with a reference in that location, but not have it filled with references from within the city as cities will be tied to the location as well. Example: 4 guards OUTSIDE of solitude you want to fill to an alias while using "GetInCurrentLoc: SolitudeLocation == 1.00". You also add "GetInWorldspace: SolitudeWorld == 0.00" to prevent guards INSIDE the city from filling the aliases.

These fill types run the conditions on THE PLAYER (because there is no loaded reference available to test):

-   Unique actor
-   Location Alias Reference
-   Create Reference

### Alias Data:

-   **Scripts**: Select scripts to run on the alias. These must extend [ReferenceAlias](https://ck.uesp.net/wiki/ReferenceAlias_Script "ReferenceAlias Script") script type in order to work properly.
-   **Factions**: The aliased reference will be considered a member of the specified factions while in the alias.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>The faction will be removed from the base actor when the alias is cleared (including when the quest is stopped) or forced to point at a different reference, even if it appears in the faction list for another reference alias targeting the same actor that is still filled. The behavior is as though <a href="https://ck.uesp.net/wiki/RemoveFromFaction_-_Actor" title="RemoveFromFaction - Actor">RemoveFromFaction</a> is called on the reference as it is leaving the alias.<p><b>Example:</b> 2 quests, named <code>Quest1</code> and <code>Quest2</code>, are both started, and both have aliases that are filled with the same Actor. Both aliases add the Actor to <code>ThievesGuildFaction</code>. <code>Quest1</code> is stopped, but <code>Quest2</code> continues running. <b>The Actor will no longer be in <code>ThievesGuildFaction</code></b>, even though <code>Quest2</code> is still running.</p></td></tr></tbody></table>

-   **Spells**: The specified spells will be added to the reference that fills the alias, and removed when the reference leaves the alias. Note that rightclicking and using the Add menu in this box will allow you to add only Shouts, but if you wish to add other kinds of spell, you can drag them into this box from the Object Window.
-   **Keywords**: The aliased reference will be considered to have the specified keywords while in the alias.
-   **Inventory**: The specified items are added to the reference's inventory when the reference is placed into the alias.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>This is permanent - these items are NOT removed when the reference leaves the alias.</td></tr></tbody></table>

-   **Package Data**: The list of packages is considered an additional "package stack" that sits on top of the aliased actor's base package stack. If an actor is in multiple aliases, the alias packages stack in quest priority order.
-   **Override Package Lists**: Anything specified here replaces the matching "override" package list from the base actor. (See [Interrupt Override Packages](https://ck.uesp.net/wiki/Interrupt_Override_Packages "Interrupt Override Packages").)

## Location Aliases

Location aliases are assigned to [Locations](https://ck.uesp.net/wiki/Location "Location") when the quest starts.

### Location Alias Data

-   **Alias Name**: used within the quest to refer to this alias. This is never displayed in the game.
-   **Force Into Alias When Filled**: (optional) The specified alias will also be filled with whatever fills this alias.

### Checkboxes:

-   **Reserves Location**: Similar to Reference Aliases, once a Location is assigned to a Reserved alias, the Story Manager will not assign it to any other aliases (unless they are marked "Allow Reserved").
-   **Optional**: If checked, this alias can be unfilled and the quest will still start. If unchecked, failure to fill this alias will cause the quest to fail to start.
-   **Displays Text**: Check this if the alias is used in text replacement.
-   **Allow Reuse in Quest**: Normally, the Story Manager will not fill two aliases on the same quest with the same location. If "Allow Reuse in Quest" is checked, the location in this alias CAN be placed into another alias on this quest during the startup process.
-   **Allow Reserved**: Allows locations that are in Reserved aliases on other quests to be picked for this alias.
-   **Allow Cleared**: If unchecked, "Cleared" Locations will never be selected for this alias. If checked, "Cleared" Locations can be checked, but uncleared locations will be preferred if available.

### Fill Type:

There are 4 ways that a location alias can be filled during the process of starting the quest.

Specific Location

A specific [Location](https://ck.uesp.net/wiki/Location "Location") is assigned to this alias.

Reference Alias Location

Select a Reference Alias on this quest (must be higher in the alias list); fill with that reference's current location (optionally use a keyword to select a desired parent location of the current location - no keyword means the current location).

External Alias Location

Select another Quest, and then a Location Alias from that quest. When this quest starts, it will fill this alias with whatever is currently in the selected alias. (If the selected quest isn't running, or the selected alias is empty, this alias will fail to fill.)

Find Matching Location

This option allows the Story Manager to find a Location that matches specified conditions. If "From Event" is unchecked, a matching location is randomly selected from all locations in the game. If "From Event" is checked, the location on the specified event data is checked to see if it passes the conditions - if not, this alias fails to fill.

## Notes

-   A Location Alias will not fill with a location that is cleared, unless the “allow cleared” flag is set (and even then non-cleared locations are preferred)
    -   Note: Forced Location Aliases ignore this.
-   Condition function: [LocationHasRefType](https://ck.uesp.net/wiki/LocationHasRefType "LocationHasRefType") returns false if the ref type is dead or disabled.
-   Due to the reference window's large height it may not fit all resolutions. To activate the OK button (and save your changes) select the first field (Alias Name) and press Shift+TAB twice. Then press enter to confirm and close the window.
    -   This little utility may help [http://www.howtogeek.com/howto/windows-vista/get-the-linux-altwindow-drag-functionality-in-windows/](http://www.howtogeek.com/howto/windows-vista/get-the-linux-altwindow-drag-functionality-in-windows/) it will allow you to move the window with it's top outside the screen (this doesn't work on all machines - try this instead - [http://www.ntwind.com/software/windowspace/download.html](http://www.ntwind.com/software/windowspace/download.html))
-   To add the Player as a Reference, select _Specific Reference_, click _Select Forced Reference_, pick (any) for cell and find the Player reference
-   Shortcut keys to change flags on multiple aliases at the same time:

CTL+SHIFT+R = toggle the Allow Reserved Flag

CTL+SHIFT+D = toggle the Allow Disabled Flag

CTL+SHIFT+O = toggle the Optional Flag