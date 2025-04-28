A Keyword represents metadata (a named bit of information) that can be added to most objects (such as [Locations](https://ck.uesp.net/wiki/Location "Location"), [Actors](https://ck.uesp.net/wiki/Category:Actor "Category:Actor"), or Named [LinkRefs](https://ck.uesp.net/w/index.php?title=LinkRefs&action=edit&redlink=1 "LinkRefs (page does not exist)")). Keywords do nothing in and of themselves, but are often used by [Condition Functions](https://ck.uesp.net/wiki/Category:Condition_Functions "Category:Condition Functions") or other game systems.

For example:

-   Banish spells only affect Actors that have the 'ActorTypeDaedra' Keyword.
-   The Enchanting System will prevent the player from disenchanting items with the 'MagicDisallowEnchanting' Keyword.
-   The 'VendorItem' Keywords determine which kinds of merchants will buy the item from the player.

## Keyword Dialog

-   **ID:** The Keyword's Editor ID.
-   **RGB:** Optionally, an RGB color to use for Named LinkRefs that use this Keyword

Optionally, each instance of a Keyword on an object can also be assigned a numeric value. The 'value' of a Keyword can't be set in the Editor, but it can be done through script (see, for example, [SetKeywordData](https://ck.uesp.net/wiki/SetKeywordData_-_Location "SetKeywordData - Location") and [GetKeywordData](https://ck.uesp.net/wiki/GetKeywordData_-_Location "GetKeywordData - Location")).