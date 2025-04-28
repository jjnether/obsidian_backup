## Overview

Conditions are used in a number of places in the editor to tell the game when certain things should happen, and whether certain events or effects should be applied. Conditions are simply a list of one or more logical statements that specify the circumstances under which the associated editor item should be valid or take effect. In the case that a list of conditions evaluates to be false, the effect or event it is attached to will not happen. Conditions can be used in conjunction with the following editor objects:

## The Condition List

The condition list displays all of the individual Condition Items that make up this set of Conditions. Right-clicking in the list displays a popup menu which you can use to create New condition items, Duplicate or Delete existing condition items, Copy one condition, Copy All Conditions, or Paste conditions that have been copied from another condition list.

  
The << and >> buttons below the list window are used to move Condition Items up or down in the list, respectively. The right and left keyboard arrows can also be used for this purpose. The order of conditions may be important when combining AND and OR operators (see below).

  
The 'New' button can be used to create a new item. To edit a Condition Item, double-click its list entry, and a pop-up window will appear allowing you to make changes.

## Condition Items

When making a new condition, or editing an existing condition, the Condition Item pop-up window will appear. This window allows you to configure the details of one particular condition, by altering the following parameters:

### Condition Function

The Condition Function dropdown list contains all possible Condition Functions that can be processed or tested against the object that the condition is attached to. See [Condition Functions](https://ck.uesp.net/wiki/Category:Condition_Functions "Category:Condition Functions") for a complete list of the possible functions and descriptions of how many of them work. The relatively straightforward names of many condition functions may clue you in to their purpose--most commonly, condition functions are used to query the current state, value, or "condition" of a particular object. For instance, IsSneaking or IsSwimming can be used to test--you guessed it--whether an actor is sneaking or swimming at the time the condition is checked.

### Run On

The "Run On" field is used to indicate the actor or object on which the condition function should be "run" or checked. The meaning of these choices (like "Subject" or "Target") can vary somewhat depending on what editor object the condition is attached to. For some types, an additional drop down to the right of the "Run On" field will allow you to specify further data (for example, picking which alias to use when running your condition on a "Quest Alias")

-   **Subject:** The actor owning the object. In the case of dialogue, it's whoever is saying it. In the case of quest targets, it's the player. In the case of Magic Effects and other [Effect Items](https://ck.uesp.net/wiki/Effect_Item "Effect Item"), it is the reference being targeted by the effect.
-   **Target:** For dialogue, this is the actor being spoken to. For Packages, it's the actor/object specified as the target. Magic Effects and Effect Items, it is the reference being targeted by the effect.
-   **Reference:** A specific reference in the world. Use the Select button to find the reference.
-   **Combat Target:** If the owning actor is in combat, it is his current combat target. For Magic Effects and Effect Items, it is the reference being targeted by the effect.
-   **Linked Reference:** If the reference is linked to another reference, the condition function will be run on the linked object.
-   **Quest Alias:** If the condition is being applied to something that is owned by a quest (dialogue in a quest, an alias in a quest, or a package whose "owning quest" is set to a particular quest) then you can select to run a condition on a reference alias belonging to that quest.
-   **Package Data:** you can point to package data that is a reference and run the condition function on that, however, this only works for conditions applied to [packages](https://ck.uesp.net/wiki/Packages "Packages"), [procedures](https://ck.uesp.net/wiki/Procedures "Procedures"), and procedure tree branches.
-   **Event Data:** points to references in particular radiant quest event data (for example Actor1 in an ActorDialogue event), like 'Run on Quest Alias' this only works for things owned by a quest of that type.

### Swap Subject and Target

The "Swap Subject and Target" flag is particularly useful for Magic Effects and Effect Items in the Effect Lists associated with Spells, Enchantments, and Scrolls. Condition functions attached to these types of objects that are Run On the **Subject**, **Target**, or **Combat Target** will all be checked only against the targeted reference. Ticking "Swap Subject and Target" and running the condition on the **Subject** will allow you to instead target _the caster of the effect_ with your condition, assuming that there is a caster.

### Parameters

The Parameters button opens up another dialog box in which parameters that are unique to the currently selected Condition Function can be set. This is where the reference for a GetDistance function or the faction for a GetFactionRank function is set, for example. Not all condition functions make use of additional Parameters.

### Comparison and Value

The "Comparison" dropdown list includes various logical operators that determine how the return value of the Condition Function should be compared against the provided "Value" to determine whether the condition item is true. For Condition Functions that would return a _true_ or _false_ value, setting the "Value" field to 1.00 will check whether the function is _true_ and setting the "Value" to 0.00 will test whether the Condition Function is _false_.

The comparison "Value" is (by default) a text field where a numeric value can be entered by the user. However, if the **Use Global** checkbox below the "Value" field is checked, you will instead be able to choose any [Global Variable](https://ck.uesp.net/wiki/Globals "Globals") from the dropdown list to be compared against the Condition Function's return value.

### Or

By default, all Conditions are set to be run with an **AND** operator between themselves and the condition that follows them. The **OR** checkbox is used to override this behavior, and replace the operator following this condition with an **OR** instead. In the Condition List, consecutive **OR**s are treated like a single block when evaluating and have order precedence over **AND**.

For example, the condition items: _**A**_ AND _**B**_ OR _**C**_ AND _**D**_ are evaluated as ( _**A**_ AND ( _**B**_ OR _**C**_ ) AND _**D**_ ) and _not_ as ( ( _**A**_ AND _**B**_ ) OR ( _**C**_ AND _**D**_ ) ).

## Complex Conditions

By applying the distributive property and taking other logical considerations, complex expressions can be converted into a list of Condition Items that will evaluate as intended.

  
For example, the expression

-   ((_**A**_ AND _**B**_) OR (_**C**_ AND _**D**_))  
    

Can be represented by the logically equivalent list of Condition Items

-   (_**A**_ OR _**C**_ AND _**B**_ OR _**C**_ AND _**A**_ OR _**D**_ AND _**B**_ OR _**D**_).  
    

As described above, operator precedence will result in this being evaluated as

-   ((_**A**_ OR _**C**_) AND (_**B**_ OR _**C**_) AND (_**A**_ OR _**D**_) AND (_**B**_ OR _**D**_))    -    which is equivalent to the initial expression.

To properly check whether ((_**A**_ AND _**B**_) OR (_**C**_ AND _**D**_) OR (_**E**_ AND _**F**_)) is true, one would use:

-   _**A**_ OR _**C**_ OR _**E**_   AND   _**A**_ OR _**C**_ OR _**F**_   AND   _**A**_ OR _**D**_ OR _**E**_   AND   _**A**_ OR _**D**_ OR _**F**_   AND   _**B**_ OR _**C**_ OR _**E**_   AND   _**B**_ OR _**C**_ OR _**F**_   AND   _**B**_ OR _**D**_ OR _**E**_   AND   _**B**_ OR _**D**_ OR _**F**_

  
This looks daunting, but you may be able to reduce this list using further logical refinement. For instance, let us transform the statement above into a more realistic list of conditions we might want to check. Say we have a special regeneration ability, for which we use a GlobalVariable to adjust when the ability kicks in. The GlobalVariable's value determines when an actor's extra health regen ability gets applied. We might be attaching these conditions to the regen spell to tell it when to take effect. So if we have three possible settings for the GlobalVariable, which make the regen kick in when an actor's health is at or below 30%, 60%, or 100% respectively, we essentially want to say...

  
**If:** ((Global == 1) AND (Health <= 30%)) OR ((Global == 2) AND (Health <= 60%)) OR ((Global == 3) AND (Health <= 100%))  
**Then:** The ability should start working!

  
If we properly distribute these conditions using the formula above, the first **OR**\-block that checks for (_**A**_ OR _**C**_ OR _**E**_) will, in our case, be a check for ((Global == 1) OR (Global == 2) OR (Global == 3)). If these are the only three valid settings for our global variable, we know that this block of statements will _always be true_, so we can simply eliminate it from our conditions list to shorten things up. Furthermore, any triplet of ORs above that includes condition F (Health <= 100%) will also always be true, because the actor's health will always be at 100% or less, so we can eliminate several more sets of conditions as a result, leaving us with:

_**A**_ OR _**D**_ OR _**E**_   AND   _**B**_ OR _**C**_ OR _**E**_   AND   _**B**_ OR _**D**_ OR _**E**_

  
Thus, by taking these steps we would have cut our condition list down from 24 conditions to only 9!

**IMPORTANT:** Keep in mind that when attaching conditions to "high-demand" items, like spells and magic effects, using too many conditions can result in a major hit to performance, and should be avoided. Checking whether one AND-pair is true in a set of more than three such pairs (beyond what is shown above) will quickly and exponentially increase the number of conditions that would have to be checked if distributed to account for OR-precedence. Try to find alternative methods if possible--like checking the necessary conditions in a script that can evaluate them more quickly and efficiently.