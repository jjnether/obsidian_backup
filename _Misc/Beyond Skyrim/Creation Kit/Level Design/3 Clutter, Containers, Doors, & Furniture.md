## Overview

In this chapter we will go over cluttering the dungeon with static and moveable objects, adding furniture and adding loot.

The reader will learn:

-   The different types of clutter
-   How to place regular and leveled loot
-   Adding furniture
-   Placing doors

## Basic Clutter

Right now you have a very basic layout for the dungeon with empty rooms and repeating wall pieces. This section will give you some tips on how to nicely break up the space as well as personalizing the rooms to give the dungeon a cohesive feeling.

We'll begin by covering the many types of objects available and exploring several small examples. Once you're done, you should be well equipped to clutter Lokir's Tomb however you want.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>It's helpful to give every room a purpose or story when creating it. This will make it easier to clutter since you're just filling in what the room should have as opposed to just adding things to make the room look full. It is also obvious to the player when the room has a reason for existing.</td></tr></tbody></table>

## Find & Replace: Swapping Repetitive Pieces

The first and simplest way to add some variety to your rooms is by swapping out any repeating kit pieces. To do this you'll need to select the piece you want to replace and use the **Ctrl+F** hotkey which will bring up the **Search & Replace** prompt.

[![](https://ck.uesp.net/w/images/9/99/Pn_searchAndReplacePrompt.jpg)](https://ck.uesp.net/wiki/File:Pn_searchAndReplacePrompt.jpg)

**Fig. 3.1:** Search and Replace prompt

Let's try it out now by swapping one of our repetitive wall pieces for a variant.

1.  Select a _NorRmSmWallSide01_ piece anywhere in your dungeon.
2.  Press Ctrl+F to summon the Search & Replace dialog. The editor may hitch.
3.  The next alphabetical piece - _NorRmSmWallSide02_, in this case - is automatically selected
4.  Press **OK** to change the piece.

As long as you have one or more of the same piece selected, you can now change the selection in the Replace With field to replace the selected pieces.

If you explore the list of available pieces, you'll notice the nordic wall has about eight variations to choose from, including damaged versions. Use the Search & Replace tool and swap out some of your walls so they do not repeat. Swapping in some damaged walls will help add a ruined feeling to the dungeon.

You can use Search & Replace on any object in the game to quickly check if it has variations. If you try it on the nordic floors, for example, you may see that you can replace the flat ground with a pillar. When kit pieces are named, the alphabetical sorting in search & replace is taken into consideration to make these changes quick and easy.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>You may have noticed that there are three checkboxes at the bottom of the Search &amp; Replace dialog, with "<i>Selection Only</i>" being chosen by default. This is what you'll want most of the time, but you can also swap all instances of a piece by cell and worldspace. Less obviously, you can perform a swap on every object in the game by unchecking all three boxes. Be careful to only do this if you're absolutely sure! Ctrl+F operations cannot be undone.</td></tr></tbody></table>

## Static Clutter

Static pieces of clutter make up the majority of large objects in the game. They are placed in the editor and cannot be moved, interacted with, or otherwise influenced by the player. Statics may be items such as tables, platforms, book cases, rubble piles and the kit pieces we've been working with so far.

### Placing Objects

If you know what pieces you're looking for, you can use ctrl+D to duplicate a piece you already have in the scene and replace it with something else. This is a common workflow technique for advanced level designers, as it can be much faster than manually searching for each piece in the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window") window.

Let's go through the motions by quickly placing an altar into one of our rooms.

1.  Select any floor piece from the first room in your dungeon
2.  Duplicate it with **ctrl+D** - _Note that upon duplication, the new reference is automatically selected._
3.  Use Ctrl+F to begin Search & Replace
4.  Replace it with the **RuinsAltar** piece. - _You can do this by manually scrolling through the drop-down list, but it's must faster to click into that list and type the first several letters of the desired piece._
5.  Position your new altar in the center of the first room

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>Because duplicated items inherit the exact position, rotation and dimensions of the object they are duplicated from, it's a common mistake to accidentally leave the duplicate item in place. This is a common cause of <i>z-fighting</i>, a common error in games when two overlapping surfaces cause a flickering effect. Be sure to keep an eye out for this as you work.</td></tr></tbody></table>

Clutter will usually follow a naming convention, although it is less stringent than kit naming. If you're looking for all of the nordic clutter you can search for static objects beginning with the prefix _**Ruins**_. Here you'll find the benches, altars, tables and other large pieces of clutter appropriate to the setting.

Not all clutter has to add new items and obstacles to a space, however. Perfectly flat, tiling floors create a very sterile and artificial feeling in our spaces. Floor pieces and rubble piles are excellent ways to break up rooms and floors.

1.  Place some **NorRmSmFloorRaised01** objects and 02s around to break up the floor
2.  Don't worry lining up with the floor pattern - rotate these pieces freely for the best visual effect
3.  Also place some **NorRubblePile01-08** pieces
4.  Rubble piles are effective in corners and where the wall meets the floor, creating a more natural flow of space

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>For added effect, use the raised floor under your rubble piles to make it look like chunks of the floor have damage. You can also line up the edges to create small canals in the floor to lead the player to areas.</td></tr></tbody></table>

Feel free to add some other static clutter around the room to fill it out as you see fit. This room is to be the entrance to the tomb where people came to pay their respects. Try to find ways to support that through your clutter.

## Scaling Objects

[![](https://ck.uesp.net/w/images/thumb/2/28/Pn_scalePrompt.jpg/250px-Pn_scalePrompt.jpg)](https://ck.uesp.net/wiki/File:Pn_scalePrompt.jpg)

**Fig. 3.2:** Scale value in Reference Properties Window

Scale and rotation are useful tools while cluttering with static objects. Through clever scale and rotation, you can reuse a small amount of pieces multiple times in an area before they become too repetitive.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>To maintain the proper look of a piece, you should only scale between 0.5 and 1.5. This rule of thumb preserves not only logical and visual consistency, but prevents the texel density of surfaces in an environment from becoming too disproportionate.</td></tr></tbody></table>

### Scale An Object

Next, we'll place some **ruinsFloorCandle...** objects around the entrance and use scaling and rotating to prevent them from looking the same. There are a few different ways to scale an object. Try each of these to find what you prefer.

**Manual Scaling** This technique is useful for precise scaling.

1.  Double click on the object to bring up its [Reference Properties](https://ck.uesp.net/wiki/Reference "Reference") Window
2.  You'll find Scale at the bottom of the 3D Data tab
3.  Use the arrows or type the number in manually

**Free Scaling** This technique is most useful when you want to quickly scale one or more objects arbitrarily.

1.  Select the object(s) you'd like to scale.
2.  Press and hold the **S** key
3.  Drag the mouse to affect scale.

**Gizmo Scaling** This technique provides a visual tool for arbitrarily scaling one or more objects. Gizmos are discussed in detail [here](https://ck.uesp.net/wiki/Bethesda_Tutorial_Creation_Kit_Interface#Gizmos "Bethesda Tutorial Creation Kit Interface"). **NOTE:** _Although the scaling gizmo has axis handles, non-uniform scaling is not supported except when dealing with [editor-created primitives](https://ck.uesp.net/wiki/Creating_Primitives "Creating Primitives") such as triggers and roombounds._

1.  Select the object(s) you'd like to scale.
2.  Press the **2** key to summon the scaling gizmo
3.  Drag the mouse to affect scale.
4.  Press the **2** key to dismiss the scaling gizmo and resume normal selection.

## Moveable Clutter

_Moveable_, or _"dynamic"_ clutter are physics-enabled objects that the player can move around or interact with in some way. This kind of clutter gives the space life and allows the player to interact with the world making it feel more real. The different types are listed below. Note that objects with no physics data will never be movable, regardless of object type. (ToDo: explain what physics data is, and how you can detect whether an object has some).

### Misc Item

Misc items are the most prominent type of moveable clutter in the game and includes things like plates, utensils, goblets and buckets.  

**The defining properties of a Misc Object**

-   Objects the player can manipulate in game
-   Player can pick these up and add them to their inventory
-   Some Misc Items are valuable/useful, and this should be considered for pacing/balance reasons.

Place some misc items around the room, like the examples below:

-   [![](https://ck.uesp.net/w/images/thumb/1/15/ClutterBucket01.jpg/120px-ClutterBucket01.jpg)](https://ck.uesp.net/wiki/File:ClutterBucket01.jpg)
    
    **Fig. 3.3**:  
    Bucket01
    
-   [![](https://ck.uesp.net/w/images/thumb/8/8c/ClutterLantern01.jpg/120px-ClutterLantern01.jpg)](https://ck.uesp.net/wiki/File:ClutterLantern01.jpg)
    
    **Fig. 3.4**:  
    Lantern01
    
-   [![](https://ck.uesp.net/w/images/thumb/6/62/ClutterLeather01.jpg/120px-ClutterLeather01.jpg)](https://ck.uesp.net/wiki/File:ClutterLeather01.jpg)
    
    **Fig. 3.5**:  
    Leather01
    
-   [![](https://ck.uesp.net/w/images/thumb/f/fb/ClutterLinens01.jpg/120px-ClutterLinens01.jpg)](https://ck.uesp.net/wiki/File:ClutterLinens01.jpg)
    
    **Fig. 3.6**:  
    RuinsLinenPile01
    
-   [![](https://ck.uesp.net/w/images/thumb/a/ac/ClutterScapel01.jpg/120px-ClutterScapel01.jpg)](https://ck.uesp.net/wiki/File:ClutterScapel01.jpg)
    
    **Fig. 3.7**:  
    RuinsScalpel
    
-   [![](https://ck.uesp.net/w/images/thumb/d/d6/ClutterScissors01.jpg/120px-ClutterScissors01.jpg)](https://ck.uesp.net/wiki/File:ClutterScissors01.jpg)
    
    **Fig. 3.8**:  
    RuinsScissor
    

### Moveable Statics

Moveable statics are pieces of clutter that the player can move, but cannot take. This includes things like bones, urn chunks and some rubble blocks.

**The defining properties of a Moveable Static**

-   Player can manipulate/grab in game
-   Player **cannot** add these to their inventory

Try placing some of the example items below around your level:

-   [![](https://ck.uesp.net/w/images/thumb/2/24/ClutterBoneDeerSkull01.jpg/120px-ClutterBoneDeerSkull01.jpg)](https://ck.uesp.net/wiki/File:ClutterBoneDeerSkull01.jpg)
    
    **Fig. 3.9**:  
    BoneDeerSkull01
    
-   [![](https://ck.uesp.net/w/images/thumb/e/eb/ClutterBoneHumanRibcage01.jpg/120px-ClutterBoneHumanRibcage01.jpg)](https://ck.uesp.net/wiki/File:ClutterBoneHumanRibcage01.jpg)
    
    **Fig. 3.10**:  
    BoneHumanRibcage
    
-   [![](https://ck.uesp.net/w/images/thumb/7/7e/ClutterHandCartWheel01.jpg/120px-ClutterHandCartWheel01.jpg)](https://ck.uesp.net/wiki/File:ClutterHandCartWheel01.jpg)
    
    **Fig. 3.11**:  
    HandCartWheel
    
-   [![](https://ck.uesp.net/w/images/thumb/a/a6/ClutterHook01.jpg/120px-ClutterHook01.jpg)](https://ck.uesp.net/wiki/File:ClutterHook01.jpg)
    
    **Fig. 3.12**:  
    Hook
    
-   [![](https://ck.uesp.net/w/images/thumb/1/18/ClutterRuinsPot01.jpg/120px-ClutterRuinsPot01.jpg)](https://ck.uesp.net/wiki/File:ClutterRuinsPot01.jpg)
    
    **Fig. 3.13**:  
    RuinsPot01
    
-   [![](https://ck.uesp.net/w/images/thumb/c/cd/ClutterWagonWheel01.jpg/120px-ClutterWagonWheel01.jpg)](https://ck.uesp.net/wiki/File:ClutterWagonWheel01.jpg)
    
    **Fig. 3.14**:  
    WagonWheel
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Interactivity can be both a blessing and a curse for player immersion. Where two visually-similar but differently-typed objects are adjacent, it damages immersion, as the player can take or use one, but not the other. If one skeleton in an area can be searched, all should be searchable. If you used a <i>RuinsFloorCandleLamp...</i> static, it should not be adjacent to -- or even in the same room as -- a <i>RuinsFloorCandleStand...</i> movable static, or the player will be asking "why can I only knock stands over when they have no candles on?"</td></tr></tbody></table>

### Physics Settling

[![](https://ck.uesp.net/w/images/thumb/f/fd/Pn_HavokButton.jpg/350px-Pn_HavokButton.jpg)](https://ck.uesp.net/wiki/File:Pn_HavokButton.jpg)

**Fig. 3.15:** "Run Havok Sim" Button

Physics settling is an important tool in the editor. This feature allows you to switch physics on in the editor, causing any selected, physics-enabled objects to interact with the environment. This is much faster and often more accurate than manually placing all objects.

**Havok Preview Button**

Pressing the **Run Havok Sim** button, pictured in _Fig. 3.15_, with a moveable static selected will cause the object to behave as it would in-game. This is a great way to make clutter placement look more random, or to see how an object will act if the game were running.

[![](https://ck.uesp.net/w/images/thumb/b/b7/Pn_dontHavokSettle.jpg/250px-Pn_dontHavokSettle.jpg)](https://ck.uesp.net/wiki/File:Pn_dontHavokSettle.jpg)

**Fig. 3.16:** Don't Havok Settle Checkbox

1.  Select one of placed ruinsPot\*s you've placed
2.  Raise and rotate it in mid-air above the floor
3.  Keeping the object selected, press the Havok button [![IconHavok.png](https://ck.uesp.net/w/images/4/43/IconHavok.png)](https://ck.uesp.net/wiki/File:IconHavok.png)
4.  Allow the pot will fall to the ground and roll around until it settles
5.  When satisfied with the positioning of the pot, turn settling back off.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>In order for Havok Sim to work, the selected object must be from the <b>moveable static</b> item list. Static items will not react the "Run Havok Sim" button is pressed.</td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td>Unlike previous Bethesda toolsets, physics-enabled objects in the Creation Engine will automatically settle when they are loaded in-game. Objects marked with "<b>Don't Havok Settle</b>", shown in <i>Fig 3.16</i>, will skip their initial settle, but still simulate when affected by some impulse in-game. For example, a bucket in mid-air with this box checked will still be floating in that position when you load the game. Once hit by some other physics entity, however - such as an arrow, spell or the player - it will behave just like any other object.</td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Because all objects settle once the player gets close enough, it is important to run Havok settling on the whole area before releasing it, by zooming out, drag-selecting the whole map, and clicking the Havok button, then going back and checking that none of the objects "settled" down through shelves or tables! While it can be painful to find and fix all these settling bugs, and you may not even find all items that disappeared, it is still far better than having the player walk up to an item on a table, only to see it sink away out of sight!</td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>For advanced users who wish to disable the physics simulation of an object entirely, there is an included <a href="https://ck.uesp.net/wiki/Category:Papyrus" title="Category:Papyrus">Papyrus</a> script called <b><a href="https://ck.uesp.net/wiki/SetMotionType_-_ObjectReference" title="SetMotionType - ObjectReference">defaultDisableHavokOnLoad</a></b> which can be attached specifically for this purpose, although its use is not necessary for this tutorial.</td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>It is much easier to use Havok settling to place an item at a realistic angle, than to rotate a static item and make sure it is resting correctly. So where there are movable and static versions of the same object, and you wish to place the static one to rest on an angled surface, it is often faster to place the movable version, settle it, then use Ctrl-F to convert it to the static version. <b>RuinsPot</b> and <b>RuinsPotStatic</b> are good examples of this.</td></tr></tbody></table>

### Animating Objects

Animating objects are a type of moveable static that the player cannot interact with, but provides particles or an animation. Some examples would be banners, fires or water drips. Placing fire effects in sconces is a great way to create light sources - although you will have to add the actual light-casting actor separately. This is covered in a [later tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Lights_and_FX "Bethesda Tutorial Lights and FX").

**The defining properties of an Animating Object**

-   These objects remain in place but have built in particles or animations
-   Player **cannot** manipulate these in game
-   Player **cannot** add these to their inventory

  
Place some animating objects around the rooms, such as the examples below.

-   [![](https://ck.uesp.net/w/images/thumb/d/d2/ClutterFXFire01.jpg/120px-ClutterFXFire01.jpg)](https://ck.uesp.net/wiki/File:ClutterFXFire01.jpg)
    
    **Fig. 3.17**:  
    FXFireWithEmbersHeavy
    
-   [![](https://ck.uesp.net/w/images/thumb/a/a6/ClutterBanenr01.jpg/120px-ClutterBanenr01.jpg)](https://ck.uesp.net/wiki/File:ClutterBanenr01.jpg)
    
    **Fig. 3.18**:  
    GenericBannerBlue01
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>It's important never to rest non-movable statics ontop of movable objects. <b>FXFireWithEmbersHeavy</b> looks quite nice in a <b>RuinsPot</b> - but this would be a mistake. The player can move the RuinsPot, and the fire would look very wrong. This is the type of situation where a static version of a movable object comes in handy - <b>RuinsPotStatic</b> in this case.</td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td>Corpses can also be placed using physics settling. Unlike previous Bethesda toolsets, however, simply setting the health of an actor doesn't actually cause it to be dead at game time. In order to mark an actor dead (and, in turn, allow it to be settled in-editor), check the <b>"Starts Dead"</b> checkbox on the reference properties. This is visible in the grayed-out area of <i>Fig 3.16</i>, just above "OK" and "Respawns".</td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>It's possible to adjust the position of a physics-enabled object while simulation is toggled on. For small, precise changes, try holding alt and dragging on the object. This is especially useful for objects with multiple joints, such as corpses, as you can grab the individual "bones" in the rig.</td></tr></tbody></table>

## Loot

Ah, loot. Searching for and acquiring new items is a core element of the Skyrim experience, and should be considered an integral part of your dungeon. Luckily, the Creation Kit includes several ways to populate your dungeon with loot, including loosely placed items, containers and leveled items. Let's consider some of the options we can work with.

## Loose Loot

Just about any object in the editor can be placed loosely in your space. This can serve the dual purpose of providing loot and visual interest to a space. Here are a few of the major object types at your disposal:

-   **[Armor](https://ck.uesp.net/wiki/Armor "Armor"):** Any objects that the player can wear, including non-armored clothing. Single pieces like gloves, boots and helmets will show up in the editor/game as their normal pieces, but chest pieces will appear folded up.

-   **[Books](https://ck.uesp.net/wiki/Book "Book"):** Regular books are a great object to throw around rooms. Pepper in an occasional spell tome or skill book to keep the player reading them. Keep in mind that vanilla Skyrim dungeons typically only include one skill book, if any. When a player activates a book in the world it will open the book but not automatically give it to the player.

-   **Ingredients** These are objects like food and alchemy ingredients that the player can pick up and consume for an effect. Used in alchemy and potion creation.

-   **[Potions](https://ck.uesp.net/wiki/Potion "Potion")** Similar to ingredients

-   **[Weapons](https://ck.uesp.net/wiki/Weapon "Weapon")** The weapons usable by the player. When placed in the world these will appear the same as when the player would have them equipped.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Don't Havok Settle is a great way to have objects appear to be mounted on walls. There are some examples at the final room in the south hall with some weapons "mounted" to the head sculptures.</td></tr></tbody></table>

## Containers

Containers are objects like chests and urns that have an internal list of what the player can receive when looted. The chest fills itself when the cell is loaded. One of the major benefits of placing a chest is that most pre-made chests are designed to scale the loot to the player's level. That way you don't have to place separate objects to take the player's level in to account.

Place some containers around the room, such as the examples below. Note the "_Treas_" prefix. This is short for "treasure", meaning that these containers are more likely to have items of value.  

-   [![](https://ck.uesp.net/w/images/thumb/4/49/ContainerBarrel.jpg/120px-ContainerBarrel.jpg)](https://ck.uesp.net/wiki/File:ContainerBarrel.jpg)
    
    **Fig. 3.22**:  
    BarrelFood01
    
-   [![](https://ck.uesp.net/w/images/thumb/5/53/ContainerMiscSack.jpg/120px-ContainerMiscSack.jpg)](https://ck.uesp.net/wiki/File:ContainerMiscSack.jpg)
    
    **Fig. 3.23**:  
    MiscSackLarge
    
-   [![](https://ck.uesp.net/w/images/thumb/3/3d/ContainerDraugrChest.jpg/120px-ContainerDraugrChest.jpg)](https://ck.uesp.net/wiki/File:ContainerDraugrChest.jpg)
    
    **Fig. 3.24**:  
    TreasDraugrChest
    
-   [![](https://ck.uesp.net/w/images/thumb/e/e2/ContainerRuinsUrn.jpg/120px-ContainerRuinsUrn.jpg)](https://ck.uesp.net/wiki/File:ContainerRuinsUrn.jpg)
    
    **Fig. 3.25**:  
    TreasRuinsUrnLarge02
    

### Previewing Contents

The Creation Kit offers the ability to preview the contents of any given container at various [encounter zone](https://ck.uesp.net/wiki/Encounter_Zone "Encounter Zone") levels. This can be a useful way to get an idea of what sort of loot the player may see, which can be difficult to approximate in-game due to the randomized nature of most loot containers.

1.  Double click on the object you want to preview
2.  Click **Edit Base** to view the container Base Object (_Fig 3.19_)
3.  Click on **Preview Calculated Result** (_Fig 3.19a_)
4.  This displays a randomly-generated list of loot the container may produce (_Fig 3.20_)
5.  Repeat this as many times as you'd like to see additional possible loot results
6.  You can also change the preview level to see what the loot would be like at different levels. Note that the level of a container is based on the [encounter zone](https://ck.uesp.net/wiki/Encounter_Zone "Encounter Zone") of the area a container is within, which may not always be the same as the current player level.
7.  _Fig 3.21_ shows an example of the same chest at player level 30

-   [![](https://ck.uesp.net/w/images/thumb/8/83/EditBaseButton.png/98px-EditBaseButton.png)](https://ck.uesp.net/wiki/File:EditBaseButton.png)
    
    **Fig. 3.19:** Edit Base Button
    
-   [![](https://ck.uesp.net/w/images/thumb/7/72/Pn_previewCalculatedResult.jpg/120px-Pn_previewCalculatedResult.jpg)](https://ck.uesp.net/wiki/File:Pn_previewCalculatedResult.jpg)
    
    **Fig. 3.19a:** Preview Calculated Result Button
    
-   [![](https://ck.uesp.net/w/images/thumb/1/1b/Pn_lootPreviewWindow.jpg/79px-Pn_lootPreviewWindow.jpg)](https://ck.uesp.net/wiki/File:Pn_lootPreviewWindow.jpg)
    
    **Fig. 3.20:** Loot Preview Window
    
-   [![](https://ck.uesp.net/w/images/thumb/b/b0/Pn_lootPreviewWindowL30.jpg/79px-Pn_lootPreviewWindowL30.jpg)](https://ck.uesp.net/wiki/File:Pn_lootPreviewWindowL30.jpg)
    
    **Fig. 3.21:** Loot Preview Window at Level 30
    

## [Leveled Items](https://ck.uesp.net/wiki/LeveledItem "LeveledItem")

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td><a href="https://ck.uesp.net/wiki/LeveledItem" title="LeveledItem">Leveled items</a>, or "dummy" objects, are a new feature in the Creation Kit. These allow you to place loose items that will be leveled appropriately in a space. Read on for more information!</td></tr></tbody></table>

The Creation Kit features a number of Dummy objects. These are simple markers that approximate the size and shape of various loot objects that can be loosely placed around the environment. Dummy objects do nothing on their own, and must have a [Leveled Item](https://ck.uesp.net/wiki/LeveledItem "LeveledItem") list associated to generate loot in-game. Let's place a leveled potion using a dummy now:

[![](https://ck.uesp.net/w/images/thumb/8/8a/Pn_dummyLeveledItem.jpg/250px-Pn_dummyLeveledItem.jpg)](https://ck.uesp.net/wiki/File:Pn_dummyLeveledItem.jpg)

**Fig. 3.30:** Leveled Item Tab

1.  Place a **dummyPotion** object (under Magic in the object tree window) in the level. Be sure markers are displayed (_"M" hotkey_)
2.  Double click on the object and go to the Leveled Item tab (_Fig. 3.30_)
3.  You can use the filter to search for the type of potion you want
4.  _(optional)_ Type _restore_ in the filter.
5.  Set the _Leveled Item Base Object_ to **LItemPotionRestoreHMS**

-   "_LItem_" is shorthand for [Leveled Item](https://ck.uesp.net/wiki/LeveledItem "LeveledItem"). "_HMS_" is an abbreviation of Health/Magicka/Stamina, which means this potion will restore one of those three resources.
-   You can also choose items with the "_Best"_ suffix, indicating that the list will attempt to produce the best item appropriate to the current level.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>Dummy items are counted as markers - so be sure you have the <b>"M"</b> key toggled so that you can see them!</td></tr></tbody></table>

### Some Dummy Objects

The following are some of the dummy objects you can use. Try placing some around your dungeon and experiment with the different [Litem](https://ck.uesp.net/wiki/LeveledItem "LeveledItem") lists available. Remember - if you do not set a Leveled Item, nothing will appear.

Likewise, remember that the Dummy objects are only helpers, and know nothing about their Leveled Item lists. This means that if you accidentally set up a _dummyPotion_ object with a _LItemArmorShieldHeavy_ list, for example, the item will generate a shield at run-time. The resulting shield is likely to intersect the world, depending on how the dummy object had been placed.

-   DummyBook
-   DummyBoots
-   DummyBow
-   DummyCuirass
-   DummyDagger
-   DummyGauntlets
-   DummyHelmet
-   DummyMace
-   DummyPotion
-   DummyShield
-   DummySoulGem
-   DummyWeapon1H - _Can be any one-handed weapon_
-   DummyWeapon2H - _Can be any two-handed weapon_

-   [![](https://ck.uesp.net/w/images/thumb/7/70/DummyBook.jpg/120px-DummyBook.jpg)](https://ck.uesp.net/wiki/File:DummyBook.jpg)
    
    **Fig. 3.26**:  
    Dummy Book
    
-   [![](https://ck.uesp.net/w/images/thumb/8/8c/DummyHelmet.jpg/120px-DummyHelmet.jpg)](https://ck.uesp.net/wiki/File:DummyHelmet.jpg)
    
    **Fig. 3.27**:  
    Dummy Helmet
    
-   [![](https://ck.uesp.net/w/images/thumb/3/39/DummyMace.jpg/120px-DummyMace.jpg)](https://ck.uesp.net/wiki/File:DummyMace.jpg)
    
    **Fig. 3.28**:  
    Dummy Mace
    
-   [![](https://ck.uesp.net/w/images/thumb/f/f2/DummyPotion.jpg/120px-DummyPotion.jpg)](https://ck.uesp.net/wiki/File:DummyPotion.jpg)
    
    **Fig. 3.29**:  
    Dummy Potion
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>To prevent Dummy items from being generated and then promptly settling through the furniture, place the dummies a little above the surface on which you intend for them to rest. Better for the player to hear the item drop a little, than to see it plunge through a solid tabletop to become inaccessible!</td></tr></tbody></table>

## Furniture

## Placing Markers

When placing a furniture marker, it is important to make sure that it is facing the proper direction. This isn't always obvious, as with a chair. It's easy to accidentally place a bench that will seat NPCs facing into a wall, for example. The easiest way to check for this is with the 'M' hotkey which will toggle markers. Let's place a bench now.

1.  Place a **ruinsBench01**, as shown in _Fig. 3.31_.
2.  Fig. 3.32 shows the same bench with markers toggled on _('M' Hotkey)_
3.  The blue humanoid models are where the actor will be while in the marker. Make sure they face out.
4.  The light blue diamonds indicate entry/exit nodes, and should not be blocked by any walls/objects.
5.  Place more furniture around the level, including the examples in _Fig. 3.33 and 3.34_ below.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>It is important to make sure the exit nodes go in to areas that actors can move around in. Otherwise the actor can get stuck.</td></tr></tbody></table>

-   [![](https://ck.uesp.net/w/images/thumb/a/aa/Pn_benchMarkerToggleOff.jpg/120px-Pn_benchMarkerToggleOff.jpg)](https://ck.uesp.net/wiki/File:Pn_benchMarkerToggleOff.jpg)
    
    **Fig. 3.31:** Ruins Bench with Markers toggled off
    
-   [![](https://ck.uesp.net/w/images/thumb/6/6c/Pn_benchMarkerToggleOn.jpg/120px-Pn_benchMarkerToggleOn.jpg)](https://ck.uesp.net/wiki/File:Pn_benchMarkerToggleOn.jpg)
    
    **Fig. 3.32:** Ruins Bench with Markers toggled on
    
-   [![](https://ck.uesp.net/w/images/thumb/3/31/ClutterRuinsBench01.jpg/120px-ClutterRuinsBench01.jpg)](https://ck.uesp.net/wiki/File:ClutterRuinsBench01.jpg)
    
    **Fig. 3.33**:  
    RuinsBench01
    
-   [![](https://ck.uesp.net/w/images/thumb/b/b8/ClutterNorThroneShadow.jpg/120px-ClutterNorThroneShadow.jpg)](https://ck.uesp.net/wiki/File:ClutterNorThroneShadow.jpg)
    
    **Fig. 3.34**:  
    NorThroneShadow
    

## Interactive Furniture

Some furniture markers are interactive, such as crafting stations. These are placed in the world just like regular furniture markers. Place some interactive furniture around the level, such as the examples in _Fig. 3.35-3.37_. This kind of furniture is especially useful for creating a sense of life in NPC-populated dungeons, although we won't be using them as such in this example.

-   [![](https://ck.uesp.net/w/images/thumb/1/15/CraftingAlchemyWorkbench.jpg/120px-CraftingAlchemyWorkbench.jpg)](https://ck.uesp.net/wiki/File:CraftingAlchemyWorkbench.jpg)
    
    **Fig. 3.35**:  
    Crafting AlchemyWorkbench
    
-   [![](https://ck.uesp.net/w/images/thumb/b/bc/CraftingTanningRackMarker.jpg/120px-CraftingTanningRackMarker.jpg)](https://ck.uesp.net/wiki/File:CraftingTanningRackMarker.jpg)
    
    **Fig. 3.36**:  
    Crafting TanningRackMarker
    
-   [![](https://ck.uesp.net/w/images/thumb/8/8e/CraftingEnchantingWorkbench.jpg/120px-CraftingEnchantingWorkbench.jpg)](https://ck.uesp.net/wiki/File:CraftingEnchantingWorkbench.jpg)
    
    **Fig. 3.37**:  
    Crafting EnchantingWorkbench
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Some of the crafting objects have tabletop versions as well. This is simply a version of the marker that can be placed on other objects but shares the same basic art. Be careful to line these items up with the floor properly, as to avoid NPCs (or the player) appearing sunken or floating while using them.</td></tr></tbody></table>

## Doors

Doors simply open and close when activated by the player. They can optionally be locked at various difficulties, including requiring a [Key](https://ck.uesp.net/wiki/Keys "Keys") to open.

Doors can also be set to start open; to accomplish this, check the **Open By Default** box on the reference properties. This is also a useful trick to see which way the door opens. Generally speaking, it's best to have doors swing away from the player when possible.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Open By Default also works on containers, and can be useful if you want to check the opening animation of a container (where applicable) or manually set up a chest that looks like it's already been looted.</td></tr></tbody></table>

The doors that work with this kit begin "Nor" - such as **NorDoorMedium01** and **NorDoorSm01**.

The various parts of the name are once again meaningful:

-   MinUse - The base object has the "Minimal Use" checkbox checked, which means NPCs will avoid this door if possible. This is useful to prevent NPCs from wandering into the wrong areas, and possibly to prevent companions from rampaging through inside areas that the player has not yet explored, just to get to an outer balcony.
-   Load - These doors are for teleporting to new areas. They typically do not open properly, and have only one side, and a slight "starting to open" animation.

## Locking Doors & Containers
[![](https://ck.uesp.net/w/images/thumb/4/45/Pn_lockingADoor.jpg/250px-Pn_lockingADoor.jpg)](https://ck.uesp.net/wiki/File:Pn_lockingADoor.jpg)

**Fig. 3.38:** Locking a Door

Let's try locking an object in your dungeon. You can lock a door or a container; it's your choice.

1.  Double click on the door to open the reference
2.  Navigate to the Lock tab (_Fig. 3.38_)
3.  Check the **Locked** check box
4.  **Level** is the difficulty of the lock. **Requires Key** means it cannot be picked.
5.  (_optional_) The **Key** field is for any key that can unlock the door.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Locking critical-path doors (<i>those that prevent forward progress through a space/quest</i>) is usually a bad idea unless you're providing a key somewhere. Likewise, it's generally best to avoid locking objects that wouldn't conceivably feature a keyhole, such as bags or barrels.</td></tr></tbody></table>

## Cluttering Lokir's Tomb

As you can see, there are many tools at your disposal for cluttering a space. Try employing everything you've learned here to flesh out the clutter in this, keeping in mind the purpose of each room and any story goals you may have. If you're stuck for ideas, try checking out other cells in the editor or load up the [example plugin](https://ck.uesp.net/w/index.php?title=Special:Upload&wpDestFile=LDClutterTutorialComplete.esp "LDClutterTutorialComplete.esp"), which shows a fully cluttered version of Lokir's Tomb.

Once you're satisfied with the layout and clutter of the Tomb, you're ready to move onto making the space navigable for enemies and followers - covered in the [next tutorial: Navmesh!](https://ck.uesp.net/wiki/Bethesda_Tutorial_Navmesh "Bethesda Tutorial Navmesh")

## Object Palettes (OPALs)
_OPTIONAL_  
While the Duplicate-and-Replace method described above is a fast way to place clutter (especially once you become familiar with the Creation Kit's naming conventions), you may also want to experiment with the [Object Palettes (OPAL)](https://ck.uesp.net/wiki/Object_Palettes "Object Palettes"), which allows you to create and manage collections of objects, and place them in the world directly. For more information, please refer to the tutorial on the [OPAL](https://ck.uesp.net/wiki/Object_Palettes "Object Palettes") page.