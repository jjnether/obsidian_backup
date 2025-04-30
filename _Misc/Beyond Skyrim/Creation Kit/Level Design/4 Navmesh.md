## Overview

In this chapter we will go over creating a navmesh both manually and with automatic generation.

The reader will learn:

-   What _"Navmesh"_ is, and why it's important
-   How to auto generate a navmesh using Recast Based generation
-   How to edit navmesh by hand
-   Fixing navmesh warnings
-   Generating basic cover

## What is [Navmesh](https://ck.uesp.net/wiki/Category:Navmesh "Category:Navmesh")?

When an area has been built and cluttered, we need to determine where actors can navigate. This is where [navmesh](https://ck.uesp.net/wiki/Category:Navmesh "Category:Navmesh") comes in. Simply put, a navmesh is a collection of polygons that tells an actor where it can walk.

It's easy to take for granted the amount of information we use when playing. Our brains process every visual detail, constantly drawing conclusions and making predictions. Unfortunately, AI systems are nowhere near advanced as the human brain, and must rely on information we provide. Navmesh is critical to the knowledge an AI actor has about any given space. Quality navmesh is an important factor in helping the AI behave as well as possible.

The navmesh editor is a robust tool - which can be frustrating to use at first. We'll learn step-by-step how to get started with it. Once you've learned the fundamentals and had some practice you'll be a navmesh expert in no time.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td>GECK users take note: not much in the way of navmeshing <i>by hand</i> has changed. There have, however, been additions to auto generation, such as the all-new "<i>Recast</i>" generation mode, which is covered in this tutorial. For more information, check the <a href="https://ck.uesp.net/wiki/Navmesh_Generation" title="Navmesh Generation">Navmesh Generation</a> page.<p>Users of the Oblivion and/or Morrowind Construction Set will note that <a href="https://ck.uesp.net/wiki/Navmesh" title="Navmesh">Navmesh</a> has entirely replaced the pathfinding system in those tools.</p></td></tr></tbody></table>

## Auto-Generating Navmesh

[![](https://ck.uesp.net/w/images/thumb/e/ed/Jb_NavmeshToolBar01a.jpg/500px-Jb_NavmeshToolBar01a.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshToolBar01a.jpg)

[![](https://ck.uesp.net/w/images/thumb/1/13/Jb_NavmeshToolBar01b.jpg/500px-Jb_NavmeshToolBar01b.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshToolBar01b.jpg)

**Fig. 4.2:** Navmesh Tool Bar

All navmesh work is done in a separate editor mode. To enter this mode, click the Navmesh Button (_Fig. 4.1_) on the Main Tool Bar, or press **"CTRL+E"**. The [Navmesh toolbar](https://ck.uesp.net/wiki/Navmesh_Toolbar "Navmesh Toolbar") (_Fig. 4.2_) will appear.

We don't actually need to use anything on the Navmesh Tool Bar in order to auto generate our navmesh; it exists as a convenience. We do need to be in Navmesh Mode in order to use auto generation, however, and the presence of the toolbar lets us know that this is the case.

There are four types of auto-generation: [Object Based](https://ck.uesp.net/wiki/Navmesh_Generation#Object-Based_Generation "Navmesh Generation"), [Havok Based](https://ck.uesp.net/wiki/Navmesh_Generation#Havok-Based_Generation "Navmesh Generation"), [Recast Based](https://ck.uesp.net/wiki/Navmesh_Generation#Recast-Based_Generation "Navmesh Generation"), and [Advanced](https://ck.uesp.net/wiki/Navmesh_Generation#Advanced_Generation "Navmesh Generation"). For the majority of interiors, you'll want to use the Recast Based generation and clean up your navmesh by hand afterwards. This tutorial will not go into depth on [Object Based](https://ck.uesp.net/wiki/Navmesh_Generation#Object-Based_Generation "Navmesh Generation") or [Havok Based](https://ck.uesp.net/wiki/Navmesh_Generation#Havok-Based_Generation "Navmesh Generation") generation. Advanced users may opt to create all of their navmeshes by hand. Some find this faster than auto generating and then cleaning up by hand - it's all a matter of preference once you become comfortable with the system.

Let's use [Recast](https://ck.uesp.net/wiki/Navmesh_Generation#Recast-Based_Generation "Navmesh Generation") generation to create an intial pass at navmesh in LokirsTomb:

1.  Click on the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window") to make sure it's the active window.
2.  Make sure you have nothing selected in the render window (if you're not sure, just Left-Click somewhere in the [Void](https://ck.uesp.net/wiki/Void "Void") or press the **D** key).
3.  Choose Recast Based Generation from the Navmesh menu in the main toolbar: **Navmesh > Generation > Recast Based Generation**.
4.  The **Recast Navmesh Generation** dialog will appear. (_Fig 4.3_)
5.  Don't worry about what all of the different values mean. Just make sure your values are similar to those pictured in _Fig 4.3_ and hit **"OK"**.
6.  Click **"OK"**. It may take some time to generate, depending on your PC.
7.  Once it's done, the navmesh should look similar to that shown in _Fig 4.4_ and _4.5_.

-   [![](https://ck.uesp.net/w/images/thumb/4/40/Jb_NavmeshRecastBasedGeneration.jpg/173px-Jb_NavmeshRecastBasedGeneration.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshRecastBasedGeneration.jpg)
    
    **Fig. 4.3:** Navmesh Recast Window
    
-   [![](https://ck.uesp.net/w/images/thumb/0/07/Jb_NavmeshRecastBasedGenerated01a.jpg/246px-Jb_NavmeshRecastBasedGenerated01a.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshRecastBasedGenerated01a.jpg)
    
    **Fig. 4.4**:  
    Results from the Recast Navmesh Generation
    
-   [![](https://ck.uesp.net/w/images/thumb/0/07/Jb_NavmeshRecastBasedGenerated01b.jpg/246px-Jb_NavmeshRecastBasedGenerated01b.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshRecastBasedGenerated01b.jpg)
    
    **Fig. 4.5**:  
    Recast Navmesh, navmesh only
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td>Sometimes you need to navmesh a large section of a level, but you don't want to delete other navmeshes in the level. You can hold CTRL+ALT and Left-Click and Drag Select all of the references in the cell that you want to navmesh. Once you have the references selected, click Recast Based Generation and navmesh will only be generated for those references.</td></tr></tbody></table>

## Navmesh by Hand

Now that we have a navmesh created, we need to spend some time cleaning it up. The easiest and fastest way to do this is by hand. Before we begin the clean up process, take a minute to look at your navmesh and see where Recast Based generation didn't do so well.  

If you're having trouble seeing your navmesh you can try one of the three Navmesh modes: Normal, Transparent, Navmesh Only. Press **"W"** to cycle through the three different modes, or use the toolbar buttons, pictured here:  
[![Jb NavmeshViewMode.jpg](https://ck.uesp.net/w/images/b/ba/Jb_NavmeshViewMode.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshViewMode.jpg)

## Deleting Parts of a Navmesh

When cleaning up automatically-generated navmesh, it's often best to begin by eliminating unnecessary segments of navmesh that have been placed on non-reachable areas. This will make it easier for us to see what's going on with the remaining navmesh afterward.

The Cave area and the stairs of the Nordic Ruins seem to be the biggest offenders. You will also see a lot of navmesh islands. Don't worry about these for now. Once we have cleaned up the main navmesh, removing the islands is fast and easy.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>For advanced users whom want to get rid of the islands right away, CTRL+Left Click one triangle on each navmesh you want to <i>keep</i> and then press <b>"I"</b>. This is called <b>Inverse Flood Fill</b> and selects all navmeshes not currently selected. Once you press <b>"I"</b> and all of the islands are selected, delete them with <b>"R"</b> or <b>"DELETE"</b>. This is faster than deleting each unwanted island manually, but it's also much easier to accidentally delete useful navmesh - be careful!</td></tr></tbody></table>

Begin by taking care of the cave section first. Then, we'll clean up the rest of the navmesh. For now, you'll only need to know about the three buttons on the far left of the navmesh toolbar:

-   [![](https://ck.uesp.net/w/images/d/d0/ButtonNavmeshstripTriangles.jpg)](https://ck.uesp.net/wiki/File:ButtonNavmeshstripTriangles.jpg)
    
    **Fig. 4.6**:  
    Select Triangle Button
    
-   [![](https://ck.uesp.net/w/images/3/38/ButtonNavmeshstripVerts.jpg)](https://ck.uesp.net/wiki/File:ButtonNavmeshstripVerts.jpg)
    
    **Fig. 4.7**:  
    Select Vertex Button
    
-   [![](https://ck.uesp.net/w/images/a/ac/ButtonNavmeshstripEdges.jpg)](https://ck.uesp.net/wiki/File:ButtonNavmeshstripEdges.jpg)
    
    **Fig. 4.8**:  
    Select Edge Button
    

To clean up the cave section, Left Click and Drag Select the vertices in the cave section. Remember to toggle visibility (_"W"_) to get your bearings. Don't worry about trying to preserve any of the navmesh in the cave area: we'll rebuild it later. Be sure that you have **Select Vertex** (_Fig 4.7_) and/or **Select Triangle** (_Fig4.6_) toggled _on_. You can clean up the cave section by selecting the vertices or triangles or both. _Fig 4.9a_ shows the navmesh with all vertices and triangles (or "_verts and tris_", for short) in the cave area selected and ready for deletion.

Once you've selected the Triangles and/or Vertices you wish to delete, press either **"R"** or **"del"** to delete the selection. With the cave section removed, your navmesh should look similar to that shown in _Fig 4.9b_.

-   [![](https://ck.uesp.net/w/images/thumb/8/87/LokirNavmeshCaveSection1aBEFORE.jpg/294px-LokirNavmeshCaveSection1aBEFORE.jpg)](https://ck.uesp.net/wiki/File:LokirNavmeshCaveSection1aBEFORE.jpg)
    
    **Fig. 4.9a:** Navmesh, cave section selected
    
-   [![](https://ck.uesp.net/w/images/thumb/d/d2/Jb_NavmeshCaveSection1a.jpg/300px-Jb_NavmeshCaveSection1a.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshCaveSection1a.jpg)
    
    **Fig. 4.9b:** Navmesh, cave section removed
    

## Creating a Navmesh Triangle

It's time now to create the navmesh in the cave section by hand.  

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>As you create and edit more and more navmeshes you will want to begin using <a href="https://ck.uesp.net/wiki/Navmesh_Cheat_Sheet" title="Navmesh Cheat Sheet">Navmesh hotkeys</a> instead of using the toolbar.<p><b>T</b> toggles Triangle Selection On/Off<br><b>V</b> toggles Vertex Selection On/Off<br><b>G</b> toggles Edge Selection On/Off</p></td></tr></tbody></table>

Toggle **Vertex Selection** on by either clicking the [![Jb NavmeshButtonToggleVertexSelect.jpg](https://ck.uesp.net/w/images/a/a7/Jb_NavmeshButtonToggleVertexSelect.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshButtonToggleVertexSelect.jpg) button in the navmesh toolbar or by using hotkey **"V"** and zoom into the beginning of the cave section. Right Click on the floor. Notice a vertex has appeared. Now create two more vertices the same way. You should see something like _Fig 4.10_ - three yellow (or two yellow and one green) vertices on the floor.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>Make sure you <i>do not</i> have Grid Snap on. You don't need it when navmeshing and will only cause problems if left on.</td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Navmesh editing uses a separate set of hotkeys than regular Creation Kit editing. Some hotkeys you may be accustomed to, such as <b>"T"</b> for top-down viewing, are re-bound to new keys while editing navmesh mode. You may wish to print and refer to the <a href="https://ck.uesp.net/wiki/Navmesh_Cheat_Sheet" title="Navmesh Cheat Sheet">Navmesh Cheat Sheet</a> while getting used to this mode.</td></tr></tbody></table>

Notice the colors of the vertices you've created. **Green** indicates that a vertex is currently selected. **Yellow** vertices are unselected and disconnected - not part of any triangle. Vertices that are unselected and part of a triangle render **Red**. Yellow vertices serve no purpose and can be safely deleted if any are left hanging around a complete navmesh.

To create a Triangle, select all three of your disconnected, yellow verts by using **CTRL+Left Click** on each vertex - or simply Drag Select all three at once. The selected vertices will turn green to show that they are selected. Press **"A"** or use [![Jb NavmeshButtonCreateTriangle.jpg](https://ck.uesp.net/w/images/0/09/Jb_NavmeshButtonCreateTriangle.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshButtonCreateTriangle.jpg) to create a triangle from the three vertices, as in _Fig 4.11_. Note that **"A"** only works when _exactly_ three verts are selected.

-   [![](https://ck.uesp.net/w/images/thumb/f/f9/Jb_NavmeshTriangle1a.jpg/270px-Jb_NavmeshTriangle1a.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshTriangle1a.jpg)
    
    **Fig. 4.10:** Three Yellow (disconnected) verts
    
-   [![](https://ck.uesp.net/w/images/thumb/b/b0/Jb_NavmeshTriangle1b.jpg/270px-Jb_NavmeshTriangle1b.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshTriangle1b.jpg)
    
    **Fig. 4.11:** Triangle formed from three verts
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>Notice that two vertices remain green/selected after creating the triangle. This makes it easier to create subsequent triangles. With two vertices selected, all you need to do to create another triangle is <b>CTRL+Right-Click</b>. A new vertex is created where you click and automatically creates a new triangle.</td></tr></tbody></table>

## Navmesh the Cave Section

Now that we have our first triangle, we need to fill up the rest of the cave section with other triangles. The easiest way to do this is to select two vertices and **ctrl+Right-Click** to place a third vertex. This will automatically create a new triangle between the two selected vertices and the newly-placed one.

Notice that once the new triangle is created, two vertices remain selected/green. Simply use **ctrl+Right-Click** to create another triangle. With practice, you can get into a rhythm and be able to fill up spaces quickly just by holding CTRL and Right Clicking. If the two green vertices aren't the two you need to create your next triangle, simply press **"Tab"** to swap selected vertices. Go ahead and fill up the rest of the cave section. Once your done, your cave section navmesh should look similar to _Fig 4.12_ and _4.13_ below.

_(Note: your results may vary depending on how much your clutter matches that in the example file)_

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>With this technique, you can create triangles very quickly and cover a lot of ground by simply using CTRL-Right Click. We fondly call this technique "Walking the Dog".</td></tr></tbody></table>

-   [![](https://ck.uesp.net/w/images/thumb/6/6f/Jb_NavmeshCaveFinished1a.jpg/300px-Jb_NavmeshCaveFinished1a.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshCaveFinished1a.jpg)
    
    **Fig. 4.12**:  
    Results from the Recast Navmesh Generation
    
-   [![](https://ck.uesp.net/w/images/thumb/4/47/Jb_NavmeshCaveFinished1b.jpg/300px-Jb_NavmeshCaveFinished1b.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshCaveFinished1b.jpg)
    
    **Fig. 4.13**:  
    Recast Navmesh, navmesh only
    

## Navmesh the Nordic Stairs
Before we move on to navmeshing the rest of the cell, let's look at the nordic stairs, _NorHallSm1wayStairs128_. Stairs are a typical problem area when using automatic generation. Your navmesh is probably disconnected here, as shown in _Fig 4.14a_.

Luckily, the Creation Kit makes it easy to quickly join disconnected navmesh like this.

For this example, we want a clean edge at the top and bottom of the stairs. Follow these steps:

1.  Delete any vertices on the staircase itself, if applicable.
2.  Re-arrange the vertices at the top and the bottom of the staircase, creating a clean, open edge at each side.
3.  If either edge has three or more vertices at the top of the stairs, merge some of the vertices so there are only two remaining. - To merge vertices, select which ones you want to merge and press **"Q"** or [![Jb NavmeshButtonMergeVertices.jpg](https://ck.uesp.net/w/images/6/64/Jb_NavmeshButtonMergeVertices.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshButtonMergeVertices.jpg) on the toolbar.
4.  Make sure edge selection is toggled on (**"G"**)
5.  Double-click one of the edges. Double-clicking an edge selects the two vertices on that edge - they will turn green to indicate this.
6.  With the two vertices selected, hold CTRL and double-click the other edge. Navmesh is automatically generated to join the edges. Your result should look similar to _Fig 4.14b_ below.

-   [![](https://ck.uesp.net/w/images/thumb/3/39/Jb_NavmeshStairs1a.jpg/300px-Jb_NavmeshStairs1a.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshStairs1a.jpg)
    
    **Fig. 4.14a:** Stairs after Recast Navmesh Generation
    
-   [![](https://ck.uesp.net/w/images/thumb/a/af/Jb_NavmeshStairs1b.jpg/300px-Jb_NavmeshStairs1b.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshStairs1b.jpg)
    
    **Fig. 4.14b:** Cleaned up stair navmesh
    

## Navmesh the Rest of the Level

With the cave section navmeshed and the stairs connected you now know the essentials and are equipped to continue navmeshing the rest of the cell. Go ahead and navmesh the rest of the cell and if you run into any problems, the following pointers may come in handy.

-   Focus on a clean, simple navmesh. This will be easier to edit and run faster in-game.
-   Remember your hotkeys! Keep the [Navmesh Cheat Sheet](https://ck.uesp.net/wiki/Navmesh_Cheat_Sheet "Navmesh Cheat Sheet") handy while learning.
-   Don't bother creating navmesh in areas that AI won't be able to use anyway, such as narrow areas between furniture. [Pathing Tests](https://ck.uesp.net/wiki/Pathing_Tests "Pathing Tests") can be used to test this.
-   Remember: to automatically create navmesh between two nearby, open edges: **Double-Left Click** one edge, then **CTRL+Double-Left Click** the other edge.
-   Take advantage of the multiple view modes. To cycle through, press **"W"** or use the toolbar buttons  
    [![Jb NavmeshViewMode.jpg](https://ck.uesp.net/w/images/b/ba/Jb_NavmeshViewMode.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshViewMode.jpg)
-   To delete a triangle, toggle "**T**", select the offending triangle and press **DELETE** or **R**. You can also undo a change you've made with **CTRL-Z**.
-   Deleting any vertex will delete all triangles and edges of which it was a part.
-   Remember the hotkeys for toggling Triangle, Vertex, and Edge Selection. (**T**, **V**, **G** respectively).
-   To merge vertices, select two or more and press **Q** or [![Jb NavmeshButtonMergeVertices.jpg](https://ck.uesp.net/w/images/6/64/Jb_NavmeshButtonMergeVertices.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshButtonMergeVertices.jpg) The vertices will merge to the _first_ selected vertex.
-   **Double-Click** an edge (with Edge Selection turned on, **"G"**) to quickly select its two vertices.
-   Remember how two vertices remain selected after creating a triangle? You can cycle through which two vertices you want selected by pressing **"TAB"**.
-   You can press **"R"** to delete selected objects if you don't want to reach across your keyboard and hit the **DELETE** key.
-   Strive to create "fat" triangles - as close to equilateral as possible. These are much more efficient. Thin, "skinny" triangles are to be avoided. Use edge-rotating with hotkey **"S"** or [![Jb NavmeshButtonSwapEdge.jpg](https://ck.uesp.net/w/images/3/3d/Jb_NavmeshButtonSwapEdge.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshButtonSwapEdge.jpg) to achieve a more ideal result, as picture in _Fig 4.15_s before & after example.
-   If you have what looks like a connected navmesh, but you see a yellow edge, this just means there are two vertices overlapping each other. To fix, drag select over the vertices and merge them together (**"Q"**). If the yellow edge remains, do the same thing on the vertices on the other side of the edge. If the yellow edge disappears, you have merged the vertices and have connected your navmesh.
-   Right-Click on an edge to create a vertex on that edge. This is called _splitting_ an edge.

-   [![](https://ck.uesp.net/w/images/thumb/c/cf/Sunburstnavmeshbefore.jpg/250px-Sunburstnavmeshbefore.jpg)](https://ck.uesp.net/wiki/File:Sunburstnavmeshbefore.jpg)
    
    **Fig. 4.15a:** Example of inefficient, _"sunburst"_ edges
    
-   [![](https://ck.uesp.net/w/images/thumb/0/06/Sunburstnavmeshfixed.jpg/250px-Sunburstnavmeshfixed.jpg)](https://ck.uesp.net/wiki/File:Sunburstnavmeshfixed.jpg)
    
    **Fig. 4.15b:** Same navmesh shape after edge-flipping cleanup
    

Here is what the navmesh should look like near the cluttered areas of the level. Notice in _Fig 4.16_ that the navmesh goes under physics-enabled (_moveable/dynamic_) objects. You never need to navmesh around a Havok object, the navmesh takes care of it during run-time. In the example below, the Havok objects in the scene are the shovel, wooden cart, and ceramic pot. Notice the navmesh goes underneath these objects. The wooden barrels are not Havok objects and therefore we need to navmesh around them.

-   [![](https://ck.uesp.net/w/images/thumb/c/c2/Jb_NavmeshFinalHavok01a.jpg/300px-Jb_NavmeshFinalHavok01a.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshFinalHavok01a.jpg)
    
    **Fig. 4.16:** Navmesh properly avoiding static but not dynamic objects
    

_Fig 4.17_ shows approximately what your navmesh should look like after you're done. In this example, we've left the small, isolated navmesh _"islands"_. These can easily be deleted.

1.  Select any triangle in your main navmesh and press **"I"** or [![Jb NavmeshButtonToggleInverseFloodFill.jpg](https://ck.uesp.net/w/images/f/f8/Jb_NavmeshButtonToggleInverseFloodFill.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshButtonToggleInverseFloodFill.jpg)
2.  This is called inverse flood fill and selects all navmeshes not in the selection. Assuming your playable area consists of a single, contiguous navmesh, all the area now highlighted green are unnecessary.
3.  With the islands selected, delete them with **"R"** or **"DELETE"**.
4.  Your final navmesh should look similar to that in _Fig 4.18_.

-   [![](https://ck.uesp.net/w/images/thumb/8/87/Jb_NavmeshFinal01a.jpg/300px-Jb_NavmeshFinal01a.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshFinal01a.jpg)
    
    **Fig. 4.17:** Hand Crafted Navmesh w/islands
    
-   [![](https://ck.uesp.net/w/images/thumb/5/5f/Jb_NavmeshFinal01b.jpg/300px-Jb_NavmeshFinal01b.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshFinal01b.jpg)
    
    **Fig. 4.18:** Final Navmesh
    

## Fixing Navmesh Errors

You need to always check your navmesh for errors after you're done navmeshing a cell. This is a relatively simple process.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>You'll be notified upon saving your plugin if you have any errors. Regardless if you get an error or not when saving, you should always run "Check Navmesh".</td></tr></tbody></table>

1.  Bring up the [Select Triangle by Index](https://ck.uesp.net/wiki/Select_Triangle_by_Index "Select Triangle by Index") dialog pictured in _fig 4.18_. There are three ways to do this:
    1.  Use the Find Triangle button on the Navmesh Tool Bar, [![Jb NavmeshButtonFindTriangle.jpg](https://ck.uesp.net/w/images/a/ac/Jb_NavmeshButtonFindTriangle.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshButtonFindTriangle.jpg)
    2.  Pressing the **"CTRL+F"** hotkey
    3.  Via the Main Menu: **Navmesh > Select Triangle by Index**.
2.  Once this dialog is up, select **"Check Navmesh"**.
3.  A warning, shown in _fig 4.19_, pops up showing how many triangles were found (if any) and asks if you want to delete all of them.
4.  Next, deal with the problem triangles. There are two approaches to this:
    1.  Choosing **"Yes"** will delete all of the problem triangles - but you'll have to go in and find where these triangles were located and patch them up (usually by creating a new triangle). You won't have any way to find these triangles except by eye, which can be difficult with complex navmesh, especially if the offending triangles were small or overlapped.
    2.  We recommend you fix each error by hand, in which case you can select **"No"** to bypass. This will close the warnings dialog.
    3.  Select **Next Warning** in the Select Triangle dialog. The render window camera will automatically snap to the problem triangle and highlight it for you. Most errors are easily solved by deleting the problem triangle and rebuilding.
    4.  If you have more than one warning, select **Check Navmesh** once again and repeat the process until all problem triangles have been corrected. (You have to re-check between each deletion because the index of navmesh triangles is affected when you correct each error.)
5.  When you've finished, save your plugin again.

-   [![](https://ck.uesp.net/w/images/thumb/8/84/Jb_NavmeshSelectTriangleDialog.jpg/300px-Jb_NavmeshSelectTriangleDialog.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshSelectTriangleDialog.jpg)
    
    **Fig. 4.18:** Select Triangle Dialogue
    
-   [![](https://ck.uesp.net/w/images/thumb/0/03/Jb_NavmeshWarnings.jpg/300px-Jb_NavmeshWarnings.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshWarnings.jpg)
    
    **Fig. 4.19:** Navmesh Warnings
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>If you don't want to fix each error by hand, click through each bad triangle with the "Next Warning" button, then choose <b>"Yes"</b> to delete all of the problem triangles. This will let you know where to check the navmesh for missing coverage after the deletion.</td></tr></tbody></table>

## Create Cover Edges

Cover edges store data such as the height of a piece of cover, which NPCs use in combat and during regular pathfinding.

1.  To automatically detect cover, navigate to **Navmesh > Find Cover Edges** from the Main Toolbar, or use the [![Jb NavmeshButtonFindCover.jpg](https://ck.uesp.net/w/images/2/24/Jb_NavmeshButtonFindCover.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshButtonFindCover.jpg) button in the Navmesh Toolbar.
2.  Finding cover should take a small amount of time to process, depending on your hardware and the complexity of the navmesh.
3.  When done, you'll notice different colored edges in your navmesh. Each color represents different cover heights. The navmesh should look similar to that pictured in Fig 4.20 below after you've generated cover.
4.  To get a better visual of what kind of cover is in your level, simply navigate to **Navmesh > Draw Cover** (shown in _Fig 4.21_).

With navmesh complete, actors will be able to navigate the space. Building quality navmesh can be a time-consuming and, at times, tedious process - but the results of a bad navmesh are evident during gameplay.

-   [![](https://ck.uesp.net/w/images/thumb/2/27/Jb_NavmeshEditingDrawCover01a.jpg/300px-Jb_NavmeshEditingDrawCover01a.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshEditingDrawCover01a.jpg)
    
    **Fig. 4.20**:  
    A typical navmesh with cover data
    
-   [![](https://ck.uesp.net/w/images/thumb/4/4c/Jb_NavmeshEditingDrawCover01b.jpg/300px-Jb_NavmeshEditingDrawCover01b.jpg)](https://ck.uesp.net/wiki/File:Jb_NavmeshEditingDrawCover01b.jpg)
    
    **Fig. 4.21**:  
    Navmesh with Cover Draw toggled on
    

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>Cover information isn't just used for ranged combat - it also determines where an AI will tend to go when fleeing from an enemy, for example. So it's a good idea to generate this information, even when it doesn't seem important.<p>Navmesh can hold more data than just cover - it's also possible to mark triangles as water, preferred, and edges as drop-down ledges. More information can be found <a href="https://ck.uesp.net/wiki/Category:Navmesh#Navmesh_Data" title="Category:Navmesh">here</a>.<br>It is also possible to fine-tune cover data, although this level of detail isn't often necessary. To manually adjust cover data, select an edge and press <b>"E"</b>. This will summon the "<i>Edge Cover</i>" dialog.</p></td></tr></tbody></table>

Here are a few pages you might want to reference during and after the tutorial, or in your further reading.

-   [Navmesh Overview](https://ck.uesp.net/wiki/Category:Navmesh "Category:Navmesh") - The Navmesh category has links to other topics regarding navmesh.
-   [Main Toolbar](https://ck.uesp.net/wiki/Main_Toolbar "Main Toolbar") - Information on what the different icons on the Main Toolbar and Navmesh Toolbar and what they do.
-   [Navmesh Toolbar](https://ck.uesp.net/wiki/Navmesh_Toolbar "Navmesh Toolbar") - Explains the buttons in the Navmesh Toolbar.
-   [Navmesh Cheat Sheet](https://ck.uesp.net/wiki/Navmesh_Cheat_Sheet "Navmesh Cheat Sheet") - Useful Hotkeys while in navmesh editing. Good to print out and keep handy while learning.

A solid navmesh provides the foundation needed to set up good NPC and combat gameplay. In the next tutorial we'll deal with just that.

## Known Issue

There was an issue causing navmeshes in .ESPs to stop working if you travelled a few cells away from where they were placed. NPCs stopped moving and would not resume until the game was restarted. This issue was resolved with the 1.6 Title Update.