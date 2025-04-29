## Overview

This chapter will guide you through connecting your dungeon to the outside world.

The reader will learn:

-   How to, very basically, navigate a Worldspace
-   How to create a load door
-   Learn how to name your cell and place a mapmarker.

## Connecting your dungeon to Skyrim

## Finding a good place to put your dungeon.

[![](https://ck.uesp.net/w/images/thumb/8/8e/CellViewTamrielWorldspace.jpg/300px-CellViewTamrielWorldspace.jpg)](https://ck.uesp.net/wiki/File:CellViewTamrielWorldspace.jpg)

Cell View window with the Tamriel worldspace selected and 3, -11 coordinates in place.

In the **Cell View** window select "**Tamriel**" from the **World Space** drop-down, or just select the drop-down and hit the **T** key. Give it a second to load. Once it's finished loading check the **Loaded at top** checkbox (makes sure that currently loaded cells filter to the top of the cell list) and then type "**3**" in the **X** box and "**\-11**" in the **Y** box, then click the **Go** button.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>You "may" need to press <b>F5</b> to load the render window if it looks like everything didn't load in correctly. This can sometimes happen in both Interior and Exterior cells. You will also need to press <b>F5</b> to load cells in the exterior if you want to explore around in the editor.</td></tr></tbody></table>

  
Your **Render Window** will then load the cell at those coordinates, which is just across the river from Riverwood. Once it's done loading you will notice that a cell named **Wilderness** is now highlighted with a dull grey color in the **Cell View** window's cell list, most likely just below the **SnowFX** cell. Verify this is the correct cell by checking that its coordinates are indeed **3, -11**. You may need to scroll the list to the right some just to be sure. If it is, then select the cell in the list, hit **F2** to rename the cell and change it's name to "**LokirsTombExterior**" since this is where we will put our dungeon entrance.

[![](https://ck.uesp.net/w/images/thumb/1/1c/LokirsTombExterior.jpg/300px-LokirsTombExterior.jpg)](https://ck.uesp.net/wiki/File:LokirsTombExterior.jpg)

Now use the pieces **NorDwelling02ExtBaseC**, **NorDwelling02ExtBaseB** and a **NorDoorSmLoad02** to create an entrance that looks like the image to the left.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>As of Creation Kit version 1.4.23.0 there is a bug where larger Objects might sometimes not appear in game. A temporarly solution is to open the objects reference window and enable <b>Is Full LOD</b>, although this is not recommended as a permanent solution, as it may affect performance.</td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>If the textures on some objects are flickering, especially the ones on the "<b>NorDwelling...</b>" pieces you should be able to fix it by setting "<b>View &gt; Depth Biasing</b>" on.</td></tr></tbody></table>

## Creating a Load Door

[![](https://ck.uesp.net/w/images/thumb/e/e4/IntExtDoorTeleportMarkers.jpg/300px-IntExtDoorTeleportMarkers.jpg)](https://ck.uesp.net/wiki/File:IntExtDoorTeleportMarkers.jpg)

Interior/Exterior Door Teleport Markers in the correct position.

To create a load door just double click on the **NorDoorSmLoad02** in the exterior and check the **Teleport** checkbox. Now, with the **Reference** window still open for the **NorDoorSmLoad02** go back to your **LokirsTomb** cell by selecting "**Interiors**" from the **World Space** drop-down in the **Cell View** window and double-click on the "**LokirsTomb**" cell, and let it load. Once loaded click on the "**Select Reference in Render Window**" button just underneath the **Teleport** checkbox you checked earlier and then double-click on the **NorDoorSmLoad01** which is interior entrance of your dungeon.

Now that the doors are connected if you activate either one in-game you will teleport to the other. But wait, you're not done yet! Notice the yellow teleport marker that was created when you connected the doors? This is where you will start when entering the level from the connected door. For the interior teleport marker move it so it's roughly in the same position, and direction, as the blue COC marker (COCMarkerHeading). Then double click the teleport marker to easily move to **LokirsTombExterior** and re-position that teleport marker so it's just outside the door, facing away from it. When you're done the teleport markers should look like the picture to the right.

The last thing to do before you're finished with the teleport doors is to Finalize the Navmesh of both the interior and exterior cells. To do this for the interior cell just press **Ctrl+E** or click the Navmesh Button [![EnableNavmeshButton.jpg](https://ck.uesp.net/w/images/2/29/EnableNavmeshButton.jpg)](https://ck.uesp.net/wiki/File:EnableNavmeshButton.jpg) and then Finalize the navmesh by pressing **Ctrl+ 1** or clicking the Finalize Button[![FinalizeNavmeshButton.jpg](https://ck.uesp.net/w/images/e/e8/FinalizeNavmeshButton.jpg)](https://ck.uesp.net/wiki/File:FinalizeNavmeshButton.jpg). A navmesh triangle under the yellow Teleport Marker will turn green after finalization. To do the exterior cell you go through the same process, except make sure your camera is inside the cell you are trying to Finalize the Navmesh in. Hit the **B** key while in an exterior cell to Toggle Cell Borders on/off.

If you're feeling brave you can tweak the navmesh in this exterior cell to better fit the static references we've added, but it's not entirely necessary since what you've added here doesn't affect the navmesh much. Navmeshing in the exterior has its own quirks that are probably best avoided until you get to the [Intermediate Landscaping](https://ck.uesp.net/w/index.php?title=Intermediate_Landscaping&action=edit&redlink=1 "Intermediate Landscaping (page does not exist)") tutorial. Still, if you do edit the navmesh in this exterior cell be sure to finalize when you are done to ensure connection to the teleport door, and to nearby cells (a green line on the cell border shows whether it's connected correctly or not).

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>When you Finalize the navmesh a link gets created between connected doors, as well as cell borders in the exterior. This helps the game find out how to get from one place to another. This makes it possible for NPCs to navigate around the world, and also affects how Quest Markers display.</td></tr></tbody></table>

## Naming your cell and placing a Map Marker

[![](https://ck.uesp.net/w/images/thumb/e/e6/LokirsTombMapMarker.jpg/300px-LokirsTombMapMarker.jpg)](https://ck.uesp.net/wiki/File:LokirsTombMapMarker.jpg)

Map Marker placed and Link-Ref'd to an XMarkerHeading for better Fast Travel Placement of the player.

The last thing you want to do is name your cell, and place a [Map Marker](https://ck.uesp.net/wiki/Map_Marker "Map Marker") so the player can discover it on a subsequent visit to the location.

To name the cell just right click on your cell in the **Interiors** cell list in the **Cell View** window and click **Edit**. Click the **Interior Data** tab and then type "**Lokir's Tomb**" in the **Name** text box. Click **OK** and your dungeon will now have a name while in game.

You will probably also want to place a **MapMarker** in your exterior so it looks somewhat like the picture to the left. Then double-click the **MapMarker** in the exterior, click the **Marker Data** tab, check the **Marker Data** checkbox and set the **Name** to "**Lokir's Tomb**" and the **Type** to "**Nordic Ruin**". Now when the player enters the yellow radius surrounding the MapMarker he will have discovered this dungeon, and whenever he Fast Travels here he will spawn exactly where the MapMarker's center is. If you want the player to appear in a different position than the center of the MapMarker just Link-Ref the MapMarker to an **XMarkerHeading**, just like in the picture to the left.

Now you have a dungeon exterior that the player can discover, fast travel to, and most importantly, access your dungeon.