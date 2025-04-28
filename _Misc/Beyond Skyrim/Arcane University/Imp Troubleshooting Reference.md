This page can be used to troubleshoot any kinds of issues that you encounter during implementation.

Usually there are various different aspects that can cause certain issues, which is why a list of possible solutions to check for are presented.

-   [1 Quest](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Quest)
    -   [1.1 Quest doesn't start](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Quest_doesn.27t_start)
    -   [1.2 Quest Objective shows \[...\] for Text Replacement](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Quest_Objective_shows_.5B....5D_for_Text_Replacement)
-   [2 Dialogue](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Dialogue)
    -   [2.1 Dialogue doesn’t show up](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Dialogue_doesn.E2.80.99t_show_up)
-   [3 Package](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Package)
    -   [3.1 Package doesn’t work](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Package_doesn.E2.80.99t_work)
    -   [3.2 UseWeapon doesn’t work / NPC doesn’t hit](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#UseWeapon_doesn.E2.80.99t_work_.2F_NPC_doesn.E2.80.99t_hit)
-   [4 NPC](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#NPC)
    -   [4.1 Merchant doesn’t sell](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Merchant_doesn.E2.80.99t_sell)
-   [5 Book](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Book)
    -   [5.1 Book shows \[...\] for Text Replacement](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Book_shows_.5B....5D_for_Text_Replacement)
-   [6 Misc](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Misc)
    -   [6.1 Player is always trespassing in interior](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Player_is_always_trespassing_in_interior)

## Quest\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=1 "Edit section: Quest")\]

## Quest doesn't start\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=2 "Edit section: Quest doesn't start")\]

Check the status of your quest with the `sqv` console command, which takes the editor ID of the quest as a parameter. For example, the Bendu Olo tutorial on the Creation Kit wiki names the quest `GSQ01`, so _for that quest_ the command would be `sqv gsq01`. You will need to replace `gsq01` with the editor ID of your quest, if it is different.

**Start Game Enabled quests have unusual behavior with this command.** For most quests, if the output of `sqv` says the quest is running, then it is running. However, Start Game Enabled quests _always_ say they are running, even if they actually aren't.

-   If the quest is Start Game Enabled...
    -   If at least one of the quest aliases is filled, or **all** of the aliases are optional, then the quest is running
    -   If all of the aliases are unfilled (they say `NONE` beside their name), and any of the aliases is required, the quest is **not** running. Proceed below for troubleshooting.
-   If the quest is _not_ Start Game Enabled...
    -   If the output of the `sqv` command says the quest is running, then it is running.
    -   If the output of the `sqv` command says `Stopped`, proceed below for troubleshooting.

-   Check that your aliases fill correctly (using the `sqv` console command to check which aliases are filled & temporarily flagging all aliases as optional in case the quest doesn’t start to confirm which aliases don’t fill exactly)
    -   The alias that doesn’t fill is filled via...
        -   **Specific Reference:** Make sure the reference isn’t disabled, use “Allow Disabled” in this case
        -   **Unique Actor:** Make sure the placed actor ref has a [persistence location](https://ck.uesp.net/wiki/Reference#Persist_Location)
    -   Make sure the aliases are not reserved elsewhere, use the “Allow Reserved” flag in this case
    -   Make sure your alias doesn’t reference aliases in its “Fill Type” that are listed down below your alias in the quest
-   If the quest is a start game enabled, try pressing F5 for quicksave and F9 for quickload and see if it works now. This means the [SEQ](https://wiki.beyondskyrim.org/wiki/Arcane_University:Seq_Guide "Arcane University:Seq Guide") file needs to be updated.
-   If your quest is a story manager event quest:
    -   Make sure your quest is considered to start, there might be other quests in the story manager tree that don’t use “Shares Event” and consume the whole event without giving your quest even the opportunity to start
    -   Enable the SM log via ini tweaks and check if your quest shows up there
    -   Remove the event from the quest and check if it starts via the startgame command

## Quest Objective shows \[...\] for Text Replacement\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=3 "Edit section: Quest Objective shows [...] for Text Replacement")\]

-   If your text is supposed to show an alias
    -   Make sure the alias and the text replacement bit have the same name
    -   Make sure the alias is filled using sqv (If it doesn’t fill, check [here](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#AliasNotFilling))
    -   Make sure the alias uses the “Stores Text” and "Uses Stored Text" flags
-   If your text is supposed to show a Global Variable
    -   Make sure the name of the global matches the reference in the objective
    -   Make sure the global is added to the quest global list on the “Quest Data” tab

## Dialogue\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=4 "Edit section: Dialogue")\]

## Dialogue doesn’t show up\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=5 "Edit section: Dialogue doesn’t show up")\]

-   Check the quest with your dialogue is running (see section Quest doesn’t start [here](https://wiki.beyondskyrim.org/wiki/Arcane_University:Implementation_Troubleshooting_Reference#Quest_doesn.27t_start "Arcane University:Implementation Troubleshooting Reference"), especially the part about start game enabled quests)
-   Ensure the conditions on your starting topic are valid (Temporarily remove all conditions but the speaker condition to be sure)
-   Does the actor show up as speaker in any one of the responses (see bottom area of the dialog line window - the same where you assign emotions)? If not, the conditions are not valid.
-   Does the actor who should speak have a voice type assigned?
-   Is other dialogue playing instead? Maybe the other dialogue is blocking your dialogue due to higher dialogue and/or quest priority

## Package\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=6 "Edit section: Package")\]

## Package doesn’t work\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=7 "Edit section: Package doesn’t work")\]

-   Make sure the package is actually running (Use [More Informative Console](https://www.nexusmods.com/skyrimspecialedition/mods/19250) to check)
-   Make sure navmesh is available where the package is running, you can use the navmesh test tool for that
-   If the package is attached to a quest alias, makes sure the quest is running
-   If the quest has an “owning quest” set - make sure you only use it in scenes or on quest aliases in that quest.
-   Make sure the NPC is persistent where it should run the package (via quest alias or persistence location)

## UseWeapon doesn’t work / NPC doesn’t hit\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=8 "Edit section: UseWeapon doesn’t work / NPC doesn’t hit")\]

-   Check if the NPC has an attack race set. It should usually be equivalent to the race of the NPC itself. You may want to check in xEdit to be sure.

## NPC\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=9 "Edit section: NPC")\]

## Merchant doesn’t sell\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=10 "Edit section: Merchant doesn’t sell")\]

-   Ensure they are in the main JobMerchantFaction and in a specialized Job faction
-   Do they have a Services faction that has the vendor feature enabled?
    -   Is it currently inside the start and end hours? Is the start hour smaller than the end hour?
    -   Are they in the location and radius of their vendor location?
-   Do they have a default voice type assigned?

## Book\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=11 "Edit section: Book")\]

## Book shows \[...\] for Text Replacement\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=12 "Edit section: Book shows [...] for Text Replacement")\]

-   If your text is supposed to show an alias
    -   Make sure you’ve at least once filled this book to an alias with the flags “Stores Text” and "Uses Stored Text". You can do this either by:
        -   Creating the book object in the alias
        -   [Force](https://ck.uesp.net/wiki/ForceRefTo_-_ReferenceAlias) the book reference to an alias

## Misc\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=13 "Edit section: Misc")\]

## Player is always trespassing in interior\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:Implementation_Troubleshooting_Reference&action=edit&section=14 "Edit section: Player is always trespassing in interior")\]

-   Make sure the package they use has an unlock door procedure and the variable “Unlock on arrival” is set to true (usually that's part of a sandbox package)
-   Make sure the cell has a lock list and owner faction and is not set to “Off Limits”
-   Make sure the cell door is locked