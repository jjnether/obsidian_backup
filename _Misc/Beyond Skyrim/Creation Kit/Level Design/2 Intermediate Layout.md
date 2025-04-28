| Bethesda Tutorial Layout Part 2                                                                                                                                                                                                                                                 |                                                                                                                                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Level Design Series, Chapter 2                                                                                                                                                                                                                                                  |                                                                                                                                                                                                                                                      |
| [Return to Tutorial Hub](https://ck.uesp.net/wiki/Category:Tutorials "Category:Tutorials")                                                                                                                                                                                      |                                                                                                                                                                                                                                                      |
| [![LeftArrow.png](https://ck.uesp.net/w/images/9/97/LeftArrow.png)](https://ck.uesp.net/wiki/Bethesda_Tutorial_Layout_Part_1 "Bethesda Tutorial Layout Part 1") [Previous Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Layout_Part_1 "Bethesda Tutorial Layout Part 1") | [Next Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Clutter "Bethesda Tutorial Clutter")[![RightArrow.png](https://ck.uesp.net/w/images/c/cc/RightArrow.png)](https://ck.uesp.net/wiki/Bethesda_Tutorial_Clutter "Bethesda Tutorial Clutter") |
| **Example Plugins:**                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                      |
| [Initial](https://ck.uesp.net/w/index.php?title=Special:Upload&wpDestFile=LDLayoutPart1TutorialComplete.esp "LDLayoutPart1TutorialComplete.esp")                                                                                                                                | [Completed](https://ck.uesp.net/w/index.php?title=Special:Upload&wpDestFile=LDLayoutPart2TutorialComplete.esp "LDLayoutPart2TutorialComplete.esp")                                                                                                   |
| [Companion Video Tutorial](http://youtu.be/p1Twdld0tLc?hd=1)                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                      |

## Overview\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&veaction=edit&section=1 "Edit section: Overview") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&action=edit&section=1 "Edit section: Overview")\]

This chapter delves a little deeper into layout technique. Specifically, working with the more organic "cave" kit.

The reader will learn:

-   Using and transitioning between multiple kits
-   Working with an organic kit
-   Working off the grid and using a Snap Reference

## Organic Level Design\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&veaction=edit&section=2 "Edit section: Organic Level Design") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&action=edit&section=2 "Edit section: Organic Level Design")\]

You can easily create levels by connecting kit pieces on the grid, all at 90 degree angles. This works well for "architectural" dungeons, such as Nord ruins or Imperial Towers. However, natural environments use more organic features, so as you create, you may find yourself wanting to go off the grid, especially when creating natural environments such as caves. Luckily, many of the kits available are built with such a workflow in mind. For this next section, we'll work in the Cave kit into the Nordic dungeon.

## The Cave Kit\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&veaction=edit&section=3 "Edit section: The Cave Kit") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&action=edit&section=3 "Edit section: The Cave Kit")\]

The Cave kit functions essentially like the Nordic Ruins kit - it's composed of a series of sub-kits that obey snapping rules - but the caves allow for more organic freedom, as seen throughout Skyrim. The versatility of this kit allows a designer to create just about any kind of chamber imaginable. However, working this way is a little different than the way we built the Nordic portion of this dungeon.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>There are multiple Cave kits variations available: Ice, Mine and Caves. We'll be using the Green Cave kit. When searching in your object window, you can start all searches with the prefix <b>caveg*</b>, which will prevent Ice and Mine variations from appearing.</td></tr></tbody></table>

## Creating a Shell\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&veaction=edit&section=4 "Edit section: Creating a Shell") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&action=edit&section=4 "Edit section: Creating a Shell")\]

We're going to replace the final room of the Lokir's Tomb (the really big one) with a cave chamber. Delete the area pictured in _Fig. 2.1_ so that it looks more like _Fig. 2.2_

We're going to replace the deleted room with a simple "Shell" chamber. When working with Caves, it's often best to start with a very basic shape, then build inwards to create a natural-looking space. Our shell will be a large 4x4 room. Locate and drag the following pieces into the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window"). These pieces are pictured in _Fig. 2.3_ as a visual aid.

-   **CaveGLRoomCorner01**
-   **CaveGLRoomCorner02**
-   **CaveGLRoomCorner03**
-   **CaveGLRoomCorner04**
-   **CaveGLRoomWall01** (x2)
-   **CaveGLRoomWall02** (x2)
-   **CaveGLRoomWall03** (x2)
-   **CaveGLRoomWall04** (x2)
-   **CaveGLRoomMid01** (x4)

Arrange the loose pieces together as pictured in _Fig. 2.4_. (Hint: You need one type of wall piece per side to get the pieces to fit together correctly without seams. It might be easier if you start with the middle, then add the walls, making sure they match correctly as you go.) This will be the starting point for our final room. We'll be deleting a few pieces so that the player can get in and out of the room, but for right now we're only worried about roughing in the general shape in which we'll define the room.

-   [![](https://ck.uesp.net/w/images/thumb/e/ed/StartingLayout01.jpg/120px-StartingLayout01.jpg)](https://ck.uesp.net/wiki/File:StartingLayout01.jpg)
    
    **Fig. 2.1**:  
    The starting layout of the final room
    
-   [![](https://ck.uesp.net/w/images/thumb/c/ce/StartingLayout02.jpg/120px-StartingLayout02.jpg)](https://ck.uesp.net/wiki/File:StartingLayout02.jpg)
    
    **Fig. 2.2**:  
    After the portion has been removed
    
-   [![](https://ck.uesp.net/w/images/thumb/9/9d/CaveShellBrokenUp01.jpg/114px-CaveShellBrokenUp01.jpg)](https://ck.uesp.net/wiki/File:CaveShellBrokenUp01.jpg)
    
    **Fig. 2.3**:  
    A breakdown of all the pieces needed to build the new cave shell
    
-   [![](https://ck.uesp.net/w/images/thumb/0/0b/CaveShellComplete01.jpg/120px-CaveShellComplete01.jpg)](https://ck.uesp.net/wiki/File:CaveShellComplete01.jpg)
    
    **Fig. 2.4**:  
    The constructed cave shell
    

## Transitions\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&veaction=edit&section=5 "Edit section: Transitions") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&action=edit&section=5 "Edit section: Transitions")\]

When working with multiple kits, you'll need to create transitions from one kit to the next. Some pieces exist specifically for this purpose (such as _NorHallBg1wayToCaveG01_), but if there isn't a piece available for what you had in mind, don't worry. You can easily make your own transitions, which have the advantage of being visually unique.

Begin this transition by extending the Large Nordic Hall by another piece. Create a duplicate of **NorHallBG1way01** (select the existing piece and **ctrl+D**) and attach it to the end of that hall.

To create the hall transition, you'll need the following CaveG pieces:

-   **CaveGLWallDoorL01**
-   **CaveGLWallDoorLB01**
-   **CaveGLHall1Way01**

Assemble these pieces as shown in _Fig. 2.5_. Make sure that **snap-to-grid** [![SnapToGrid.jpg](https://ck.uesp.net/w/images/a/a4/SnapToGrid.jpg)](https://ck.uesp.net/wiki/File:SnapToGrid.jpg) is turned on. We'll be freely placing these pieces in a moment, but need them snapped to each other for now.

Once the transition area is created, turn**Snap-to-grid** [![SnapToGrid.jpg](https://ck.uesp.net/w/images/a/a4/SnapToGrid.jpg)](https://ck.uesp.net/wiki/File:SnapToGrid.jpg) off. Select all three pieces, and move them in line with the Large Nordic Hall. Adjust the positioning until it looks good to you; _Fig 2.6_ provides an example. It's a good idea to visually spot-check this in-game before continuing, keeping an eye out for any bad gaps. Better to fix them now, when it only means adjusting a few pieces!

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>Moving a selection of multiple kit pieces can sometimes introduce small seams, sometimes referred to as <i>"spiderwebs"</i>, as noted in <i>Fig 2.8</i>. These can be fixed with snap-to-reference, which is discussed in the next section.</td></tr></tbody></table>

-   [![](https://ck.uesp.net/w/images/thumb/c/cb/TransitionBreakdown01.jpg/120px-TransitionBreakdown01.jpg)](https://ck.uesp.net/wiki/File:TransitionBreakdown01.jpg)
    
    **Fig. 2.5**:  
    Breakdown of the transition pieces, individually and assembled(inset)
    
-   [![](https://ck.uesp.net/w/images/thumb/b/b4/TransitionInPlace.jpg/120px-TransitionInPlace.jpg)](https://ck.uesp.net/wiki/File:TransitionInPlace.jpg)
    
    **Fig. 2.6**:  
    The transition in place
    

## Working Off the Grid\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&veaction=edit&section=6 "Edit section: Working Off the Grid") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&action=edit&section=6 "Edit section: Working Off the Grid")\]

In order to create more organic spaces, it's important to become comfortable working "off the grid". This doesn't mean that we're going to disregard snapping rules, however. Working off the grid means that we're going to be assembling components of the level independently of the main world grid, then using transitions, such as the one we've just created, to join them. This allows us to create much more natural-feeling spaces than are possible otherwise.

The Nordic Ruins we created in the [previous tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Layout_Part_1 "Bethesda Tutorial Layout Part 1") are "on the grid". The cave chamber we are building now will be "off the grid". Let's explore that workflow now.

1.  First we make sure that **snap to grid** [![SnapToGrid.jpg](https://ck.uesp.net/w/images/a/a4/SnapToGrid.jpg)](https://ck.uesp.net/wiki/File:SnapToGrid.jpg) and **snap to angle** [![SnapToAngle.jpg](https://ck.uesp.net/w/images/2/21/SnapToAngle.jpg)](https://ck.uesp.net/wiki/File:SnapToAngle.jpg) are turned off.
2.  Select all the pieces in the shell we've just created and rotate it approximately 45 degrees, as shown in _Fig 2.7_.
3.  Delete the corner of the large room closest to the Large Nordic Hallway
4.  Reselect the rest of the room and move it until the walls of your room intersect part of the Cave Transition piece, also shown in _Fig 2.7_
5.  We're also going to shift the cave shell down somewhat, so the player will enter the room higher than the floor. This isn't an exact science - just bring the room down along the Z axis until the transition looks similar to that shown in _Fig 2.7_.

-   [![](https://ck.uesp.net/w/images/thumb/2/2f/CaveShellOffGrid.jpg/120px-CaveShellOffGrid.jpg)](https://ck.uesp.net/wiki/File:CaveShellOffGrid.jpg)
    
    **Fig. 2.7**:  
    Breakdown of the transition pieces, seperate and assembled
    
-   [![](https://ck.uesp.net/w/images/thumb/5/5d/SpiderWebbing.jpg/120px-SpiderWebbing.jpg)](https://ck.uesp.net/wiki/File:SpiderWebbing.jpg)
    
    **Fig. 2.8**:  
    An example of spider-webbing
    

## Working With Snap-to-Reference\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&veaction=edit&section=7 "Edit section: Working With Snap-to-Reference") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&action=edit&section=7 "Edit section: Working With Snap-to-Reference")\]

Placing an entire room off the grid is one thing, but it's no good if we can't work with that room once placed. The next exercise will show how that's possible - and is _critical_ to working off the grid.

Now that we've got the room placed as we want it, try grabbing a corner of the cave room and resetting its rotation with **ctrl+K**. Turn snapping on and attempt to put snap that piece back into place now. You should notice pretty quickly that it can't be done - the reset piece is snapping to the global grid.

Click back into the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window") and press **Shift+Q**. Notice that your mouse icon has changed to a crosshair, as seen below.

The icon will be red when over the [Void](https://ck.uesp.net/wiki/Void "Void"): [![CrosshairRed.png](https://ck.uesp.net/w/images/8/81/CrosshairRed.png)](https://ck.uesp.net/wiki/File:CrosshairRed.png), and white when over a valid reference: [![CrosshairWhite.png](https://ck.uesp.net/w/images/c/c7/CrosshairWhite.png)](https://ck.uesp.net/wiki/File:CrosshairWhite.png). Hover over any piece in the off-kilter room we've placed and click when the crosshair turns white.

What this has done is temporarily changed the global grid and angle orientation to match the piece you've just selected - known as the **snap reference**. Try selecting the piece we reset at the beginning of this section and snapping it back into place now. This is a great way to work off the normal grid, but make sure all your pieces snap together without any visual abnormalities or spiderwebbing (Fig 2.8).

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>Whenever you're ready to clear your snap reference and return to using the global grid, just <b>shift+Q</b> and click the red crosshair anywhere in the <a href="https://ck.uesp.net/wiki/Void" title="Void">grey void</a>.</td></tr></tbody></table>

## Reshaping the Cave\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&veaction=edit&section=8 "Edit section: Reshaping the Cave") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&action=edit&section=8 "Edit section: Reshaping the Cave")\]

What you have right now is a pretty standard large cave room. The cave kit is designed specifically to convert rooms such as this into more organic spaces. The idea is to create a space larger than we need and start eating into it with add-in pieces - so let's change the shape of this room a little bit by building inwards. Every kit in Skyrim is designed with this workflow in mind, but the cave kit exemplifies it.

The cave kit comes with many different pieces to help you reshape your play space. Place in the following loose columns and free walls, pictured in _Fig. 2.9_.

-   **CaveGLPillar01**
-   **CaveGLPillar02**
-   **CaveGLPillar03**
-   2x**CaveGLWallStraight01**

We're going to use these pieces to bring in the southern wall of the room. In order to get that organic look,turn off **snap to grid** and **snap to angle** and start moving the pieces around to form the wall. Use the pillars to hide any seams between the walls. (See _Figs. 2.10_ and _2.11_) Take your time and frequently check your work in-game to look for any open gaps/seams.

-   [![](https://ck.uesp.net/w/images/thumb/0/0b/CaveWallBreakdown.jpg/96px-CaveWallBreakdown.jpg)](https://ck.uesp.net/wiki/File:CaveWallBreakdown.jpg)
    
    **Fig. 2.9**:  
    The individual pieces used in the cave wall
    
-   [![](https://ck.uesp.net/w/images/thumb/f/f0/CaveWallBefore.jpg/120px-CaveWallBefore.jpg)](https://ck.uesp.net/wiki/File:CaveWallBefore.jpg)
    
    **Fig. 2.10**:  
    Before the new cave wall is in place
    
-   [![](https://ck.uesp.net/w/images/thumb/3/3b/CaveWallAfter.jpg/120px-CaveWallAfter.jpg)](https://ck.uesp.net/wiki/File:CaveWallAfter.jpg)
    
    **Fig. 2.11**:  
    The cave wall pieces in place
    

Now that we've reshaped the walls, let's play with the verticality of the level using two cave-specific _"cliff"_ pieces, pictured in _Fig. 2.12_.

-   **CaveGCliffsCornerOut01NS**
-   **CaveGCliffs01**

Verticality in a level makes encounters more interesting than fighting in a large, flat room, as well as being more natural and pleasing to the eye. (See _Figs. 2.13_ and _2.14_) Feel free to experiment with other walls, rocks, floors and pillars to get the right feel and flow in your rooms. There's no need to match the example directly; experiment and express yourself here.

-   [![](https://ck.uesp.net/w/images/thumb/d/da/CaveCliffsBreakdown.jpg/120px-CaveCliffsBreakdown.jpg)](https://ck.uesp.net/wiki/File:CaveCliffsBreakdown.jpg)
    
    **Fig. 2.12**:  
    The cave cliff pieces
    
-   [![](https://ck.uesp.net/w/images/thumb/c/c3/CaveCliffsBefore.jpg/120px-CaveCliffsBefore.jpg)](https://ck.uesp.net/wiki/File:CaveCliffsBefore.jpg)
    
    **Fig. 2.13**:  
    Before the new cave cliffs are in place
    
-   [![](https://ck.uesp.net/w/images/thumb/b/b1/CavecliffsAfter.jpg/120px-CavecliffsAfter.jpg)](https://ck.uesp.net/wiki/File:CavecliffsAfter.jpg)
    
    **Fig. 2.14**:  
    The cave cliffs in place
    

## Filling in the Gaps\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&veaction=edit&section=9 "Edit section: Filling in the Gaps") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Layout_Part_2&action=edit&section=9 "Edit section: Filling in the Gaps")\]

Now that you've got gameplay space worked out, you'll probably notice large gaps that expose the grey void. You'll want to cover these up before you're done here. Here are the pieces we'll be using in this example, pictured in _Fig. 2.15_.

-   **CaveGLPillar01**
-   **CaveGBoulderL01**
-   **CaveGBoulderL04**
-   **CaveGRockPileS01**
-   **CaveGDirtMound01**

The pillar and boulders can be used for the larger gaps in the ceiling and wall. The dirt mound and rock piles work great for ground transitions between different kits (see _Figs 2.16_ and _2.17_). As before, feel free to try using any of the pieces you want until you find ones that you think work well: for example, in _Fig 2.17_, an additional **CaveGCliffs01** has been used to give a nicer step down.

-   [![](https://ck.uesp.net/w/images/thumb/0/03/CaveFillinBreakdown.jpg/120px-CaveFillinBreakdown.jpg)](https://ck.uesp.net/wiki/File:CaveFillinBreakdown.jpg)
    
    **Fig. 2.15**:  
    The cave fillin pieces
    
-   [![](https://ck.uesp.net/w/images/thumb/1/17/CaveFillinBefore.jpg/120px-CaveFillinBefore.jpg)](https://ck.uesp.net/wiki/File:CaveFillinBefore.jpg)
    
    **Fig. 2.16**:  
    Before the new cave fillin are in place
    
-   [![](https://ck.uesp.net/w/images/thumb/1/1e/CaveFillinAfter.jpg/120px-CaveFillinAfter.jpg)](https://ck.uesp.net/wiki/File:CaveFillinAfter.jpg)
    
    **Fig. 2.17**:  
    The cave fillin in place
    

Once you're happy with the layout of this chamber and the general layout of the tomb, you're ready to move onto smaller details - clutter.

<table><tbody><tr><th><b><a href="https://ck.uesp.net/wiki/CreationKit:Language_policy" title="CreationKit:Language policy">Language:</a></b></th><td><b><a>English</a></b> <span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="fr"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Layout_Part_2/fr" title="Bethesda Tutorial Layout Part 2/fr">français</a></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="ja"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Layout_Part_2/ja" title="Bethesda Tutorial Layout Part 2/ja">日本語</a></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="pl"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Layout_Part_2/pl" title="Bethesda Tutorial Layout Part 2/pl">polski</a></span><span></span><span></span><span></span>&nbsp;• <span lang="ru"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Layout_Part_2/ru" title="Bethesda Tutorial Layout Part 2/ru">русский</a></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></td></tr></tbody></table>