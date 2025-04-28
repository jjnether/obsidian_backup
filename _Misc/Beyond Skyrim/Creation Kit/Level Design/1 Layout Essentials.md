## Overview

This chapter will guide you through the basics of creating a layout for an interior space using the "Ancient Nord Ruin" art.

The reader will learn:

-   What "kits" are and how to use them
-   How to find kit pieces in the Object Window
-   Kit piece naming conventions
-   How to place and fit kit pieces together
-   How to test a custom dungeon in game

## Kits

The majority of spaces in Skyrim are created using "kits". These kits are composed of pieces of environment art designed to be used together to create a wide variety of spaces, and are instrumental to our ability to create the large number of areas in the game with the flexibility to keep things fresh and experiment with gameplay, while minimizing the amount of custom art that needs to be created.

One heavily used kit in Skyrim is the "Ancient Nord Ruin" kit. Because most players will be very familiar with the kit, we'll be using it for the first phase of our layout in this tutorial. Some other examples of the kits available are the Cave Kit and the Imperial Fort Kit.

## Finding Kit Pieces in the Object Window

To make the standard kits available, first click on the load button [![Jbrowne IconLoad.jpeg](https://ck.uesp.net/w/images/e/e3/Jbrowne_IconLoad.jpeg)](https://ck.uesp.net/wiki/File:Jbrowne_IconLoad.jpeg) on the toolbar at the top of the creation kit window, double-click the checkbox in front of "Skyrim.esm" to make sure it is selected, and click OK. Answer "yes to all" for any errors that pop up during this process.

To view categories of kits in the object window, expand the ‘World Objects’ category on the left side of the Object Window. From there, expand the **"STATIC > Dungeons"** categories. Several kit types are available. For the purposes of this tutorial we will be using the **"Nordic"** category. You can browse through this category to see the different sub kits and pieces that are available for use in this kit. For now, choose the **"SmRooms"** sub-kit.

You can use the **[Preview Window](https://ck.uesp.net/wiki/Preview_Window "Preview Window")** to preview objects by right clicking an object in the object window and selecting "preview". A window will pop up showing the object. This window automatically updates to show whatever object you select in the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window"), so it can be handy to keep up for browsing the art. Unfortunately, the camera controls for the Preview Window are a markedly different and simplified subset of those in the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window"), and these differences can take some getting used to.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Kits are very robust, and the large number of pieces at your disposal can be overwhelming at first. Stick with it! Just knowing your way around the kit is a huge part of being able to effectively work with it, and this will take some time and experimentation on your part. Give yourself a generous amount of time for this before moving on. Try not to get frustrated at slow progress right now!</td></tr></tbody></table>

## Kit Naming Conventions
[![](https://ck.uesp.net/w/images/thumb/6/6e/PreviewWindow01.jpg/300px-PreviewWindow01.jpg)](https://ck.uesp.net/wiki/File:PreviewWindow01.jpg)

Fig.1: The Preview Window

Let's examine the name of a piece of this sub-kit: **NorRmSmWallSideExSm01**. The name is a sort of code - it may not make much sense at first, but once you understand the naming convention it tells you everything about the piece at a glance.

Let's break down this name and examine the meaning of each component.

<table><tbody><tr><td><b>Nor</b></td><td>Short for "Nord" - this lets us know it's part of the Nord Ruins kit</td></tr><tr><td><b>Rm</b></td><td>Stands for "room", the sub-kit this piece is a member of. For example, a piece beginning with NorHall would be part of the Nord Hall sub-kit.</td></tr><tr><td><b>Sm</b></td><td>This stands for "small". The Nordic Room kit uses "Sm" for small rooms and "Bg" for big rooms.</td></tr><tr><td><b>Wall</b></td><td>Fairly self-explanatory: this is a wall. Pieces in this kit are wall, mid, or cor (for corner) pieces.</td></tr><tr><td><b>Cor</b></td><td>Corner pieces. Designated as CorIn (inside corner) or CorOut (Outside corner.)</td></tr><tr><td><b>Side</b></td><td>Pieces in the Nordic Small room kit fit together as either "Front" or "Side" More on this later.</td></tr><tr><td><b>Ex</b></td><td>Denotes an exit/doorway piece. This will snap nicely with doors and matching "Ex" doorways within the same kit.</td></tr><tr><td><b>Sm</b></td><td>Denotes the size of the exit/doorway piece. The Nordic Room kit uses "Sm" for small exits and "Bg" for big exits. Only matching sizes will fit together.</td></tr><tr><td><b>01</b></td><td>The number suffix usually means that a piece has multiple variations. The number increments to identify each variation the piece has.</td></tr></tbody></table>

You are able to search for the pieces you need by typing any of these parts into the Object Window filter. For example, if you want to view all of the Nordic Small Room pieces, type _"NorRmSm"_ into the filter. The search will turn up results based on the category selected on the left side of the object window.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>Once you've learned the naming convention, you can use the asterisk "(*)" to serve as a wildcard when searching for pieces in the Object Window. For example, if you are searching for all possible exits from a Nordic Small Room, just enter <b>"NorRmSm*Ex"</b> into the Object Window Filter. Each possible exit piece for the Nordic Small Room kit will appear. <a rel="nofollow" href="http://en.wikipedia.org/wiki/Wildcard_character">More about wildcards at Wikipedia</a></td></tr></tbody></table>

## Building a Room

You are now equipped with all the information you need to create an actual, playable space. We'll go slowly through the first handful of steps. Once you've learned the fundamentals, you'll be able to create a full layout using the Nordic Ruins kit at your own pace.  

## Step 1: Creating A Cell

Before we can do anything else, we need to create a space to work in. You do this by clicking on **World > Cells**, then in the **Cell Info window** you right click any cell and select **New** and type in the **Cell EditorID** you want for your cell. We'll call this dungeon **LokirsTomb**. Click **Ok** to close the **Cell Info Window**. Now we need to find **LokirsTomb** in the **Cell View window**. You can either scroll down till you find it, or you can check the box **Show only active (\*) cells** (you'll then only see edited cells) or check the box **Loaded at top** (edited cells are at the top in the **Cell View window**).

Now that you have your own interior cell to work with, be sure to select the LokirsTomb cell.

Right click on the **LokirsTomb** Cell and pick "View" to assign it to the render window.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>It's important to be 100% sure of what cell you have loaded before doing any editing. There are two places to check this: the title bar of the <a href="https://ck.uesp.net/wiki/Render_Window" title="Render Window">Render Window</a>, and the area above the filter box in the <a href="https://ck.uesp.net/wiki/Cell_View" title="Cell View">Cell View</a> window both show the name of the currently-loaded cell</td></tr></tbody></table>

## Step 2: Placing Your First Piece

Let's get started by placing our first piece. Take a look at your [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window") and expand: "**World Objects > STATIC > Dungeons > Nordic**" You'll notice several sub-kits here, but for now we're just concerned with the Small Room, or "_SmRooms_" sub-kit. Expand that sub-kit now, and the list on the right-hand side of your Object Window will populate with a number of pieces beginning with "NorRmSm".

Now that we have the sub-kit loaded and ready to go, select "**NorRmSmWallSide01**" and place it into your cell by dragging and releasing it over the Render Window. You may or may not see the object appear. In either case, right-click on the newly-created reference ID in your Cell View Window. Choose "**Edit**". As seen in [Fig 2](https://ck.uesp.net/wiki/File:SettingToOrigin01.jpg "File:SettingToOrigin01.jpg"), change the XYZ Position coordinates to 0,0,0, and click OK.

Double-click the ref ID in the [Cell View](https://ck.uesp.net/wiki/Cell_View "Cell View") to manually focus the Render Window camera on it, and you should see a piece of floor floating in space. Double-clicking the object also made this object the current selection, so you can use [your camera controls](https://ck.uesp.net/wiki/Bethesda_Tutorial_Creation_Kit_Interface#Controlling_the_Camera "Bethesda Tutorial Creation Kit Interface") to get a good look at it.

## Working on the Grid

Before going any further, it's important to understand "**the Grid**", and **"Snapping"** to it.

When we work in the Render Window, we are actually within an invisible, three-dimensional [Cartesian Grid](http://en.wikipedia.org/wiki/Cartesian_coordinate_system#Cartesian_coordinates_in_three_dimensions). The center of this grid, at XYZ coordinates (0,0,0), is referred to as the **"Origin"** - which is where we manually placed _NorRmSmWallSide01_ only moments ago. [See Fig. 2](https://ck.uesp.net/wiki/File:SettingToOrigin01.jpg "File:SettingToOrigin01.jpg")

You don't always need to be aware of the grid. When placing an enemy, rotating a treasure chest, or adjusting the position of a light, for example, precision isn't important. The Grid is critical when working with kits, however. Kit pieces are designed to "snap" to each other precisely, and the Grid is the only way to get this precision. "Eyeballing" kit pieces will always leave gaps and seams.

Everything in the Creation Kit is measured in **["Units"](https://ck.uesp.net/wiki/Unit "Unit")**. These units don't correspond to any real-world units of measurement, but [Fig. 3](https://ck.uesp.net/wiki/File:UnitScaleRef.jpg "File:UnitScaleRef.jpg") should give you an idea of how they scale against our kit and some characters.

The Nordic Ruin works well on a 128-unit grid. To set this up, either right-click anywhere in the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window") and choose **"Render Window Properties"**, or click this button in the [Main Toolbar](https://ck.uesp.net/wiki/Main_Toolbar "Main Toolbar"): [![ButtonRenderWindowPrefs.jpg](https://ck.uesp.net/w/images/f/f0/ButtonRenderWindowPrefs.jpg)](https://ck.uesp.net/wiki/File:ButtonRenderWindowPrefs.jpg). This will cause the dialog in [Fig. 4](https://ck.uesp.net/wiki/File:MovementTab01.jpg "File:MovementTab01.jpg") to appear. Choose the **"Movement Tab"** if it is not already visible. There are several options in here, but for the moment we just want to make sure that **"Snap To Grid"** is set to 128, and **"Snap To Angle"** is 45. Click Apply to save your settings and dismiss the dialog.

Returning to the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window"), make sure that snap-to-grid is toggled on. This is controlled with the **"Q"** hotkey or this button: [![Buttongridsnapping.jpg](https://ck.uesp.net/w/images/6/63/Buttongridsnapping.jpg)](https://ck.uesp.net/wiki/File:Buttongridsnapping.jpg). Likewise, snap-to-angle should be enabled. This is toggled with **"Ctrl+Q"** or [![ButtonAnglesnapping.jpg](https://ck.uesp.net/w/images/b/b2/ButtonAnglesnapping.jpg)](https://ck.uesp.net/wiki/File:ButtonAnglesnapping.jpg).

-   [![](https://ck.uesp.net/w/images/thumb/f/f3/SettingToOrigin01.jpg/99px-SettingToOrigin01.jpg)](https://ck.uesp.net/wiki/File:SettingToOrigin01.jpg)
    
    **Fig. 2**:  
    Manually placing our first piece at the origin.
    
-   [![](https://ck.uesp.net/w/images/thumb/d/d1/UnitScaleRef.jpg/120px-UnitScaleRef.jpg)](https://ck.uesp.net/wiki/File:UnitScaleRef.jpg)
    
    **Fig. 3**:  
    Some reference markings for unit scale
    
-   [![](https://ck.uesp.net/w/images/thumb/6/6c/MovementTab01.jpg/87px-MovementTab01.jpg)](https://ck.uesp.net/wiki/File:MovementTab01.jpg)
    
    **Fig. 4**:  
    Preferences: Movement Tab
    

## Step 3: Fitting the Pieces Together

Select your _NorRmSmWallSide01_ piece we placed before. Use **"ctrl+D"** to create a duplicate piece. This will place a new _NorRmSmWallSide01_ reference directly on top of the pre-existing one. Note that the duplicated object is automatically selected for you.

Click and drag on the object inside the Render Window to move the newly-created wall piece. With grid-snapping turned on, it will lock into place relatively easily.

Two walls is hardly a room; we need corners! Return your attention to the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window") and search for "**NorRmSmCorIn01**", then drag it into the render window. [Rotate the piece](https://ck.uesp.net/wiki/Creation_Kit_Interface_Cheat_Sheet "Creation Kit Interface Cheat Sheet") into the correct orientation to line up with one of your walls and drag it into place. [See Fig. 5.](https://ck.uesp.net/wiki/File:FittingPieces01.jpg "File:FittingPieces01.jpg") Remember to have your angle-snapping turned on and locked at 45 degrees.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td>When dragging new references to the Render Window, they will be placed with their pivot point wherever your cursor is when you release the left mouse button. This makes it easy to quickly create new pieces at the correct floor height. If you release over the void, the object will be placed at the camera.</td></tr></tbody></table>

Some kits have a "flow", which means that pieces have to be configured in a specific way for aesthetic reasons. For example, in this kit, walls are either **"side"** or **"front"** types. The two walls you've placed are _side_ walls, as denoted in the name of the piece. Any perpendicular walls must therefore be of the _front_ type. In this case, it's because of ceiling details that flow the length of the room, and using the pieces incorrectly can create large gaps in the ceiling.

In the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window"), find "**NorRmSmWallFront01**" and drag it into the Render Window. If needed, Rotate the piece to line it up with one of the corner pieces. Complete the outer walls with two additional "_NorRmSmWallFront01_" pieces. You can then finish the room's walls using corners and the same amount of "_NorRmSmWallFront01_" and "_NorRmSmWallSide01_" pieces on each side.

The room is nearly complete - except for the gaping hole in the center.[See Fig. 6.](https://ck.uesp.net/wiki/File:LevelShell01.jpg "File:LevelShell01.jpg") Place a **NorRmSmMid01** piece, which can be snapped into the gap. Duplicate the mid piece and keep snapping until the hole is filled. There's something you have to check at this point: this piece also has specific flow, so rotation is important, even though it may not appear to be at first glance.

To check the ceiling flow, [rotate the camera](https://ck.uesp.net/wiki/Creation_Kit_Interface_Cheat_Sheet "Creation Kit Interface Cheat Sheet") so you're looking at the ceiling. Notice the linear pattern in the pieces. Rotate the mid pieces individually where necessary to connect the pattern to the walls. [See Fig. 7](https://ck.uesp.net/wiki/File:WrongRotation01.jpg "File:WrongRotation01.jpg") for the correct configuration.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>Rotating the camera to look up can be disorienting, especially if you are new to the Creation Kit or working in 3D. Be patient and use Shift+F to re-focus the camera and start over if you end up looking into the void.</td></tr></tbody></table>

-   [![](https://ck.uesp.net/w/images/thumb/9/9b/FittingPieces01.jpg/120px-FittingPieces01.jpg)](https://ck.uesp.net/wiki/File:FittingPieces01.jpg)
    
    **Fig. 5**:  
    NorRmSmCorIn01 lined up with NorRmSmWallSide01.
    
-   [![](https://ck.uesp.net/w/images/thumb/b/b9/LevelShell01.jpg/120px-LevelShell01.jpg)](https://ck.uesp.net/wiki/File:LevelShell01.jpg)
    
    **Fig. 6**:  
    The outer edges of your room.
    
-   [![](https://ck.uesp.net/w/images/thumb/c/c3/WrongRotation01.jpg/120px-WrongRotation01.jpg)](https://ck.uesp.net/wiki/File:WrongRotation01.jpg)
    
    **Fig. 7**:  
    The NorRmSmMid01 piece placed incorrectly, notice the gap. On the right the piece is in the correct configuration.
    

## Step 4: Connecting Rooms and Finishing Layout

We've completed a room with walls, a ceiling, and a floor - but no way out. Time to add a door. Delete one of the **NorRmSmWallFront01** pieces by selecting it in the render window and pressing "delete". In the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window"), search for **NorRmSmWallFrontExSm01** and drag it into the render window. Remember to preserve front/side consistency. Since this exit is on a "front" wall, use a "front" exit piece.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Not sure what object you have selected? The <a href="https://ck.uesp.net/wiki/Main_Toolbar" title="Main Toolbar">Main Toolbar</a> displays this in its lower-left corner. If you have multiple objects selected, it displays the most recently selected object name and "+X more" to give you an idea how large your total selection is. Your current selection is also highlighted in the <a href="https://ck.uesp.net/wiki/Cell_View_Window" title="Cell View Window">Cell View Window</a></td></tr></tbody></table>

Try creating a hallway connected to the new doorway. In the object window search for **NorHallSm1WayEndExSm01**. Make sure your [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window") is opened to **WorldObjects>Static>Dungeons>Nordic>SmHalls**. Note the _ExSm_ suffix, shorthand for "Exit Small". This lets us know it will snap with any other _ExSm_ piece in the Nordic kit. Be sure grid-snapping is still on and snap the pieces together.

You now know everything you need complete the first layout pass for this dungeon. Try using the image below to do so now. If you get stuck, try downloading the [example plugin](https://ck.uesp.net/w/index.php?title=Special:Upload&wpDestFile=LDLayoutPart1TutorialComplete.esp "LDLayoutPart1TutorialComplete.esp") to see the layout completed.

-   [![](https://ck.uesp.net/w/images/thumb/8/8f/Final01.jpg/120px-Final01.jpg)](https://ck.uesp.net/wiki/File:Final01.jpg)
    
    **Fig. 1**:  
    The completed layout map.
    
-   [![](https://ck.uesp.net/w/images/thumb/7/74/Final02.jpg/120px-Final02.jpg)](https://ck.uesp.net/wiki/File:Final02.jpg)
    
    **Fig. 2**:  
    Completed layout with labels
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>When loading example plugins, remember <b>not</b> to load your plugin to avoid conflicts caused by having two cells with the same name.</td></tr></tbody></table>

## Step 5: Checking It Out In the Game

As you work, it's a good idea to frequently test your work in-game. For a refresher on loading your plugin, [check here](https://ck.uesp.net/wiki/Category:Getting_Started#Loading_Your_Plugin_in_the_Game "Category:Getting Started"). As you walk around the space, look for gaps and seams you may have accidentally missed in the editor.

If you choose to load the above plugin to your game, or if you named your newly created cell the same as LokirsTomb, you can teleport to it by typing `COC LokirsTomb` in the console.

[![LokirstombSS.jpg](https://ck.uesp.net/w/images/thumb/c/c3/LokirstombSS.jpg/300px-LokirstombSS.jpg)](https://ck.uesp.net/wiki/File:LokirstombSS.jpg)

___

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>When testing, it's helpful to use the <b><a href="https://ck.uesp.net/wiki/COCMarkerHeading" title="COCMarkerHeading">COCMarkerHeading</a></b>. These markers are only used for testing - when using the COC <a href="https://ck.uesp.net/wiki/Console_Commands" title="Console Commands">console command</a>, this is where you will appear. Only one of these markers should be placed per cell. If a cell has a pre-existing coc Marker, simply move it before saving the plugin. Like all markers, if it's hidden, press <b>"M"</b> to show it. If you are having trouble finding it in the Object Window, simply type "COC" into the filter box and select the <b>*ALL</b> category.</td></tr></tbody></table>

___

## Problem

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td><p>'Creation-kit' has been having some slight problems with rendering objects from your mod into the real game, although this is a problem for some people. If you make a mod that has a Piece of Static objects in it, and then you save and upload, but when you go to test it out it is not there then the problem has occurred, currently there is not a fix to this, I will be looking for a way on avoiding this, or preferable fixing it. Hopefully Bethesda Game Studios.</p></td></tr></tbody></table>