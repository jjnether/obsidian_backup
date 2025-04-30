## Overview

This chapter will show how to make an area ready to be used by radiant quests and to scale properly to the player's level. The reader will learn:

-   What is a **Location Reference Type**?
-   How can **[Radiant Story](https://ck.uesp.net/wiki/Radiant_Story "Radiant Story")** use our dungeon?
-   How to create and assign a **Location** to a Cell
-   Creating and configuring an **Encounter Zone**
-   Setting the Music and audio space for a cell

## Location Reference Types and Radiant Story

[![](https://ck.uesp.net/w/images/thumb/5/51/LocRefTypes.jpg/400px-LocRefTypes.jpg)](https://ck.uesp.net/wiki/File:LocRefTypes.jpg)

**Fig. 10.1:** LocRefTypes in the ObjectWindow.

A [Location Reference Type or **LocRefType**](https://ck.uesp.net/wiki/Location_Ref_Type "Location Ref Type"), as we more commonly refer to it, is a special type of flag that you can place on a Reference in your level that [Radiant Story (our procedural quest generation system)](https://ck.uesp.net/wiki/Radiant_Story "Radiant Story") uses to find the right objects. Essentially it lets you define for the quest system which actor is the "Boss" or which would be a good "Container" to place a quest item in, for example.

We can find the whole list of LocRefTypes under **"WorldData > Location Ref Type"** in the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window") (_Fig. 10.1_). Beyond the most advanced modding, you probably won't need to ever add new LocRefTypes.

As you can see, there are quite a lot of different LocRefTypes but for our purposes we are only interested in a much, much smaller list that we will need to place in our level.

-   **Boss** - Set the boss Actor of the dungeon (can be multiple)
-   **BossContainer** - Set on the Boss Chest in the dungeon
-   **BossTreasureMarker** - Set on an XMarker near the boss, where an important item may be
-   **CaptiveMarker** - Set on an XMarkerHeading where a captive would be kept
-   **Container** - Set on several containers in the dungeon
-   **FriendMarker** - Set on an XMarkerHeading where a friendly actor might meet you
-   **InsideEntranceMarker**\- Set on an XMarkerHeading just inside the entrance
-   **LocationCenterMarker** - Set on an XMarkerHeading in the center of the dungeon
-   **OutsideEntranceMarker** - Set on an XMarkerHeading just outside the entrance to the dungeon
-   **LocationEdgeMarker** - Set on an XMarkerHeading at the far edge of the exterior cell.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>You don't have to place all of the LocRefTypes listed in your dungeon if they don't make sense for the area. For example it doesn't always make sense for Draugr to have a captive so that might not be needed.</td></tr></tbody></table>

Let's start by setting the Boss, which is one of the most commonly used LocRefTypes. Go back to the boss we placed in the Tutorial on **Ambushes** and open up the Object Info by double clicking on the LvlDraugrAmbushBossMale or LvlDraugrAmbushMelee1HMale. Go to the second to last tab, "Location Ref Type", and set the drop down to say "Boss" then hit okay.

It's as simple as that. Notice that a small rectangular box has now appeared hovering above our Actor Marker. This our indicator that this object is flagged as a LocRefType and is very helpful for remembering which objects not to delete. Due to the large amount of unique LocRefTypes, there is not a simple color scheme, but you'll get a feel for ones you place in your dungeons frequently.

Next, on that platform, let's set the **BossContainer** LocRefType to the **TreasDrugrChestBoss** in the same way (if you have a normal TreasDrugrChest, you can replace with TreasDrugrChestBoss, but be careful with the NavMesh). If a Radiant Quest wants to place a special treasure in the Boss's Chest, this is where it will go. Let's place an Xmarker on the ground next to that chest (filter \*All for XMarker); this we will set to BossTreasureMarker. If a Radiant Quest wants to place an object near the Boss, but not in a container, this is where it will be placed. XMarkers are invisible and have no collision in game. They are used for positional data only.

-   [![](https://ck.uesp.net/w/images/thumb/f/fc/LocRefTypeBoss.jpg/99px-LocRefTypeBoss.jpg)](https://ck.uesp.net/wiki/File:LocRefTypeBoss.jpg)
    
    **Fig. 10.2:** Setting LvlDraugrAmbushBossMale to the Boss LocRefType.
    
-   [![](https://ck.uesp.net/w/images/thumb/f/f3/LocRefTypeBoss2.jpg/120px-LocRefTypeBoss2.jpg)](https://ck.uesp.net/wiki/File:LocRefTypeBoss2.jpg)
    
    **Fig. 10.3:** Red Boss LocRefType marker over the Actor Marker.
    
-   [![](https://ck.uesp.net/w/images/thumb/7/7b/LocRefTypeBoss3.jpg/120px-LocRefTypeBoss3.jpg)](https://ck.uesp.net/wiki/File:LocRefTypeBoss3.jpg)
    
    **Fig. 10.4:** BossContainer and BossTreasureMarker LocRefTypes.
    

Next we will place an XMarkerHeading for the **LocationCenterMarker** between the entrance and the boss. A good spot for this in Lokir's Tomb would be the second room. Make sure it is positioned on the generated Navmesh and set the LocRefType as **LocationCenterMarker**. An XMarkerHeading is different from a regular XMarker in that it also stores rotational data.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>XMarkerHeadings are often used when you want to specify not only the position, but also the direction something should be facing, such as an actor. They are commonly used by LocRefTypes, <a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Encounters#Linked-Refs_and_Patrols" title="Bethesda Tutorial Encounters">Patrol Paths</a>, and for positioning actors in <a href="https://ck.uesp.net/wiki/Scenes" title="Scenes">Scenes</a>.</td></tr></tbody></table>

We'll run through the rest of the interior LocRefTypes quickly. Set three Containers to the **Container** LocRefType; these can be anything from urns to chests, from dressers to barrels (_Fig. 10.5_). Next, lets place an XMarkerHeading down with the necromancer, making sure it is on the navmesh, and set it to the **CaptiveMarker** LocRefType (_Fig. 10.6_). Place another XMarkerHeading in the entrance room and mark it as **InsideEntranceMarker** (_Fig. 10.7_).

-   [![](https://ck.uesp.net/w/images/thumb/e/e4/LocRefTypeContainer.jpg/120px-LocRefTypeContainer.jpg)](https://ck.uesp.net/wiki/File:LocRefTypeContainer.jpg)
    
    **Fig. 10.5:** Placement of a Container LocRefType.
    
-   [![](https://ck.uesp.net/w/images/thumb/5/56/LocRefTypeCaptiveMarker.jpg/120px-LocRefTypeCaptiveMarker.jpg)](https://ck.uesp.net/wiki/File:LocRefTypeCaptiveMarker.jpg)
    
    **Fig. 10.6:** Placement of the CaptiveMarker LocRefType.
    
-   [![](https://ck.uesp.net/w/images/thumb/e/ee/LocRefInsideEntrance.jpg/120px-LocRefInsideEntrance.jpg)](https://ck.uesp.net/wiki/File:LocRefInsideEntrance.jpg)
    
    **Fig. 10.7:** Placement of the InsideEntrance LocRefType.
    

Now that you've placed those let's move to the exterior. The quickest way to do this is to double click on the **Yellow Door Marker** that we placed in the tutorial on [Bethesda Tutorial World Hookup](https://ck.uesp.net/wiki/Bethesda_Tutorial_World_Hookup "Bethesda Tutorial World Hookup"). This will bring up a dialogue box asking if we wish to move to the connected door on the other side of the teleport.

Now that we are in the exterior, make sure the Render Window is selected and press **B** to make sure that [Cell Borders](https://ck.uesp.net/w/index.php?title=Cell_Borders&action=edit&redlink=1 "Cell Borders (page does not exist)") are displayed. We should be in the cell we renamed "LokirsTombExterior" in the previous tutorial.

Here we will place our last three markers, each of them XMarkerHeadings. The first is going to be the **FriendMarker**, which we will place next to the Door Marker, facing away from the door. The second will be the **OutsideEntranceMarker**, other side of the Door Marker (_Fig. 10.8_). Finally, place the **LocationEdgeMarker** at the far edge of the cell, out of sight if there is a convenient tree (_Fig. 10.9_). All of these Markers MUST be in the LokirsTombExterior cell.

-   [![](https://ck.uesp.net/w/images/thumb/a/a6/LocRefTypeFriend.jpg/120px-LocRefTypeFriend.jpg)](https://ck.uesp.net/wiki/File:LocRefTypeFriend.jpg)
    
    **Fig. 10.8:** Placement of Friend and OutsideEntrance LocRefTypes
    
-   [![](https://ck.uesp.net/w/images/thumb/0/07/LocRefTypeLocEdge.jpg/120px-LocRefTypeLocEdge.jpg)](https://ck.uesp.net/wiki/File:LocRefTypeLocEdge.jpg)
    
    **Fig. 10.9:** Placement of the LocationEdge LocRefType.
    

## It's all about Location

A Location is the main way that Radiant Story uses to get everything it needs to create a quest. Locations can be found under **WorldData>Location**. Let's have a look at the BleakFallsBarrowLocation. On the left side of the panel we find several pieces of data.

-   **ID** - This is the ID used by the editor, this is never seen in game
-   **Name** - This is the written name used in game
-   **Parent Location** - This is Location that our location is a part of (usually the _Hold_)
-   **World Location Marker Ref** - This is used to set a marker to check the distance (Usually the [Map Marker](https://ck.uesp.net/wiki/Map_Marker "Map Marker"))
-   **Keywords** - This lets us tell the game what type of space it is.

There are a couple other pieces of data, but they aren't relevant to our needs right now. On the Right side of the window you will see three tabs marked _Location Ref Types, Cells, and Actors_. Once we have assigned a location to a cell, these will all be propagated automatically.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td><b>An Example of how Locations are used by Radiant Story</b><ul><li>NPC <i>Bob</i> wants to give you a quest to save his wife <i>Jane</i> from bandits and to kill their leader.</li><li>Radiant Quest finds a Location in the current Hold Location that has a Boss LocRefType and a CaptiveMarker LocRefType with the <i>LocTypeBanditCamp</i> Keyword</li><li><i>Jane</i> is moved to the XMarkerHeading with the <b>CaptiveMarker</b> LocRefType in this Location</li><li>Quest targets are placed for <i>Jane</i> and the actor with the <b>Boss</b> LocRefType in this Location</li></ul></td></tr></tbody></table>

We have all our Location RefTypes and are currently in the exterior cell, so let's go ahead and create a Location for Lokir's Tomb. With Location Selected in the Object Window Right-Click in the list of locations and choose New to create a New Location.

1.  Set the ID to "LokirsTombLocation"
2.  Set the Name to "Lokir's Tomb"
3.  Set the Parent Location to "WhiterunHoldLocation" (where our exterior cell is)
4.  Set the World Location Marker Ref to our Map Marker (choose in the Render Window)
5.  Right Click, then click **Add**, then add the following Keywords
    1.  **LocSetNordicRuin** - the main architecture here
    2.  **LocTypeDraugrCrypt** - what type of enemy is the boss
    3.  **LocTypeDungeon** - Simply, this is a dungeon
    4.  **LocTypeClearable** - This location can be marked "Cleared" on the map if all Boss LocRefTypes are dead
6.  Now hit "Ok"

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Smaller dungeons such as caves will often have all the animals marked with the "Boss" LocRefType. This way the cave is only cleared when all the animals are dead.</td></tr></tbody></table>

-   [![](https://ck.uesp.net/w/images/thumb/d/dc/LocationLokirsTomb.jpg/120px-LocationLokirsTomb.jpg)](https://ck.uesp.net/wiki/File:LocationLokirsTomb.jpg)
    
    Our new LokirsTombLocation.
    

-   [![](https://ck.uesp.net/w/images/thumb/e/e8/LocationBFB.jpg/120px-LocationBFB.jpg)](https://ck.uesp.net/wiki/File:LocationBFB.jpg)
    
    A view of the BleakFallsBarrowLocation.
    

We will go over assigning this location to cells after we create an Encounter Zone.

## Encounter Zones & Level scaling

An [Encounter Zone, or EncZone](https://ck.uesp.net/wiki/Encounter_Zone "Encounter Zone") as it is often written, is used to set the level scaling for an area. They can be found under **WorldData > Encounter Zone** in the object window. Let's have a look at the EncZone for Bleak Falls Barrow.

[![](https://ck.uesp.net/w/images/4/40/BFBZone.jpg)](https://ck.uesp.net/wiki/File:BFBZone.jpg)

A view of the BleakFallsBarrowZone.

_There are pieces of data here we are interested_

-   **ID** - The ID used by the editor
-   **Min Level** - The Minimum Level for this area
-   **Max Level** - The Maximum Level for this area (only needed if you want to cap how difficult the area is)
-   **Never Resets** - Sets this area not to reset after the 30 day reset period.
-   **Disable Combat Boundary** - Actors in combat with the player only follow the player through load doors that lead to the same encounter zone. With this box checked, actors in combat with the player will ignore this rule and follow the player into a different encounter zone.
-   **Location** - The location this EncZone is assigned to (see the **Location** Section of this tutorial)
-   **Analyze Loot** - Once the area is assigned this EncZone, this can be used to check how much loot you could pull at any given level
-   **Ownership** - Sets who owns everything in this area (Overridden if ownership is set on the reference)

The main points of data we are interested in are **Min Level**, **Max Level**, and **Location**. In Skyrim we scale the level to the player a bit differently than in previous games. Each space can have a Minimum and Maximum Level to which it will try to match the creatures. Once a location has been visited, however, that location is now locked at that level. The area will reset after 30 in game days at which point it will re-level to the player when they next visit. This allows us to have the game scale somewhat to the player's current abilities, while keeping areas you've recently visited feeling the same level of difficulty.

Here we've set up a new EncZone for LokirsTomb using the Min & Max parameters provided above.

[![](https://ck.uesp.net/w/images/5/58/EncZoneLokirsTomb.jpg)](https://ck.uesp.net/wiki/File:EncZoneLokirsTomb.jpg)

A view of the new LokirsTombZone.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>The difficulty of an area is still subject to the LvlActors used there. Even if you set Min Level of a Dwarven dungeon to "0", the lowest level creature in the LvlActor is still around level 12.<p>Likewise, the Max Level is often left to the default determined by the LvlActors present in the area.</p></td></tr></tbody></table>

## Hooking up the Location and Encounter Zone

We've finished creating our Location and EncZone, but so far they aren't attached to anything. These two pieces of data are set on the Cells for our area, through the Cell Properties Window. This can be found under **World>Cells...** in the top bar. However, the easier way of using it is to **Right-Click** on the Cell you want to set the properties for and select **Edit** from the options that appear. This is the same Window used during the [previous tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_World_Hookup "Bethesda Tutorial World Hookup") to set the name of our cell.

[![](https://ck.uesp.net/w/images/thumb/7/77/EditCell.jpg/300px-EditCell.jpg)](https://ck.uesp.net/wiki/File:EditCell.jpg)

Finding the Edit option in the Cell View.

## Exterior Cells

Let's start by editing the LokirsTombExterior cell, which will be found in the _Tamriel_. All we need to do here is set the Location to "**LokirsTombLocation**" and hit "**Apply**". It should look like this now.

[![](https://ck.uesp.net/w/images/thumb/c/c2/LokirCellExt1.jpg/300px-LokirCellExt1.jpg)](https://ck.uesp.net/wiki/File:LokirCellExt1.jpg)

Setting Location on LokirsTombExterior cell.

## Interior Cells

Next we will edit the Interior Cell, LokirsTomb either by changing the _World Space_ dropdown in the Cell Properties Window to " **Interiors**", which is located at the very top of the list. Then we can scroll down until we find the LokirsTomb Cell. Or locate it from Cell View window.

On the _Common Data_ tab we will set the _Location_ to "**LokirsTombLocation**".

[![](https://ck.uesp.net/w/images/thumb/3/34/LokirCellInt1.jpg/300px-LokirCellInt1.jpg)](https://ck.uesp.net/wiki/File:LokirCellInt1.jpg)

Setting Location on LokirsTomb cell.

In the _Interior Data_ tab, where we previously set the name, we will now set the _Encounter Zone_ to LokirsTombZone.

[![](https://ck.uesp.net/w/images/thumb/3/31/LokirCellInt02.jpg/300px-LokirCellInt02.jpg)](https://ck.uesp.net/wiki/File:LokirCellInt02.jpg)

Setting EncZone on LokirsTomb cell.

It's as simple as that. Now our Dungeon can be picked and used by Radiant Story for quests to take place here!

## Setting up Music and Audio Space

When you've run through the dungeon in game, you've probably noticed that it sounds very quiet. Let's go ahead and fix that while we are looking at the Cell Properties.

On the _Common Data_ tab, set _DefaultAcousticSpace_ to **IntDungeonCatacombsAcousticSpace**; this determines amount of echo in the space. Next set _Music Type_ to **MUSDungeon**; this will set the music to use the right queues for a dungeon. The Cell properties for LokirsTomb should now look like the image below.

[![](https://ck.uesp.net/w/images/thumb/c/c1/LokirCellInt03.jpg/300px-LokirCellInt03.jpg)](https://ck.uesp.net/wiki/File:LokirCellInt03.jpg)

Audio Settings on LokirsTomb cell.

We only need to set this for interior cells, so now our work is complete.