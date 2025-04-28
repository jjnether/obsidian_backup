_**Or, a Brief Walkthrough Hooking the Bendu Quest onto the Story Manager.**_

[![DialogueInGame.png](https://ck.uesp.net/w/images/3/33/DialogueInGame.png)](https://ck.uesp.net/wiki/File:DialogueInGame.png)

## Introduction

This is a walkthrough of the procedures in starting the Bendu Olo Quest through the **Script Event node**.

  
Requirements:

-   Completion of the "Intermediate Quest Design" series with particular focus on the \[[Story Manager](http://www.creationkit.com/Bethesda_Tutorial_Story_Manager)\].

-   A working copy of the Bendu Quest that will either activate by the Startquest command through console or with "Start Game enabled" checked off.

-   A brief look at the \[[wiki description of the topic](http://www.creationkit.com/SM_Event_Node)\].

Completion of the "Scripting with Papyrus" series is also strongly recommended.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Seasoned stagers can bypass the above and transpose just the methods to their own works.</td></tr></tbody></table>

## The Nodes

-   Load up the quest and navigate to the Keyword entry under the Miscellaneous category in the Object Browser. Right click somewhere in the RH pane, New, and type the name of a keyword, in this case: _GSQ01Keyword_.

-   From the Character category in the Object Browser choose SM Event Node and double click on Script Event. Right click and create a new Branch node. It will be checked as **stacked** by default. The new node will appear below all other entries. I gave it a name of _GSQ01BranchStart_.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>We choose to work with the Script event as opposed to the other events on offer as it is much more versatile, and less buggy.</td></tr></tbody></table>

-   Right click on _GSQ01BranchStart_ and select **New Quest Node**. Give this a name of something like _GSQ01Start_. The GSQ part will at some stage appear as lower case for some reason. I checked **Num quests to run** and left it at 1. Ensure the **Stacked** Bullet is checked and, at the base of the page locate the **Shared** checkbox and click it. On lower resolutions accessing the bottom requires some sorcery.

-   Right click on the **GSQ01Start Node** Conditions area and implement a new condition with function _GetEventData_. The function parameters will be from top-down: _GetIsId_, _Keyword_, and _GSQ01Keyword_. Click Ok out.

-   Right click on the _GSQ01Start Node_ and select **Add Quests**. Choose _GSQ01_ from the list. Then select the newly created quest node, right click it, and choose **Edit Quest**.

  
This will bring up the quest tab, which serves as quite a useful shortcut to it, actually

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>It's important to <b>remove</b> an attached quest before deleting a node.</td></tr></tbody></table>

-   Select the **Quest Data** tab and from the event drop-down list choose **Script Event**. Notice that the **Start Game Enabled** box is now greyed out. Now Ok out of all windows back to the main CK window and save.

  
Now that the **Node** has been set up with the minimum amount of information required to activate the quest, let's work on our **Script Event**.

## The Quest Script

-   Open up the **Scripts** tab and select QF\_GSQ01\_01000D62. Click the **Properties** button to add two new properties:

```
   GSQ01KeywordLocal of type Keyword filled with the GSQ01Keyword object.
   MixWaterMill of type Location filled with the MixWaterMillLocation object

```

-   Edit the script **source** and add this code below all existing code:

```
    Function GSQ01Story()
    if (!GetStageDone(0))
    GSQ01KeywordLocal.SendStoryEvent(akLoc = MixWaterMill, akRef1 =None, akRef2 = None, aiValue1 = 0, aiValue2 = 0);
    endif
    endFunction
```

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Even though the quest may be stopped and/or in a disabled state, the mod is still active,<p>and the SendStoryEvent will transmit the data from the trigger zone to the node stack via the quest script.</p></td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>All of the parameters excepting akLoc are unused here and can be removed,<p>so GSQ01KeywordLocal.SendStoryEvent(akLoc = MixWaterMill) would work fine.</p><p>Including them here shows the potential capabilities of this function in more complex quest trigger scenarios.</p></td></tr></tbody></table>

-   Save it and exit: let's review we have done so far. See [notes](https://ck.uesp.net/wiki/Bendu_and_S_M_Nodes#Notes "Bendu and S M Nodes") regarding the extra entry in the conditions.

  
[![S M Node.jpg](https://ck.uesp.net/w/images/thumb/2/27/S_M_Node.jpg/900px-S_M_Node.jpg)](https://ck.uesp.net/wiki/File:S_M_Node.jpg)

## The Trigger

Now we turn our attention to selecting the quest trigger or activator in the _MixWaterMillLocation_. The activating object doesn't have to be there, indeed it could be anywhere in Tamriel, but in the spirit of the previous tutorials let's stay in the Mixwater lumber mill locale.

We would also prefer to use something inside the workers house like a chest, barrel, bed, or even Bendu himself. But as Bendu is a base object, and exists outside the quest when the mod is activated, it'll be Keith Szarabajkas's voice on the infos, making an early visit an immersion breaker. (Not to mention what happens post quest completion)

So let's look at something in the exterior. Candidates like chopping blocks, the lever on the lumber mill or any object in Gilfre's home are great. A one-off "Bendu sweetroll" found on the crate outside Gifre's home would be ideal, but we'll use something rather obvious here, Bendu's door.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>One drawback of opting for "well used" objects like doors as activators, is that Papyrus will log those events more often.<p>Also, the quest is being started unnecessarily every time we use the door during the quest.</p><p>To limit Papyrus logging, conditions on Quest Stages can be employed on the Quest Node. See Notes Below.</p></td></tr></tbody></table>

-   Locate and edit the **FarmhouseDoor01** object on the exterior of the MixwaterMill Workers House. Click the scripts tab and Add a new script. Call it _StartingGSQ01Quest_.

-   Add a new property to it:

```
   GetGSQ01of type Quest filled with the GSQ01 object.

```

-   Edit the script source of _StartingGSQ01Quest_ and add this code below the property:

```
    EVENT onActivate (objectReference akActionRef)
    Send_Story()
    EndEvent

    Function Send_Story()
    QF_GSQ01_01000D62 tempGSQ01 = GetGSQ01 as QF_GSQ01_01000D62
    tempGSQ01.GSQ01Story()
    tempGSQ01=None
    EndFunction
```

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>The long line of code beginning with <i>QF_GSQ01_01000D62</i> looks scary.<p>Here we replace the (empty) reference of <i>tempGSQ01</i> with the reference we <i>got</i> from <i>GetGSQ01</i>, a reference which is, in fact, directed toward our quest object, <i>GSQ01</i>.</p><p>Consider <i>QF_GSQ01_01000D62</i> as a "type". It's type is that of <b>script</b>.</p></td></tr></tbody></table>

  
If the line in _Send\_Story()_ were just

```
QF_GSQ01_01000D62 tempGSQ01 = GetGSQ01
```

That would be the same as:

```
QF_GSQ01_01000D62 tempGSQ01 = GetGSQ01 as Quest
```

The "as" operator is called a **cast** and the following statement looks for something in GSQ01 to "match" the **script** object _QF\_GSQ01\_01000D62_:

```
QF_GSQ01_01000D62 tempGSQ01 = GetGSQ01
```

Unfortunately Quest doesn't match and it won't compile because there is no implicit casting of _GetGSQ01_ to _QF\_GSQ01\_01000D62_

  
We expect the variable _tempGSQ01_ to be used just once, so it's good practice to clear any persistent reference to the local _GetGSQ01_ by "nulling" _tempGSQ01_ after _GSQ01Story_ is called.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>For more detailed info on casting refer <a rel="nofollow" href="http://www.cipscis.com/skyrim/tutorials/externalaccess.aspx">here</a>.<p>For a better picture of how script objects are organized in the CK, check <a rel="nofollow" href="http://www.creationkit.com/Category:Script_Objects">this</a> out.</p></td></tr></tbody></table>

-   Save the script. Our task is done and the modifications are ready for Bendu.

## Notes

-   We could, of course have put all the scripts in the _StartingGSQ01Quest_ script instead of the quest script.

The upside of our decision not to is that the properties and functions are available for re-use globally.

The downside is that for some reason the nice message in the Papyrus Log:

```
   [Date - Time] [StartingGSQ01Quest < (0001656B)>]: send_story Called - starting quest [Keyword <GSQ01Keyword (2E00A9D9)>]

```

only appears when the SendStory Event is generated from the trigger object.

-   Given a \[[problem](http://www.creationkit.com/Talk:SM_Event_Node#Conditions)\] experienced with conditions, the **if** condition in Function _GSQ01Story_() can be replaced by adding:

```
   GetStageDone {MyQuest 0} == 0

```

to the **Quest Node** for GSQ01 in **S M Event Nodes** for very much the same effect.