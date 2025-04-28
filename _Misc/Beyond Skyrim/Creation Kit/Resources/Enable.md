Enables the calling object.

-   All objects are Enabled by default, which means they are rendered in the game, and if they are [Actors](https://ck.uesp.net/wiki/Category:Actor "Category:Actor"), will process their AI.
-   Enable can be used to Enable objects marked 'Starts Disabled', or objects that have been disabled through scripts or console commands.
-   Enabled objects are effectively 'turned on':
    -   If the player is in their cell, their 3D loads. Any scripts associated with the [OnLoad Event](https://ck.uesp.net/wiki/OnLoad_-_ObjectReference "OnLoad - ObjectReference") fire.
    -   They regain their collision, begin processing Events and AI, and otherwise operate normally.
-   The Enable call will fail if the object has an [EnableParent](https://ck.uesp.net/w/index.php?title=EnableParent&action=edit&redlink=1 "EnableParent (page does not exist)"). Objects with [EnableParents](https://ck.uesp.net/w/index.php?title=EnableParents&action=edit&redlink=1 "EnableParents (page does not exist)") can never be enabled or disabled through script.
-   When called on an Enable Parent, the \[FadeIn\] property will not be passed to its enable children. They will Enable as through the default Enable (with Fadein=1) was called on them.
    -   In order for the Enable Children to Pop In (instead of fade in), you must go to each child and, under the enable parent tab, check the 'Pop In' checkbox.

## Syntax

```
Enable [FadeIn=1]

```

## See Also

[Disable](https://ck.uesp.net/wiki/Disable "Disable")  
[GetDisabled](https://ck.uesp.net/wiki/GetDisabled "GetDisabled")

## Papyrus Version

[ObjectReference.Enable (Papyrus)](https://ck.uesp.net/wiki/Enable_-_ObjectReference "Enable - ObjectReference")