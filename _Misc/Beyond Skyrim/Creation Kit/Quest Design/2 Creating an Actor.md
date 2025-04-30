## Overview

This chapter will show you how to make NPCs in the editor, both civilians (not meant to provide a combat challenge to the player) and enemies.

The reader will learn:
-   How NPCs are created in the editor
-   How to set up basic combat stats on an NPC

## Actors

In Skyrim, all moving creatures are set up as a special kind of object called an Actor. All animals and humanoids use this object, and it's where appearance, behaviors, and everything else about a character is defined.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td>If you're familiar with Fallout 3 and earlier engines, Creatures and NPCs have been combined into Actors, which gives you a lot more flexibility in creating their behaviors.</td></tr></tbody></table>

In the [[Object Window]], navigate to Actors -> Actor in the category list. Right-click anywhere in the list of actors and select "New".

## Creating Bendu Olo

Thankfully, a lot of the fields in the [[Actor Window]] are pretty self-explanatory. That said, there's a decent amount of setup that you need to do to make someone. So here we go.

[![EmptyActor.png](https://ck.uesp.net/w/images/thumb/2/2c/EmptyActor.png/700px-EmptyActor.png)](https://ck.uesp.net/wiki/File:EmptyActor.png)

- **ID: GSQBenduOlo** Just like with the quest ID, this needs to be unique across the game. Give him the ID GSQBenduOlo. (Note that IDs can't have spaces or special characters in them.)
- **Name: Bendu Olo** The name that will be visible to the player. "Bendu Olo" in our case.
- **Short Name: Bendu** How somebody familiar with this character might refer to them. This gets used by the radiant story system, which we'll come back to later. For now, just call him "Bendu".
- **Unique:** This is the only checkbox you need to worry about for now. It lets the engine know that there should only be one of this actor in the world (as opposed to a new type of animal we were making, for instance). Make sure this is checked.

There are a few things we need to set up in the [[Traits Tab]], just to the right.

- **Race:DarkElfRace** Pretty self-explanatory -- sets the race that this actor will be. Select "DarkElfRace" from the pull-down menu. Now Bendu will have the appearance and racial bonuses of a Dark Elf.
- **Voice Type:MaleDarkElf** This determines what generic dialogue and combat barks this actor will have available to them. Set him up as a MaleDarkElf.

[![StartedActor.png](https://ck.uesp.net/w/images/thumb/4/44/StartedActor.png/600px-StartedActor.png)](https://ck.uesp.net/wiki/File:StartedActor.png)

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>In most cases, characters are not prefixed with an identifier because they are often used by multiple quests. Since Bendu might have a bright future ahead of him, we might consider just calling him "BenduOlo".</td></tr></tbody></table>

Finally, hop over to the [[Inventory Tab]]. Here we'll give him some clothes so he's not just running around in his underwear.

What an actor chooses to wear is determined by their [[Outfit]]. Skyrim ships with a number of snazzy outfits already defined, but you can make your own fairly easily if you want to. For now, give him some plain clothes with a hat by choosing "FarmClothesOutfit01WithHat" from the Default Outfit pulldown menu.

Make sure to hit "OK" instead of "Cancel" or just closing the window, or your work will be discarded. (This goes for most of the Creation Kit. The rest of the tutorials won't always remind you of this, so keep on your toes!)

## Placing the Actor

What we've done here is create the base object for the actor; to actually place him in the game, we'll need to create a reference for him. (If you're unfamiliar with the difference between a base object and a reference, see the callout box labeled [[Creation Kit Interface#^7fbf8f|Base Object vs Reference]].)

We're going to place Bendu into an existing space. In Mixwater Mill, there's a house that used to have workers there, but has since been abandoned. Let's make it Bendu's home.

Look at the [[Cell View Window]]. Make sure that the pulldown menu to the right of "World Space" says "Interiors," then select "MixwaterMillWorkersHouse" from the cell list. Double click to load it up.

[![CellViewSelected.png](https://ck.uesp.net/w/images/thumb/1/17/CellViewSelected.png/600px-CellViewSelected.png)](https://ck.uesp.net/wiki/File:CellViewSelected.png)

Zoom out a little bit so you can see more of the interior space. (If you need help navigating around the render window, you can review [[Creation Kit Interface#Navigating the Render Window|the earlier tutorial]] on it.)

[![MixwaterInterior.png](https://ck.uesp.net/w/images/thumb/6/61/MixwaterInterior.png/500px-MixwaterInterior.png)](https://ck.uesp.net/wiki/File:MixwaterInterior.png)

Adding our good Mr. Olo to the cell is as simple as grabbing GSQBenduOlo in the object window and dragging it to a place in the render window.

[![MixwaterInteriorPlusBendu.png](https://ck.uesp.net/w/images/thumb/5/56/MixwaterInteriorPlusBendu.png/500px-MixwaterInteriorPlusBendu.png)](https://ck.uesp.net/wiki/File:MixwaterInteriorPlusBendu.png)

## Testing the Actor In-Game

If you're eager to meet your new creation, that's easy enough. Just make sure [[Getting Started#Loading a plugin in the game|your plugin is loaded]], and start the game. Once you do, start the game, pull up the console, and:

```
COC MixwaterMillWorkersHouse

```

Inside, you should find Bendu wandering around, maybe sitting in a chair. He won't have much to say to you, since we haven't written any dialogue for him, and won't have much to do, since we haven't given him any activities. But you have now created a new NPC, so congrats.

[![BenduInGame.png](https://ck.uesp.net/w/images/thumb/f/f0/BenduInGame.png/500px-BenduInGame.png)](https://ck.uesp.net/wiki/File:BenduInGame.png)

## Making an Enemy
Now we're going to make the thief who stole Bendu's amulet. Create a new actor like you did before, and give it the ID "GSQThief" and the name "Dirty Thief".

Now things get a little more interesting, though. Instead of specifying the rest of the thief's data, we're going to use a template. In the bottom left of the Actor window, you can see a "Template Data" section.

[![ActorWindowTemplateArea.png](https://ck.uesp.net/w/images/thumb/7/7d/ActorWindowTemplateArea.png/600px-ActorWindowTemplateArea.png)](https://ck.uesp.net/wiki/File:ActorWindowTemplateArea.png)

Using a template lets us base this actor off another one. It's great for any kind of actor you plan to be a combatant, because you can easily use existing leveled lists and stats, just changing the bits that you want.

So from the ActorBase pulldown list, choose "LvlBanditMelee1H". That name is kind of a mouthful, but is easily broken down:

-   **Lvl:** This actor uses a leveled list, so as the player becomes more powerful, this actor will increase in difficulty accordingly. (Leveled lists are too complicated to get into here; if you're interested, their [[Leveled Lists|details are documented]].
-   **Bandit:** This actor's appearance and gear fit the archetype we generally think of for bandit characters in the world, and will show up as "Bandit" in the player's combat interface.
-   **Melee:** This actor will use melee attacks as opposed to ranged or magic attacks.
-   **1H:** This actor will use a one-handed weapon.

Within that, there's a lot of variation and randomness. You might get a female Khajiit one time, a male Nord another. Using leveled templates let us provide suitable challenges to the player regardless of their progress, as well as a bit of variety.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>Note that most leveled templates can resolve to a multitude of voice types, so you need to be careful when writing dialogue for templated actors. In our case, this actor is just a quest obstacle, so we don't care.</td></tr></tbody></table>

Having chosen a template, we need to select which aspects of that template we want to use, by checking the appropriate boxes in the template area. Check every box except for "Use Script" and "Use Base Data".

[![TemplatedActorFilled.png](https://ck.uesp.net/w/images/thumb/1/16/TemplatedActorFilled.png/300px-TemplatedActorFilled.png)](https://ck.uesp.net/wiki/File:TemplatedActorFilled.png)

We don't have to worry about setting race, inventory, equipment, or anything else, since we're pulling all that from the template!

Click "OK" to save the thief actor.

## Placing the Enemy
There aren't many unoccupied "dungeon" spaces in Skyrim, but one is available far out in the Reach. Load the cell "ReachwindEyrie01" and place a reference to the thief object the same way we placed Bendu into the Mixwater Mill cell.

[![TemplatedActorPlaced.png](https://ck.uesp.net/w/images/thumb/2/27/TemplatedActorPlaced.png/500px-TemplatedActorPlaced.png)](https://ck.uesp.net/wiki/File:TemplatedActorPlaced.png)

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>You'll notice that the reference appears in the editor as a green <i>M</i>. Because this actor is templated, the editor doesn't know what it looks like, so it draws a capital <i>M</i> for historical reasons since lost to the vortex of time (theories range from "MOB" (Mobile Object) to "ninja monkey" to "monster" to "marker"). It's green because the default difficulty for leveled actors is "Easy".</td></tr></tbody></table>

If you want to visit the new baddie you've created, start up the game with your plugin and:

```
COC ReachwindEyrie01

```

Be ready for a fight!

[![DirtyThiefInGame.png](https://ck.uesp.net/w/images/thumb/7/77/DirtyThiefInGame.png/500px-DirtyThiefInGame.png)](https://ck.uesp.net/wiki/File:DirtyThiefInGame.png)

## Bugs/Issues
The [[Dark Face Bug]]: There is currently an issue where created actors do not export their facial data (scars, make-up, tones etc) onto the rendered NPCs in game. This can be temporarily rectified by opening the console and selecting the actor in-game, and typing "setnpcweight x" for the selected NPC. However, this only sets the skin tones to a normalized state, with no facial traits.

This can also be permanently rectified by exporting the facial data manually. Highlight your actor(s) in the **Object Window listing** and then press **CTRL+F4**. Unfortunately this might not work, until you've saved your plugin file, and restarted the Creation Kit.