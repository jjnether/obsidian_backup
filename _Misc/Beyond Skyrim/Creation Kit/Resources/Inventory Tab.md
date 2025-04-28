The [Actor](https://ck.uesp.net/wiki/Actor "Actor") Inventory Tab lists all of the [Items](https://ck.uesp.net/wiki/Items "Items") that the actor is carrying or wearing by default.

Note that additional items can be added in a variety of other ways (through [Script](https://ck.uesp.net/wiki/AddItem_-_ObjectReference "AddItem - ObjectReference"), [Quest Aliases](https://ck.uesp.net/wiki/Quest_Aliases "Quest Aliases"), from the [Traits Tab's Death Item](https://ck.uesp.net/wiki/Traits_Tab "Traits Tab"), etc.), so this list may not be comprehensive.

## Outfits

[Outfits](https://ck.uesp.net/wiki/Outfit "Outfit") are predetermined sets of items, such as a full suit of armor. In most cases, Actors will only wear armor that is in their outfit.

-   **Default Outfit:** This is the Actor's 'standard' outfit (clothes for townspeople, armor for guards, etc.).
-   **Sleep Outfit:** Not used.
-   **Outfit Objects:** A list of the items in the Actor's Default Outfit. This list cannot be changed (change the [Outfit](https://ck.uesp.net/wiki/Outfit "Outfit") instead), but is here for reference.
-   **Geared Up Weapons:** Not used.

## Inventory

-   **Inventory List:** You can add items to the Actor's inventory by dragging them in from the Object Window, or by right-clicking, selecting new, and then choosing the item you want from the Object field.
-   For each object in this list, you can set:
    -   **Object:** The ID of the object.
    -   **Count:** The quantity of the object the Actor has.
    -   **Health%:** Not used.
    -   **Owner/Faction:** The Actor or Faction who owns the item and will consider it stealing if you take it. If left blank, this Actor owns the item by default.
    -   **Global Variable:** Not used.
    -   **Required Rank:** Not used.
-   **Preview Calculated Result:** Given a **Preview Level**, calculates the contents of the Actor's inventory (resolving any leveled items) and shows you the resulting list.