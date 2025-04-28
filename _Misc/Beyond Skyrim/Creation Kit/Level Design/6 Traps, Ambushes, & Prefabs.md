| Bethesda Tutorial Traps and Prefabs |
| --- |
| Level Design Series, Chapter 6 |
| [Return to Tutorial Hub](https://ck.uesp.net/wiki/Category:Tutorials "Category:Tutorials") |
| [![LeftArrow.png](https://ck.uesp.net/w/images/9/97/LeftArrow.png)](https://ck.uesp.net/wiki/Bethesda_Tutorial_Encounters "Bethesda Tutorial Encounters") [Previous Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Encounters "Bethesda Tutorial Encounters") | [Next Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Optimization "Bethesda Tutorial Optimization")[![RightArrow.png](https://ck.uesp.net/w/images/c/cc/RightArrow.png)](https://ck.uesp.net/wiki/Bethesda_Tutorial_Optimization "Bethesda Tutorial Optimization") |
| **Example Plugins:** |
| [Initial](https://ck.uesp.net/w/index.php?title=Special:Upload&wpDestFile=LDEncountersTutorialComplete.esp "LDEncountersTutorialComplete.esp") | [Completed](https://ck.uesp.net/w/index.php?title=Special:Upload&wpDestFile=LDAmbushesTrapsTutorialComplete.esp "LDAmbushesTrapsTutorialComplete.esp") |
| [Companion Video Tutorial](http://youtu.be/PN5vCtlxvwk?hd=1) |

## Overview\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=1 "Edit section: Overview") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=1 "Edit section: Overview")\]

This chapter covers the basics of working with AI ambushes and traps.

The reader will learn the following skills:

-   Activate Parenting
-   Using Ambush set-up prefabs
-   Basics of Trap prefab Placement
-   Use of other prefabs

## Linked References\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=2 "Edit section: Linked References") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=2 "Edit section: Linked References")\]

The [previous tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Encounters "Bethesda Tutorial Encounters") discussed [linked references, or **linkedRefs**](https://ck.uesp.net/wiki/Glossary#LinkedRef "Glossary"). In that example, linkedRef relationships were used to create NPC patrol paths. This behavior is the result of logic that has already been set up with an AI [package](https://ck.uesp.net/wiki/Category:Packages "Category:Packages"). This is just one example of how linkedRef and other object-to-object relationships can be used to drive complex interaction in the Creation Kit.

## Basic Activation Parenting\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=3 "Edit section: Basic Activation Parenting") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=3 "Edit section: Basic Activation Parenting")\]

When the player "uses" an object, they are **[activating](https://ck.uesp.net/wiki/Glossary#Activation "Glossary")** it. Activation is an important concept when dealing with interaction. Three things happen whenever an object is activated.

-   **Native Behavior** Most objects have some default behavior when activated. [Doors](https://ck.uesp.net/wiki/Door "Door") will open/close, [a container](https://ck.uesp.net/wiki/Container "Container") will display its contents, [an NPC](https://ck.uesp.net/wiki/Actor "Actor") will enter conversation or be pickpocketed, and so on. These behaviors are automatic unless deliberately [blocked by script](https://ck.uesp.net/wiki/BlockActivation_-_ObjectReference "BlockActivation - ObjectReference").
-   **Script Event** Activation also sends a notification to [Papyrus](https://ck.uesp.net/wiki/Category:Scripting "Category:Scripting"), allowing us to react to the activation in novel ways. While this tutorial won't cover [scripting](https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Hello_World "Bethesda Tutorial Papyrus Hello World"), we will be taking advantage of pre-existing scripts that rely upon these Activation Events.
-   **Activate Parent** We are able to specify one or more **"Activate Parents"** of a reference. This simply means that when the Parent object is activated, any "children" will also receive an Activation.

[![](https://ck.uesp.net/w/images/thumb/1/1f/ActivateParent01.jpg/350px-ActivateParent01.jpg)](https://ck.uesp.net/wiki/File:ActivateParent01.jpg)

**Fig. 6.1**: Note the placement of the pull chain - try to keep such objects visually obvious. Searching for a lever in a dark corner is no fun.

Let's take advantage of an **activate parent** relationship now. The Portcullis in _Fig 6.1_ uses an Activate Parent link, as indicated by the blue and white line. The white end is the activate parent while the blue end is the child. Try emulating this setup in your own level:

1.  Load **LokirsTomb01** from the [example plugin](https://ck.uesp.net/w/index.php?title=Special:Upload&wpDestFile=LDEncountersTutorialComplete.esp "LDEncountersTutorialComplete.esp") or your own.
2.  Replace **NorDoorMedium01** with a **norPortcullisLarge01**.
3.  Make sure the new portcullis is snapped into place
4.  Next, place a **"NorPullChain01"** on the wall nearby
5.  Double-Click the NorPortcullis and click on the **Activate Parents** tab. (_Fig 6.2_)
6.  Double-click the empty white area and a "**Choose Reference**" dialog box will appear. (_Fig 6.3_)
7.  Click the **Select Reference in Render Window** button. (_Fig 6.4_) Note the crosshair cursor: [![CrosshairRed.png](https://ck.uesp.net/w/images/8/81/CrosshairRed.png)](https://ck.uesp.net/wiki/File:CrosshairRed.png)
8.  Double-click on the "NorPullChain01" in the Render Window. (_Fig 6.5_)
9.  Click OK to close and accept both windows.(_Figs 6.6/6.7_)
10.  Notice a blue/white line now drawing between the portcullis and switch. This represents the activate parent relationship.

-   [![](https://ck.uesp.net/w/images/thumb/5/5b/Portcullis01.jpg/270px-Portcullis01.jpg)](https://ck.uesp.net/wiki/File:Portcullis01.jpg)
    
    **Fig. 6.2**:  
    The Activate Parents tab on the Portcullis
    
-   [![](https://ck.uesp.net/w/images/thumb/b/b1/Portcullis02.jpg/270px-Portcullis02.jpg)](https://ck.uesp.net/wiki/File:Portcullis02.jpg)
    
    **Fig. 6.3**:  
    Double click in the Activate Parent Ref section
    
-   [![](https://ck.uesp.net/w/images/thumb/9/96/Portcullis03.jpg/270px-Portcullis03.jpg)](https://ck.uesp.net/wiki/File:Portcullis03.jpg)
    
    **Fig. 6.4**:  
    Activate Ref Selection
    
-   [![](https://ck.uesp.net/w/images/thumb/5/5e/Portcullis04.jpg/270px-Portcullis04.jpg)](https://ck.uesp.net/wiki/File:Portcullis04.jpg)
    
    **Fig. 6.5**:  
    Select the Pull Chain
    
-   [![](https://ck.uesp.net/w/images/thumb/4/45/Portcullis05.jpg/270px-Portcullis05.jpg)](https://ck.uesp.net/wiki/File:Portcullis05.jpg)
    
    **Fig. 6.6**:  
    OK Activate Ref
    
-   [![](https://ck.uesp.net/w/images/thumb/0/06/Portcullis06.jpg/270px-Portcullis06.jpg)](https://ck.uesp.net/wiki/File:Portcullis06.jpg)
    
    **Fig. 6.7**:  
    OK Reference
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>An object can have more than one activate parent. For example, it's usually wise to provide a lever on either side of a portcullis, just in case the player somehow becomes trapped on the wrong side of it.<p>You may also notice a checkbox which will cause a reference to ignore all activation from non-parents.</p></td></tr></tbody></table>

## Ambushes\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=4 "Edit section: Ambushes") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=4 "Edit section: Ambushes")\]

## Finding and Placing an Ambush Prefab\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=5 "Edit section: Finding and Placing an Ambush Prefab") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=5 "Edit section: Finding and Placing an Ambush Prefab")\]

This dungeon already features several encounters, but no clear climax. We'll add one now; a boss draugr will climb out of a tomb as the player enters the final chamber. Creating an event like this can be complex when done from scratch. Because of this, you are provided with a set of "**[prefabs](https://ck.uesp.net/wiki/Glossary#Prefab "Glossary")**" - which are simply a collection of objects which have already been scripted and connected for you.

1.  Load the interior cell "**warehouseAmbushes**"
2.  Make sure Markers are visible (_M hotkey_)
3.  Direct your attention to the draugr ambush prefabs along the south end of the cell
4.  There are two horizontal sarcophagus prefabs. We want the one pictured in _Fig 6.9_.
5.  Using either drag-select or ctrl+click, select _all_ of the following five references:
    1.  **LvlDraugrAmbushMelee1HMale**
    2.  **defaultActivateSelfTRIG**
    3.  **DragonPriestCoffinMarker**
    4.  **NorSarcophagusTopAnim01**
    5.  **NorSarcophagusBottom**
6.  With all these objects selected simultaneously, press **ctrl+C** to copy. Note that copying the references individually will not work; you'll lose their relationship data.
7.  Load **LokirsTomb01**.
8.  Focus the camera on the cave area and press **"ctrl+V"** to paste the prefab objects

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>When making complex, multi-object selections such as this, it can be useful to cycle visibility with the <b>"1"</b> key. Selected objects will be faded, hidden, and un-hidden by this key, making it easy to determine what you have and haven't got selected.</td></tr></tbody></table>

Don't worry too much about pasting your prefab exactly where you want it placed. It's often easier to move them into the [Void](https://ck.uesp.net/wiki/Void "Void") somewhere nearby and move each element into the scene piecemeal, as in _Fig 6.10_. The important thing is to be mindful of objects which have been lined up carefully in the prefab. Let's go ahead and do that now:

1.  Select the _Sarcophagus, Lid_, and the orange _Furniture Marker_.
2.  Turn Snap-To-Grid off it is isn't already. (_Q hotkey_)
3.  Move these, as a group, onto the raised platform in our cave area of our dungeon. (_Fig 6.11_)
4.  _Optional_ Position the **LvlDraugrAmbushMelee1HMale** near the sarcophagus. It will start in the sarcophagus; this is a visual aid for yourself.
5.  _Optional_ Assuming you want a traditional "boss" encounter, set the difficulty of the draugr to **Very Hard** as shown in the [previous tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Encounters "Bethesda Tutorial Encounters") and/or replace with **LvlDraugrAmbushBossMale** (Control+F)
6.  Modify your [navmesh](https://ck.uesp.net/wiki/Category:Navmesh "Category:Navmesh") to cut out the area now beneath the sarcophagus.
7.  Move the blue triggerbox into the room. (_Fig 6.12_) It isn't going to help us much in its current state - We'll deal with that next.

-   [![](https://ck.uesp.net/w/images/thumb/4/4c/Ambush104.jpg/150px-Ambush104.jpg)](https://ck.uesp.net/wiki/File:Ambush104.jpg)
    
    **Fig. 6.9**:  
    The Horizontal Sarcophagus Ambush prefab
    
-   [![](https://ck.uesp.net/w/images/thumb/4/4a/Ambush105.jpg/236px-Ambush105.jpg)](https://ck.uesp.net/wiki/File:Ambush105.jpg)
    
    **Fig. 6.10**:  
    Ambush set up pasted into Lokir's Tomb and moved into the void
    
-   [![](https://ck.uesp.net/w/images/thumb/f/f8/Ambush106.jpg/260px-Ambush106.jpg)](https://ck.uesp.net/wiki/File:Ambush106.jpg)
    
    **Fig. 6.11**:  
    Sarcophagus set up moved into place
    
-   [![](https://ck.uesp.net/w/images/thumb/e/ed/Ambush107.jpg/140px-Ambush107.jpg)](https://ck.uesp.net/wiki/File:Ambush107.jpg)
    
    **Fig. 6.12**:  
    Triggerbox moved into place
    

## Triggering an Ambush\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=6 "Edit section: Triggering an Ambush") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=6 "Edit section: Triggering an Ambush")\]

The blue trigger is a critical element of the prefab. When the player collides with it, the draugr begins to climb out of its tomb. The default size of the trigger doesn't do much good, however. We'll need something bigger to stage this event well. We'll use non-uniform scaling to sculpt a custom trigger shape to fit the room.

1.  Select the blue trigger [primitive](https://ck.uesp.net/wiki/Creating_Primitives "Creating Primitives")
2.  Press "**2**" to bring up the [Scale Gizmo](https://ck.uesp.net/wiki/Bethesda_Tutorial_Creation_Kit_Interface#Gizmos "Bethesda Tutorial Creation Kit Interface").
3.  Notice that the non-uniform gizmo (_Fig 6.13_) offers two handles per axis.
4.  Place your cursor over one of the red x-axis handles. Click and hold when the handle turns yellow.
    1.  _NOTE: If your red/green handles are reversed, don't worry. This just means your trigger is rotated and won't cause any erors._
5.  Drag your cursor to scale the trigger to a thickness similar to that in _Fig 6.14_.
6.  Repeat this process with the green y-axis handle to stretch the trigger across the room, as in _Fig 6.15_.
7.  Use the blue z-axis handles to stretch the trigger vertically so that there's no chance the player will go over or under it.
8.  Move the trigger to cover the transition between hall and cave, and re-scale as neccessary (_Fig 6.16_). Use your own judgement on the right moment to trigger the ambush.
9.  Press "**2**" again to dismiss the gizmo and resume normal editing.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>There are a few rules of thumb to keep in mind for good trigger placement:<ul><li>Very large triggers can be slightly more expensive to process. In general, however, err on the side of too large.</li><li>Avoid "thin" triggers, which may fail to detect actors. 128 is a good minimum thickness on all axes.</li><li>Get creative with trigger positioning. Sometimes the most efficient trigger will be placed at a strange angle.</li><li>It's possible to manually define the dimensions of a primitive. Double-click to open reference properties, and navigate to the "Primitive" tab. The XYZ Bounds values define how thick the primitive is along the corresponding axis.</li><li>Primitives can also be colored however you like, also from the <i>Primitive</i> tab. This can be a useful way to color-code triggers for personal reference.</li><li>Chokepoints are useful for triggers you want to be sure get hit.</li></ul></td></tr></tbody></table>

Save your plugin and test the ambush in-game several times. Try to role-play as different types of players, who may be sneaking, running backwards, or doing anything else you can think of. Strive to make the staging of your ambush work for as many player circumstances as possible.

You may wish to add more draugr ambushes to your level. You can also trigger multiple ambushes from a single trigger - feel free to try [this extended tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Multiple_Ambushes "Bethesda Tutorial Multiple Ambushes") before moving on, which covers that. The [completed example plugin](https://ck.uesp.net/w/index.php?title=Special:Upload&wpDestFile=LDAmbushesTrapsTutorialComplete.esp "LDAmbushesTrapsTutorialComplete.esp") also includes some additional ambushes set up this way.

-   [![](https://ck.uesp.net/w/images/thumb/7/71/Ambush108.jpg/170px-Ambush108.jpg)](https://ck.uesp.net/wiki/File:Ambush108.jpg)
    
    **Fig. 6.13**:  
    Scale Gizmo for trigger primitive
    
-   [![](https://ck.uesp.net/w/images/thumb/9/97/Ambush109.jpg/270px-Ambush109.jpg)](https://ck.uesp.net/wiki/File:Ambush109.jpg)
    
    **Fig. 6.14**:  
    Triggerbox scaled in one direction
    
-   [![](https://ck.uesp.net/w/images/thumb/f/fb/Ambush110.jpg/270px-Ambush110.jpg)](https://ck.uesp.net/wiki/File:Ambush110.jpg)
    
    **Fig. 6.15**:  
    Triggerbox scaled in the other direction
    
-   [![](https://ck.uesp.net/w/images/thumb/1/10/Ambush111.jpg/266px-Ambush111.jpg)](https://ck.uesp.net/wiki/File:Ambush111.jpg)
    
    **Fig. 6.16**:  
    Triggerbox scaled to cover hallway
    

## Traps\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=7 "Edit section: Traps") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=7 "Edit section: Traps")\]

Ambushes aren't the only gameplay device for which prefabs are useful. Most traps are also composed of several objects working in concert with each other. Traps are a useful pacing device, even when they are easily noticed and avoided. Players will be on the lookout for other traps and the chance to lure enemies into them.

One of the traps available is a simple swinging mace. We'll place one of these into Lokir's Tomb as an example.

## Using a Prefab Mace Trap\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=8 "Edit section: Using a Prefab Mace Trap") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=8 "Edit section: Using a Prefab Mace Trap")\]

Setting up a trap prefab isn't very different from the process involved with a ambush prefab. Follow along with these steps:

1.  Load the interior cell "**warehouseTraps**"
2.  Locate "**TrapMace01**" (_Fig 6.33_) \[The easiest way to locate a specific trap is find it in the list that displays all the objects in the current cell (bottom-right of the Cell View window) and double click it\]
3.  Note the blue/white line which renders once the mace is selected
4.  Select the **"TrapMace01**" and connected "**TrapTripwire01**" object. (_Fig 6.34_)
5.  Ctrl+C to copy
6.  Load "**LokirsTomb**"
7.  Ctrl+V to paste into the cell
8.  Position the mace as desired. Keep in mind it will swing/hang freely after the trap has been sprung.
9.  Position the tripwire as desired. You can use _Fig 6.36_ as a guideline.

Test your trap in game several times. You may wish to tweak the placement of the tripwire and mace quite a bit before finding a setup that you're happy with.

-   [![](https://ck.uesp.net/w/images/thumb/2/2d/MaceTrap1.jpg/179px-MaceTrap1.jpg)](https://ck.uesp.net/wiki/File:MaceTrap1.jpg)
    
    **Fig. 6.33**:  
    Locating the Mace Trap in WarehouseTraps
    
-   [![](https://ck.uesp.net/w/images/thumb/1/1d/MaceTrap2.jpg/179px-MaceTrap2.jpg)](https://ck.uesp.net/wiki/File:MaceTrap2.jpg)
    
    **Fig. 6.34**:  
    Activate parent link between Mace Trap and Tripwire
    
-   [![](https://ck.uesp.net/w/images/thumb/b/b7/MaceTrap4.png/179px-MaceTrap4.png)](https://ck.uesp.net/wiki/File:MaceTrap4.png)
    
    **Fig. 6.36**:  
    Final placement of Mace Trap and Tripwire
    

## Non-Prefab Traps\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=9 "Edit section: Non-Prefab Traps") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=9 "Edit section: Non-Prefab Traps")\]

Not all traps require prefabs or separately-placed triggers, such as the examples in _Figs 6.49a-d_ below. These can be placed directly into your space like any other object, and they should work automatically. Although they are not prefabs, these are still available in "**WarehouseTraps**" for your convenience.

Try to think of clever ways to use traps in conjunction with the environment, characters and other traps. For example, a room full of oil pools and lanterns could be interesting place to battle a fire mage.

You can also mix and match traps with different triggers, such as pressure plates, levers and triggers. Feel free to experiment as you learn the system. You may also want to take a look at the [Advanced Traps Tutorial](https://ck.uesp.net/wiki/Advanced_Traps_Tutorial "Advanced Traps Tutorial") for more information.

-   [![](https://ck.uesp.net/w/images/thumb/6/66/NoTriggerTraps1.jpg/230px-NoTriggerTraps1.jpg)](https://ck.uesp.net/wiki/File:NoTriggerTraps1.jpg)
    
    **Fig. 6.49a**:  
    TrapOilPool01. Fire will spread across overlapping pools.
    
-   [![](https://ck.uesp.net/w/images/thumb/5/5d/NoTriggerTraps2.jpg/230px-NoTriggerTraps2.jpg)](https://ck.uesp.net/wiki/File:NoTriggerTraps2.jpg)
    
    **Fig. 6.49b**:  
    BearTrap01 with built-in trigger (orange marker)
    
-   [![](https://ck.uesp.net/w/images/thumb/5/5b/NoTriggerTraps3.jpg/230px-NoTriggerTraps3.jpg)](https://ck.uesp.net/wiki/File:NoTriggerTraps3.jpg)
    
    **Fig. 6.49c**:  
    TrapNorFirePlate01. Red marker indicates hazardous.
    
-   [![](https://ck.uesp.net/w/images/thumb/9/91/NoTriggerTraps4.jpg/230px-NoTriggerTraps4.jpg)](https://ck.uesp.net/wiki/File:NoTriggerTraps4.jpg)
    
    **Fig. 6.49d**:  
    Trap Rune Projectiles
    

## Other Prefabs\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&veaction=edit&section=10 "Edit section: Other Prefabs") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Traps_and_Prefabs&action=edit&section=10 "Edit section: Other Prefabs")\]

Prefabs aren't only useful for traps and ambushes. There are [other types of prefabs](https://ck.uesp.net/wiki/Additional_Prefabs "Additional Prefabs") available, such as mining ore nodes or barred doors. Try this [optional tutorial](https://ck.uesp.net/wiki/Additional_Prefabs "Additional Prefabs") if you'd like to add some now. (Some are included in the example file)

Now that your dungeon has some gameplay, it's time to start thinking about performance. We'll cover optimization in the next chapter - because no matter how brilliant your content may be, it's no fun if it doesn't run.

<table><tbody><tr><th><b><a href="https://ck.uesp.net/wiki/CreationKit:Language_policy" title="CreationKit:Language policy">Language:</a></b></th><td><b><a>English</a></b> <span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="fr"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Traps_and_Prefabs/fr" title="Bethesda Tutorial Traps and Prefabs/fr">français</a></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></td></tr></tbody></table>