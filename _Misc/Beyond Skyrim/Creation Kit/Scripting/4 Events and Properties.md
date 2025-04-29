## Overview

This tutorial introduces Papyrus **Events** and **Properties**.

You will learn:
-   Basic information about Papyrus Events and how they are triggered.
-   Basic information about Papyrus Properties, and how to create, fill, and use them.
-   How the game interacts with Papyrus by communicating events.
-   How Papyrus interacts with the game by performing actions on properties.

This tutorial builds on the events in **Lokir's Tomb**, the sample dungeon created in the [[1 Layout Essentials|Level Design Tutorials]]. If you haven't completed that tutorial, you can [download a plugin with the finished level](https://en.uesp.net/wiki/File:SR-mod-LDWrapUpTutorialComplete.zip), but be aware that this tutorial assumes you are already familiar with the elements introduced there, including things like:

-   [[Creation Kit Interface|Basic editor navigation]].
-   Concepts like Ambushes, Activation, and Activate Parents.

## The Plan

Currently, when you enter the final chamber in Lokir's Tomb, the boss Draugr rises from his sarcophagus and attacks. Let's make this battle more exciting by introducing some unique scripted elements. We'll start by adding two dead Draugr to the room that we reanimate (with full spell effects) as the boss emerges from his tomb.

## Setting the Stage

First, let's set up the draugr we want to resurrect. In the editor, open the cell **LokirsTomb** and focus your view on the cave area; this is our boss chamber. In the [[Object Window]], navigate to **Actors>Actor** - or **All** - and use the filter to locate **"LvlDraugrMissileMale"** and **"LvlDraugrWarlockMale"**. Drag and drop one of each into the room.

Placed actors like these Draugr start alive (_well, relatively speaking_), and we need them to be dead. Double-click on each of them and check the box marked **"Starts Dead"**.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>Modders familiar with earlier BGS titles take note - simply setting the health of a base actor to zero will no longer cause the actor to begin dead. You must use the "Starts Dead" checkbox as specified here.</td></tr></tbody></table>

[[Getting Started#Creating and saving plugins|Save your plugin and run it in-game to check things out so far.]] You'll notice that two dead Draugr now lie in ragdoll on the floor of the room. That's what we want for now - but let's head back to the Creation Kit and get them back on their feet.

## Event Planning

[![](https://ck.uesp.net/w/images/thumb/5/56/EventDiagram.jpg/300px-EventDiagram.jpg)](https://ck.uesp.net/wiki/File:EventDiagram.jpg)

This diagram gives a very rough idea how events allow the Game and Papyrus to interact

### Introduction to Events

We want these Draugr to be resurrected as the boss emerges from his tomb. That is, we want this to happen in response to an **[[Events|Event]]**.

**[[Events]]** are actions or state changes that the game notifies Papyrus about. There are hundreds of different events, such as:

-   Interacting with an object or character (pulling a lever, opening a door, looting a body).
-   [Picking up](https://ck.uesp.net/wiki/OnItemAdded_-_ObjectReference "OnItemAdded - ObjectReference"), [equipping](https://ck.uesp.net/wiki/OnEquipped_-_ObjectReference "OnEquipped - ObjectReference"), [unequipping](https://ck.uesp.net/wiki/OnObjectUnequipped_-_Actor "OnObjectUnequipped - Actor"), or [dropping items](https://ck.uesp.net/wiki/OnItemRemoved_-_ObjectReference "OnItemRemoved - ObjectReference").
-   [Entering or leaving](https://ck.uesp.net/wiki/OnLocationChange_-_Actor "OnLocationChange - Actor") a [Location](https://ck.uesp.net/wiki/Location "Location").
-   [Entering or leaving combat](https://ck.uesp.net/wiki/OnCombatStateChanged_-_Actor "OnCombatStateChanged - Actor"), [getting hit in combat](https://ck.uesp.net/wiki/OnHit_-_ObjectReference "OnHit - ObjectReference"), [dying](https://ck.uesp.net/wiki/OnDeath_-_Actor "OnDeath - Actor").
-   [And much, much more.](https://ck.uesp.net/wiki/Category:Events "Category:Events")

Simply put - if we want to react to something in the game, Events are the way to do it.

### Triggering the Activation Event

You may not realize it, but our example already uses an event sent to Papyrus. This is how the boss knows when to get out of his sarcophagus. If you've done the [Ambushes Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Traps_and_Prefabs "Bethesda Tutorial Traps and Prefabs"), you may recall that the boss uses a trigger volume as its Activate Parent. When the player steps into the trigger volume, the trigger activates the boss, causing him to get up.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>There are pre-existing scripts at play here, but here's what's basically happening:<ul><li>The player collides with the trigger, causing an <a href="https://ck.uesp.net/wiki/OnTriggerEnter_-_ObjectReference" title="OnTriggerEnter - ObjectReference">onTriggerEnter</a> event</li><li>A script on trigger sends an Activate event in response to this.</li><li>The Draugr boss is an activate child of the trigger, and therefore also receives an activation</li><li>A script on the Draugr boss responds to the Activation by making him climb out of his tomb</li></ul></td></tr></tbody></table>

We can use the same trigger to also send [Activate](https://ck.uesp.net/wiki/OnActivate_-_ObjectReference "OnActivate - ObjectReference") events to our two dead draugr.

For each of the Draugr:

1.  **Double-click** on the Draugr to open its properties window.
2.  Locate and choose the **Activate Parents** tab.
3.  Right-click in the empty list and select 'New'. The Activate Ref Selection dialog appears.
4.  Click 'Select Reference in Render Window'
5.  When the Crosshair cursor appears, double-click on the trigger volume.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>If you don't see the trigger, remember to use "<b>M</b>" to toggle visibility for markers.</td></tr></tbody></table>

Both Draugr will now receive an Activate Event when the player enters the trigger. We aren't actually using that event to do anything yet, however. Next you'll write a script that responds to that event.

## Scripting the Resurrection

### Initial Setup

It's time to start scripting. Open your preferred text editor (we provide setups for [Notepad++](https://ck.uesp.net/wiki/Notepad%2B%2B_Setup "Notepad++ Setup") and [Sublime Text](https://ck.uesp.net/wiki/Sublime_Text_Setup "Sublime Text Setup")), and create a new file named "**LokirsDraugrResurrection.psc**".

Start with the following two lines of script:

```
scriptName LokirsDraugrResurrection extends Actor
{Resurrects the two dead Draugr in Lokir's Tomb.}
```

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td><ul><li><b>scriptName LokirsDraugrResurrection</b> - This is the name of the script. The name of the script must match the name of the file <i>exactly</i>.</li><li><b>extends Actor</b> - This script will be placed on an Actor (the Draugr), so it can do any of the things an Actor can do.</li><li><b>{...}</b> - The text in braces is just a file description - similar to a comment. It's not required, but it's good practice to have one here.</li></ul></td></tr></tbody></table>

We want to tell it to listen for the onActivate event. Activation occurs when another entity, such as the player or an NPC, tries to "use" or "activate" the object. In this case, the script on the ambush trigger will be sending the activation.

```
scriptName LokirsDraugrResurrection extends Actor
{Resurrects the two dead Draugr in Lokir's Tomb.}
 
Event OnActivate(ObjectReference akActionRef)
   ; Cast a Reanimate spell on the Draugr
EndEvent
```

### Casting the Spell

Next, we need to cast the Reanimate spell on the Draugr when the Activation event is received. To do this, we'll need to create a **"[Property](https://ck.uesp.net/wiki/Variables_and_Properties_(Papyrus) "Variables and Properties (Papyrus)")"**. In this case, it's a property of the [Spell](https://ck.uesp.net/wiki/Spell_Script "Spell Script") type we'll be using. This will allow us to tell the Creation Kit which specific spell to use.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td>For those who used the "<a href="https://ck.uesp.net/wiki/Papyrus_Glossary#L" title="Papyrus Glossary">legacy</a>" scripting language in editors for earlier Bethesda tools, this is a significant change. In Papyrus, you can't simply write in the Editor ID of the object you want to manipulate-- you have to use a property. This allows much more flexible and reusable scripts, since each instance of the script can have a different values for its properties. <a href="https://ck.uesp.net/wiki/Variables_and_Properties_(Papyrus)" title="Variables and Properties (Papyrus)">This page provides an overview of properties and variables in Papyrus</a></td></tr></tbody></table>

  
Begin by _"declaring"_ the Spell property, as below:

```
scriptName LokirsDraugrResurrection extends Actor
{Resurrects the two dead Draugr in Lokir's Tomb.}
 
Spell property reanimateSpell auto
 
EVENT OnActivate(ObjectReference akActionRef)
   ; Cast a Reanimate spell on the Draugr
EndEVENT
```

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td><ul><li><b>Spell</b> - Is the property <b><a href="https://ck.uesp.net/wiki/Category:Script_Objects" title="Category:Script Objects">type</a></b>. It tells Papyrus that we'll provide it with a <a href="https://ck.uesp.net/wiki/Spell_Script" title="Spell Script">Spell</a> to use.</li><li><b>property</b> - Is a <b><a rel="nofollow" href="http://en.wikipedia.org/wiki/Reserved_word">reserved word</a></b> this is how we tell Papyrus to expect a new property.</li><li><b>reanimateSpell</b> - This is the name we're giving to our variable. In-game, Papyrus will use our spell whenever we reference this property.</li><li><b>auto</b> - Another <b>reserved word</b> - it tells Papyrus to automatically generate 'get' and 'set' functions for the variable. Don't worry about the details here; this usually doesn't matter.</li><li><b>; ...</b> - Semicolons are the comment character in Papyrus. Use these to keep notes on what your script is doing. Anything after a semicolon is ignored by the game, so you can write whatever you want.</li></ul></td></tr></tbody></table>

We've defined a spell, but it isn't doing anything yet. Spell properites can use the [Cast](https://ck.uesp.net/wiki/Cast_-_Spell "Cast - Spell") function, which we'll use next. Copy the new line of script inside the onActivate event below:

```
scriptName LokirsDraugrResurrection extends Actor
{Resurrects the two dead Draugr in Lokir's Tomb.}
 
Spell property reanimateSpell Auto
 
EVENT OnActivate(ObjectReference akActionRef)
   ; Cast a Reanimate spell on the Draugr
   reanimateSpell.Cast(Self, Self)
EndEVENT
```

Like many functions, we have to pass one or more "_arguments_" to let the function know what to do. In this case, [Cast](https://ck.uesp.net/wiki/Cast_-_Spell "Cast - Spell") requires a source and a target. For this example, we just needed the draugr to "cast" the spell at itself. The reserved word **"Self"** is useful in this case; by passing it into both fields, Papyrus automatically knows we want to reference the same entity the script is attached to. In this case, then, "self" is the same as creating a new property for the draugr we'll be resurrecting - only much simpler.

Save and compile the script, then return to the Creation Kit.

### Attaching the Script

Back in the Editor, double-click on one of the Draugr to open its Properties window, then go to the Scripts tab (you can hit the 'End' key to jump right there; it's the last tab in the list). This is where we'll hook up our script:

1.  Click **Add**.
2.  In the **Add script...** Window, enter the name of our new script, 'LokirsDraugrResurrection'.
3.  Double-click on the script to add it to the Draugr.

That's attached the script to this reference, but we still need to tell the Creation Kit what spell to cast. We'll be using "dunReanimateSelf", a special non-playable spell created especially for events like this one.  

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>If you do not do what follows, any properties (any external resource) that you use in your script will NOT register correctly. (This is because properties are <b>local</b> names only). Even if the property has the same name as an existing external object, it will not work properly without this step.</td></tr></tbody></table>

1.  Select _LokirsDraugrResurrection_ in the _Scripts_ Tab.
2.  Click **Properties**.
3.  The list that appears only has a single property - _reanimateSpell_.
4.  Select reanimateSpell and click **Edit Value**.
5.  Notice that this list only displays valid forms - spells, in this case.
6.  Select **dunReanimateSelf**. Click OK.

Repeat this process for the other Draugr. Save your work and give it a try in the game!

## Debugging the Resurrection

At first glance, everything probably worked out as expected. However, if you kept playing, you may have noticed that the resurrection will occur _any_ time the draugr receives an activate event. This includes when the player loots the body! That's not the sort of nasty surprise we intended on! Unexpected bugs like this can be handled using a bit of extra logic, however.

There are a number of ways we could fix this, like making sure the resurrection only happens once by using a [control variable](https://ck.uesp.net/wiki/Papyrus_Glossary#C "Papyrus Glossary"). We could also make sure the script ignores activation from the player, but that could still result in accidental re-resurrection by an NPC.

Instead, we'll ensure that the resurrection only occurs when the triggerbox sends the activation. We'll do this by creating another property - an [Object Reference](https://ck.uesp.net/wiki/ObjectReference_Script "ObjectReference Script") this time - which we'll assign to our trigger.

We'll compare this new property to **"akActionRef"**, the _parameter_ supplied by the _OnActivate()_ event. This parameter is a sort of special variable, usable only within this onActivate event, which Papyrus automatically assigns to the reference responsible for the activation.

```
scriptName LokirsDraugrResurrection extends Actor
{This Script lives on the dead minion draugr in Lokir's Tomb. It handles their resurrection}
 
Spell property reanimateSpell Auto          ; this is the special self-resurrection spell to use
objectReference property myTrigger auto     ; This is the reference we are waiting on to send an activate
 
Event OnActivate(ObjectReference akActionRef)
   ; I've been activated - see if was my trigger
   if (akActionRef == myTrigger)
      ; Cast a Reanimate spell on the Draugr
      reanimateSpell.Cast(Self, Self)
   EndIf
EndEvent
```

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td><ul><li><b>objectReference</b> - This is the data type of our new property.</li><li><b>myTrigger</b> - As before, this is a name we've chosen for our new property.</li><li><b>if</b> - This is the beginning of an <b>"if statement</b>. If the statement beneath the if is true, then the script will run. Otherwise, Papyrus skips ahead and resumes processing commands after the corresponding <b>"endIf"</b> below.</li><li><b>(akActionRef == myTrigger)</b> - This is our test condition. The "==" is a logical operator which translates to "is equal to". In this case, it's telling the <b>"if"</b> statement to continue only if <i>akActionRef</i> and <i>myTrigger</i> are filled with the same reference.</li><li><b>endIf</b> - This is necessary to close any <b>"if"</b> statement. It's possible to have multiple if statements within each other for more complicated operations, so it becomes important to keep track of your logic using these. When an <b>"if"</b> statement is beneath another <b>"if"</b> statement, it is said to be nested.</li></ul></td></tr></tbody></table>

Now, the last thing we need to do is assign a value to our new property. To do so, let's go back to the Creation Kit, and double click either of our two dead Draugr. Get to the scripts tab and select our **LokirsDraugrResurrection** script. Then hit properties. Then select our new **myTrigger** property and hit "Edit Value". Now, select "Pick Reference in Render Window". Finally, double click our blue activation box that triggers our boss Draugr to come forth from his tomb.

Save the plugin, then go ahead and test it.

You will find that the Draugr will be resurrected only once. The reason why the Draugr aren't resurrected (and the boss Draugr trap triggered) every time the player moves through the activation box is because of a property of the script attached to it called **doOnce**. It is probably a good idea to check the script attached to our triggerbox (**defaultActivateSelf**) out in more detail to see how you can assign default, or automatic, values to properties.