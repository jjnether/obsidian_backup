## Overview

This chapter will guide you through optimizing a dungeon to enhance performance. The reader will learn:

-   Tips for the best possible performance
-   The tools available for optimization
-   How to place room markers and portals

## What is Optimization?

Objects are often [rendered](https://ck.uesp.net/wiki/Glossary#Rendering "Glossary") in games when they don't need to be, wasting precious performance. For example, if the player is in a room with walls on all sides, the player cannot see anything outside of the walls. Objects behind these walls don't need to be rendered. By default, however, such objects may render. See _Fig 7.1_ for an example. While the need to cull such objects may seem obvious to us, game engines sometimes have a hard time making decisions about what needs to be drawn.

In order to help the game know to not render anything outside the walls, we have special tools available to us to optimize the room. Thanks to these tools the game can make better decisions about what to render and what to [cull](https://ck.uesp.net/wiki/Glossary#Culling "Glossary"). The tools we have available are **Portals**, **Room Markers**, [Multibounds](https://ck.uesp.net/w/index.php?title=Multibounds&action=edit&redlink=1 "Multibounds (page does not exist)"), and [Occlusion Planes](https://ck.uesp.net/w/index.php?title=Occlusion_Planes&action=edit&redlink=1 "Occlusion Planes (page does not exist)").

Manual optimization is not always necessary - some spaces are very simple and have very little to gain. Remember that a space that performs well on your machine may run very poorly on another with a different hardware configuration. This tutorial will try and give you some familiarity with best practices to make your mod run well on as many machines as possible.

## Build for Performance with Best Practices

There are a number of guidelines you can keep in mind throughout building to avoid performance problems. Paying attention to these best practices will make your dungeon much easier to optimize.

-   **Watch your object count**

Put simply, the object count is the number of "objects" rendered at a given time in the game. Some complex references may actually be made up of several objects, therefore the number of references is not actually a good indicator of your actual object count. Still, it's a good rule of thumb to keep the number of references down in a space for the sake of performance.

-   **Avoid Long Sight Lines**

Rendering depends largely on the player's line of sight, or how far the player can see before her view is blocked. The longer the line of sight in a space, the more objects the game needs to render. It doesn't matter if there is a door or a wall blocking the way, whatever is in that line will render. Manual optimization will help avoid the worst instances, but it's a good idea to avoid long sight-lines in the first place.

There is a line of sight issue in Lokir's Tomb that could potentially cause performance problems if left unchecked. From the entry room you can see into the next two rooms causing the game to render a lot of objects as seen in _Fig 7.2_.

We can fix this by adding a staircase to the large hallway section leading into the cave. This will elevate the entire cave area, helping us block line of sight. Because we have elevated an entire room, we'll have to adjust the [navmesh](https://ck.uesp.net/wiki/Navmesh "Navmesh") to match as well.

1.  Locate the "**NorHallBg1way01**" reference closest to the dungeon entrance.
2.  Ctrl+F to replace this with a "**NorHallBg1wayStairs256**" object
3.  Make sure Markers are toggled on (_"M" hotkey_)
4.  Adjust the dungeon and navmesh to snap with the new stair
5.  Check carefully for any seams introduced by the adjustment.

-   **Check the number of lights**

The number of lights in a space affects performance as well. Try not let any object be lit by more than two lights. You can get a feel for how many references a light affects by "**CTRL+I**" to toggle light markers on then toggling the "**L**" hotkey. You can also look for lighting issues in a space by right clicking in the render window and selecting "**Render Window Properties**". Go to the "**Shaders**" tab and check the box that says "**\# of lights**". _Fig 7.3_ shows an example space that has too many lights. The colors represent the number of lights hitting a each reference. Green represents an unlit piece and red means there are too many lights on a piece and performance issues are likely. It is good practice to make sure nothing shows up red when lighting your dungeon.

-   **Observe Framerate w/FRAPS**

FRAPS is a piece of software that allows you to capture video and screenshots in game, but it also shows the framerate as it is running. It is a good idea to run through your space with FRAPS running to check your framerate while trying to look in all directions. A good rule of thumb is to try and stay consistently above 30 frames per second. If your framerate dips at any point, there could be an object count issue in your field of view. Download FRAPS [here](http://www.fraps.com/).

-   [![](https://ck.uesp.net/w/images/thumb/2/25/OptimizationFig1.jpg/144px-OptimizationFig1.jpg)](https://ck.uesp.net/wiki/File:OptimizationFig1.jpg)
    
    **Fig. 7.1:** Without Manual Optimization, the Statue will render because it is within the player's yellow view cone, even though the player cannot actually see it.
    
-   [![](https://ck.uesp.net/w/images/thumb/e/e1/OptimizationFig2.jpg/194px-OptimizationFig2.jpg)](https://ck.uesp.net/wiki/File:OptimizationFig2.jpg)
    
    **Fig. 7.2:** Lokir's Tomb features a long, unbroken sight-line.
    
-   [![](https://ck.uesp.net/w/images/thumb/9/9e/OptimizationFig3.jpg/157px-OptimizationFig3.jpg)](https://ck.uesp.net/wiki/File:OptimizationFig3.jpg)
    
    **Fig. 7.3:** References with red/purple shading have too many lights hitting them.
    

## Room Markers and Portals

[![](https://ck.uesp.net/w/images/7/70/OcclusionDiagram.gif)](https://ck.uesp.net/wiki/File:OcclusionDiagram.gif)

**Fig. 7.4:** The black dot and blue cone represent the player position and view frustum. The shapes marked **A** and **B** represent room Markers, and the red lines **a** and **b** represent portals.

Room markers are simple shapes you can create which define an area as a room. Rooms, in essence, act as collectors. When culling, the renderer will treat everything inside another room as invisible, saving valuable processing power.

## Room Markers

A **Room Marker**, sometimes called a **Roombound**, is a box used to group objects together, allowing Creation Engine to render or cull them as a group. We could create a large room marker which surrounds a room, for example. By default, standing within this marker would look normal - but once you step out of it, every object encompassed by the room marker would be culled, and become invisible.

The boxes "A" and "B" in _Fig 7.4_ represent two Room Markers. The black dot is the player, and the shaded triangle illustrates the player's field of vision. With just those room markers, the player would only see the references contained within room "A". Thanks to portals, however, we can create logical links between room Markers.

## Portals

A portal is a sort of doorway from one Room Marker to another. Without portals, the player in _Fig 7.4_ will see any reference contained within Room "A", but nothing within Room "B". There are two portals in that diagram, however: portal "**a**" and portal "**b**".

Because the player's view [frustum](https://ck.uesp.net/wiki/Glossary#Frustum "Glossary") includes some or all of "a", the contents of both "A" and "B" will be rendered. (_Assuming that "a" is linked to both "A" and "B", of course. More on that later._)

Note that the player cannot see any part of portal "b". This means that any Room connected to that portal (none are pictured) will be culled.

## Optimization Workflow

Manual optimization with Room Markers and Portals can be difficult thing to understand. Let's go through the process with Lokir's Tomb to see it in action.

## Step 1: Creating Room Markers
Before we begin, there are a couple quick set-up steps:

1.  Break the long sight-line as mentioned above if you haven't already (_Fig 7.2_)
2.  Toggle Snap-to-Grid On (_Q hotkey or [![Buttongridsnapping.jpg](https://ck.uesp.net/w/images/6/63/Buttongridsnapping.jpg)](https://ck.uesp.net/wiki/File:Buttongridsnapping.jpg))_
3.  On the main toolbar, click: **View > Show/Hide Window**
4.  Check "**Portals and Rooms**". _NOTE: "Light Markers" must be checked as well_

Lokirs Tomb is basically made up of five distinct areas. We'll use a room marker to define each of these areas in a way the Creation Engine can easily understand. We'll begin with the first room, and then repeat to create the rest.

1.  Ctrl+click to select wall pieces from each side of the room
2.  Click the "_Create a Roombound_" button on the Main Toolbar: [![Toolbar Button Cubic Room.jpg](https://ck.uesp.net/w/images/2/23/Toolbar_Button_Cubic_Room.jpg)](https://ck.uesp.net/wiki/File:Toolbar_Button_Cubic_Room.jpg)
3.  Note that our new Room Marker encompasses all the objects in our selection.
4.  Manually Scale your new Room Marker to include any stray pieces, as in _Fig 7.5b_.
5.  Repeat this process to create a total of five rooms, as seen in _Fig 7.5c-e_.
    1.  Optionally, you can duplicate and scale your existing Room Marker by hand. It's up to you, as long as you achieve the same result.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>It's possible to go overboard here. Each Portal the camera frustum hits involves a calculation cost, meaning that too many Rooms/Portals can actually cause a space to run slower than without them. It's a good rule of thumb to avoid situations where the line-of-sight will penetrate more than 3-5 portals.</td></tr></tbody></table>

Some of your rooms may overlap or be separated by small gaps, as in _Fig 7.5d_, depending on how you created them. You can use non-uniform scaling (covered in an [earlier tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Traps_and_Prefabs#Triggering_an_Ambush "Bethesda Tutorial Traps and Prefabs")) to minimize these errors. Strive to line Rooms up at the most narrow possible points, such as doorways. Further information on working with primitives can be found [here](https://ck.uesp.net/wiki/Creating_Primitives "Creating Primitives"). The Creation Kit will attempt to correct minor errors when we link these rooms together later, but it's best to strive for good snapping now, as in _Fig 7.5e_.

Try running the game now. You'll notice that things don't look right; each room renders on its own while the player is within. You'll see gaps to the void anywhere another Room Marker begins. We'll install portals in the next step, which will allow the Creation Engine to render multiple Rooms at once.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>Perfectly aligned room edges are important, or you can end up with very small overlapping areas and/or gaps in which the game will not render correctly. These are notoriously difficult to find and debug, but can usually be avoided by good snapping habits at this stage.</td></tr></tbody></table>

-   [![](https://ck.uesp.net/w/images/thumb/8/85/InitialRoomMarker.jpg/120px-InitialRoomMarker.jpg)](https://ck.uesp.net/wiki/File:InitialRoomMarker.jpg)
    
    **Fig 7.5a**: Room marker created by selecting walls at each side of the entry room.
    
-   [![](https://ck.uesp.net/w/images/thumb/c/ce/InitialRoomMarkerResized.jpg/120px-InitialRoomMarkerResized.jpg)](https://ck.uesp.net/wiki/File:InitialRoomMarkerResized.jpg)
    
    **Fig 7.5b**: The room marker re-sized to contain the entire entry room.
    
-   [![](https://ck.uesp.net/w/images/thumb/5/53/LokirsTombRoomMarkers.jpg/120px-LokirsTombRoomMarkers.jpg)](https://ck.uesp.net/wiki/File:LokirsTombRoomMarkers.jpg)
    
    **Fig 7.5c**: Room markers containing each room of the dungeon.
    
-   [![](https://ck.uesp.net/w/images/thumb/2/2e/RoomMarkerGap.jpg/120px-RoomMarkerGap.jpg)](https://ck.uesp.net/wiki/File:RoomMarkerGap.jpg)
    
    **Fig 7.5d**: A gap between two room markers in orthographic top down view.
    
-   [![](https://ck.uesp.net/w/images/thumb/5/56/RoomMarkersNoGaps.jpg/120px-RoomMarkersNoGaps.jpg)](https://ck.uesp.net/wiki/File:RoomMarkersNoGaps.jpg)
    
    **Fig 7.5e**: All room markers lined up perfectly in orthographic top down view.
    

## Step 2: Thinking With Portals

We'll create portals everywhere that a) two Room Markers meet and b) the player should be able to see from one room to the next. You can think of them as a sort of user-defined window. Try creating a portal now:

1.  Select the Room Marker encompassing the first room. Be sure nothing else is selected.
2.  Position the camera within the room.
3.  Look through the doorway, similar to a first-person view, as in _Fig 7.6a_.
4.  Enter "**Portal Mode**" by pressing [![Jb MainPortalMode.jpg](https://ck.uesp.net/w/images/4/4e/Jb_MainPortalMode.jpg)](https://ck.uesp.net/wiki/File:Jb_MainPortalMode.jpg) or the **Ctrl+P** hotkey.
    1.  _NOTE: While in portal mode, only portals can be selected._
5.  Click the "**Create Portal**" button in the Main Toolbar: [![Jb MainPortal.jpg](https://ck.uesp.net/w/images/b/b0/Jb_MainPortal.jpg)](https://ck.uesp.net/wiki/File:Jb_MainPortal.jpg)
6.  Click on the visible blue surface within the doorway
7.  A dark shape, flush with the edge of your room, will have been created. This is your portal.
    1.  _Sometimes the portal will not be created on the correct edge of the room. If this happens, press shift+F to focus the camera on the newly-created portal, then rotate/position it approximately where the two rooms meet. It will be snapped precisely when we join it with the second room, which we'll do shortly._
8.  Use the scale gizmo to adjust the shape of the portal. It should be as small as possible while completely filling the visible space at the intersection. (_Fig 7.6b_)

Your portal is positioned correctly, but it's only linked to one of the two rooms. You'll need to link it to the second room before it will work properly.

1.  **Keeping the portal selected**, exit Portal Mode. ( _[![Jb MainPortalMode.jpg](https://ck.uesp.net/w/images/4/4e/Jb_MainPortalMode.jpg)](https://ck.uesp.net/wiki/File:Jb_MainPortalMode.jpg) or **Ctrl+P**_)
2.  Ctrl+Click to **select the second Room Marker**.
3.  You should now have **two objects selected**: the portal and the unlinked second room.
4.  Click the "**Link Portal To Room**" button: [![Jb MainPortalLink.jpg](https://ck.uesp.net/w/images/b/b3/Jb_MainPortalLink.jpg)](https://ck.uesp.net/wiki/File:Jb_MainPortalLink.jpg)

Note the white arrow now drawn from the portal to the center of the newly-linked room. (_Fig 7.6c_) This visual representation is a good way to spot-check connections in a space. You may also notice a slight change in the scale/position of Room Marker #2. The Linking process will ensure the Room edges and Portal are co-planar, which sometimes corrects small errors. It's still best to try and make sure your rooms are properly snapped ahead of time, however. These auto-adjustments can become problematic when you're working with a room with multiple portals; a correction on one side of the room may create a gap on the other - so it's best not to rely upon them entirely.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>If you're having trouble selecting a portal, simply go into Portal Mode by selecting a Room Marker and pressing "CTRL+P" or <a href="https://ck.uesp.net/wiki/File:Jb_MainPortalMode.jpg"><img alt="Jb MainPortalMode.jpg" src="https://ck.uesp.net/w/images/4/4e/Jb_MainPortalMode.jpg" decoding="async" width="23" height="21"></a>, and select your portal. When in Portal Mode, you can only select portals. This comes in handy when you have a lot of references blocking your view.<p>Keep this in mind if you ever find yourself unable to select anything in the editor - you may have accidentally entered portal mode!</p></td></tr></tbody></table>

-   [![](https://ck.uesp.net/w/images/thumb/b/b6/RoomMarkerBorder.jpg/280px-RoomMarkerBorder.jpg)](https://ck.uesp.net/wiki/File:RoomMarkerBorder.jpg)
    
    **Fig 7.6a**: The border between two room markers where we want to create our portal.
    
-   [![](https://ck.uesp.net/w/images/thumb/3/3d/SizedPortal.jpg/272px-SizedPortal.jpg)](https://ck.uesp.net/wiki/File:SizedPortal.jpg)
    
    **Fig 7.6b**: The portal placed at the border and sized to cover the entire connecting area.
    
-   [![](https://ck.uesp.net/w/images/thumb/f/fa/ConnectedPortal.jpg/270px-ConnectedPortal.jpg)](https://ck.uesp.net/wiki/File:ConnectedPortal.jpg)
    
    **Fig 7.6c**: Two rooms linked to a co-planar portal. Note the white arrows.
    

## Step 3: Finishing the Optimization Pass

With Room Markers in place, continue adding portals throughout LokirsTomb until every room is linked. This layout is relatively straightforward, and most problems can be diagnosed by simply running the space in-game and looking for areas where some or all of the objects you'd expect to see pop out of existence, usually because of a gap or overlap where two Room Markers meet.

Once your level is optimized for maximum performance, you're ready to move on to lighting and FX!