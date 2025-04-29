## Overview

This tutorial will show the reader how to set up [[Packages|packages]] (the data structures that control actor behavior) on an actor to get him moving around the world.

The reader will learn:
-   How [[Package Stack|package stacks]] work
-   How to create a simple daily schedule for an NPC
-   How to create a new package

## Packages and Package Stacks
A [[Packages|Package]] is the term used in the Creation Kit for the data structure that controls an actor's behavior. At any given time, an actor is always running one and only one package, which is what tells that actor what to do - sleep, eat, wander around, follow a patrol route, work a blacksmith's forge, etc.

So how does an actor know which package he should be running at any given time? That's where the [[Package Stack]] comes in. The basic idea is that each actor has a stack of packages that it could run. The game periodically runs down the list of packages, starting with the package at the top of the stack, and checks each package one at a time to see if it is currently valid. A package is valid if:

-   Its [[Conditions]] evaluate to true, and
-   The current time of day falls within its [[Package (Form)#Schedule Tab|schedule]].

An actor always runs the first valid package in the package stack. Actors near the player will reevaluate their package stack very frequently; actors in unloaded areas of the game world less frequently.

## Creating a Simple Schedule

So let's see how these ideas play out in practice by giving our old friend Bendu Olo a schedule. (Complete the [[2 Creating an Actor|Creating an Actor tutorial]] before continuing.)

Open GSQBenduOlo and go to the AI Packages tab, which currently looks like this:

[![Package Tutorial PackageList.jpg](https://ck.uesp.net/w/images/2/2d/Package_Tutorial_PackageList.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_PackageList.jpg)

Since he has no packages at all in his list, he'll simply stand in place all day long. Let's give him something to do, so he seems more like a human being.

To add packages to an actor, you can right-click on the Package List and select "Add", or drag packages into the list from the Object Window. Let's do the latter - select Package in the Object list (under the Character section). Scroll down to the packages named "Default...". (This is a naming convention we use to indicate packages that are not tied to a particular spot in the world, and thus can be used by any actor.)

[![Package Tutorial DefaultPackages.jpg](https://ck.uesp.net/w/images/1/16/Package_Tutorial_DefaultPackages.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_DefaultPackages.jpg)

We can build a simple schedule for Bendu Olo using these premade packages. Let's say we want him to eat breakfast and dinner at home, sleep at night, and otherwise just hang around his house.

For eating, let's check the existing default "eat" packages - let's pick **DefaultEatEditorLoc8x1** (breakfast) and **DefaultEatEditorLoc18x1** (dinner). Note: we use a naming convention to indicate packages which have a schedule: "STARTTIMExDURATION". So "8x1" indicates a package starting at 8 am and lasting for 1 hour; "18x1" indicates a package starting at 6 pm and also lasting for 1 hour. But of course the naming could be wrong - let's check the actual data on the packages to make sure their schedules match their names. 1 hour in game lasts 3 minutes in real life (20 minutes in-game equals 1 minute rl; 24h equals 72min).

Open the two packages and select their Schedule tabs, which look like this:

[![Package Tutorial DefaultEatEditorLoc8x1.jpg](https://ck.uesp.net/w/images/4/44/Package_Tutorial_DefaultEatEditorLoc8x1.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_DefaultEatEditorLoc8x1.jpg)

  
Their names didn't lie - these packages are valid at the times we expected. Great, so let's add these to Bendu Olo's package list, which now looks like this:

[![Package Tutorial PackageList2.jpg](https://ck.uesp.net/w/images/3/3a/Package_Tutorial_PackageList2.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_PackageList2.jpg)

Now as we discussed earlier, order is important in the package list, since the actor will always run the highest valid package in his list. For these two packages, however, it doesn't matter, because they are never valid at the same time - if it's between 8am and 9am, DefaultEatEditorLoc8x1 is valid; if it's between 6pm and 7pm, DefaultEatEditorLoc18x1 is valid; at any other time neither are valid. So the order of these packages doesn't matter. But stay tuned - for the next packages we add to Bendu Olo's list, the order will be crucial to making his schedule work correctly.

We said we wanted him to sleep at night, so let's find a sleep package in the "default" list - let's pick **DefaultSleepEditorLoc1x8**, which isn't actually the best choice but it will help illustrate the importance of stack order in the package list.

If you're paying close attention, you may have noted that this sleep package, which is valid from 1am to 9am, overlaps Bendu's breakfast package (DefaultEatEditorLoc8x1), which is valid from 8am to 9am. Here's where the order of the package stack starts to matter.

Say we put the sleep package at the top of Bendu's list, like this:

[![Package Tutorial PackageList3.jpg](https://ck.uesp.net/w/images/c/cc/Package_Tutorial_PackageList3.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_PackageList3.jpg)

Since the highest valid package "wins", at 8am Bendu will continue running his sleep package - the eat package lower in the stack will never be run, even though it is also valid at this time.

To make this work, all we have to do is make sure that the sleep package is below the breakfast package in Bendu's list, like this:

[![Package Tutorial PackageList4.jpg](https://ck.uesp.net/w/images/e/e6/Package_Tutorial_PackageList4.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_PackageList4.jpg)

Now, he will start his DefaultSleepEditorLoc1x8 at 1 am, as we intended - it's the only valid package at that time. When 8am rolls around, Bendu will switch to DefaultEatEditorLoc8x1, because it is now the highest valid package - so Bendu will only get 7 hours of sleep instead of the 8 specified by his sleep package, but he won't miss his breakfast.

We've now got a good chunk of Bendu's day covered - he eats for 2 hours a day, and sleeps for 7. We could continue to fill in his day with scheduled packages, but it's almost always a good idea to give him a "fallback" package to run when nothing else is valid. This package should have no conditions, and no schedule so it is always valid - and because of that, it should sit at the very bottom of his package list.

We often use a [[Sandbox (Procedure)|Sandbox]] package for just this purpose - it lets the NPC move around a space, picking semi-randomly what to do. Very useful when we don't particularly care what the NPC is doing but want him to continue to behave naturally.

For our purposes, **DefaultSandboxHomeowner** is a good choice. Let's open it up and take a look at its data:

[![Package Tutorial DefaultSandbox.jpg](https://ck.uesp.net/w/images/d/da/Package_Tutorial_DefaultSandbox.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_DefaultSandbox.jpg)

Its "Location" field specifies "Near editor location, radius 1500" - this means that he will "sandbox" around the spot he is placed in the editor, with a radius of 1500 units (which is usually enough to cover a small interior building). If you look at the other default packages in Bendu's list, you'll notice they're all using "Near editor location" - because they don't specify an exact location in the world, they can be used by any actor.

Another useful feature of this package is "Unlock On Arrival = True". This means that whenever he starts running this package, he will unlock his doors, which is good since he's supposed to be a questgiver - we don't want him hiding behind a locked door.

You can flip to its Conditions and Schedule tabs to verify that it has no conditions, and no specified schedule, which means that it is always valid (which is what we wanted).

So, let's drop this into Bendu's list at the bottom. He now has a complete, simple schedule:

[![Package Tutorial PackageList5.jpg](https://ck.uesp.net/w/images/b/bd/Package_Tutorial_PackageList5.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_PackageList5.jpg)

If you want to see him in action, load up the game and move yourself to him:

```
coc MixwaterMillWorkersHouse

```

To see his behavior at different times, you can change the time in the game as follows:

```
set gamehour to 2

```

He now has some simple eat/sleep/wander behaviors inside "his" house. If he does not want to sleep and asks you to leave, you can use the command _toggledetection_ so he ignores you.

## Making a New Package
We've seen how to use existing "default" packages to build a schedule. What about making a new package specifically for Bendu? Let's say we want him to patrol the exterior around his house at a specific time during the day.

First, make a new package by right-clicking on the Package list and selecting "New". You'll get a blank package window that looks like this:

[![Package Tutorial NewPackage1.jpg](https://ck.uesp.net/w/images/1/1e/Package_Tutorial_NewPackage1.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_NewPackage1.jpg)

By default, the Travel template is selected - but we want to make a Patrol, so change the dropdown to Patrol. Note that the list of Package Data changes - the Patrol template requires different data than the Travel template. Now we have a blank Patrol package, ready to fill in some data for the specific package for Bendu:

[![Package Tutorial NewPackage2.jpg](https://ck.uesp.net/w/images/6/6f/Package_Tutorial_NewPackage2.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_NewPackage2.jpg)

The [[Patrol (Procedure)|Patrol procedure page]] has the details for the data on this package. For now, the only things we need to specify on this package are:

-   Patrol Start - where should Bendu start his patrol route?
-   Schedule - what time of day should he run this package?

We haven't yet made a patrol route for Bendu, so let's load up the exterior and set up a simple one for him. (If you have the interior loaded, double-clicking on the yellow door marker is a quick way to get to the exterior; otherwise double-click on MixwaterMillExterior in the cell list for the Tamriel worldspace.)

If you're not familiar with linked references, the [[5 Basic Encounters|Encounters Tutorial]] is a good place to start. For now, let's just create a quick 3-point patrol route:

1.  Drop an XMarkerHeading into the render window.
2.  Duplicate it twice with CTRL-D.
3.  Move the 3 markers into a nice patrol route, then link them together using the Linked Ref tab on each reference.

You should end up with something looking like this (the exact locations of the patrol markers doesn't matter):

[![Package Tutorial NewPackage3.jpg](https://ck.uesp.net/w/images/3/39/Package_Tutorial_NewPackage3.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_NewPackage3.jpg)

Now, in the package window, select Patrol Start and click the button on the right (it will initially say "Linked Ref". This will allow you to select the data for the Patrol Start - select the "Specific Reference" radio button and select one of your new patrol points (it doesn't matter which since they are all linked together in a circle).

[![Package Tutorial NewPackage4.jpg](https://ck.uesp.net/w/images/f/ff/Package_Tutorial_NewPackage4.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_NewPackage4.jpg)

The second thing we wanted to do was specify when Bendu should run this package (otherwise this will be the only thing he does when we put it on his package stack). Switch to the Schedule tab in the package window, and let's say he should walk around outside during the morning between 10am and 12pm:

[![Package Tutorial NewPackage5.jpg](https://ck.uesp.net/w/images/d/da/Package_Tutorial_NewPackage5.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_NewPackage5.jpg)

The only thing left to do is give the package a name - let's say GSQBenduPatrol10x2, keeping with the standard naming conventions. Hit OK to close the window and we're done making a new package.

Now that we've made the new package, we have to add it to Bendu's package list in order to actually change his behavior. Find the new package in the Package section of the Object window, and drag it into Bendu's AI Package List. By default, all new packages are placed at the bottom of the actor's package list, but we want this new package to go to the top (or at least above the DefaultSandboxHomeowner package - otherwise it will never run because the DefaultSandboxHomeowner package is always valid). Use the << arrow key to move it to the top of Bendu's stack:

[![Package Tutorial NewPackage6.jpg](https://ck.uesp.net/w/images/3/31/Package_Tutorial_NewPackage6.jpg)](https://ck.uesp.net/wiki/File:Package_Tutorial_NewPackage6.jpg)

Hit OK to close Bendu's actor window and save your plugin. Go into the game to see Bendu do his new patrol:

```
coc MixwaterMillExterior
set gamehour to 10

```

That's it - you now know how to set up an actor's packages using existing or new packages. Most of the time, the premade [[Package Templates]] will provide all the functionality you need. But, if you find you need even more specialized behavior, you can even [[Creating a new Package Template|build your own Package Template]].