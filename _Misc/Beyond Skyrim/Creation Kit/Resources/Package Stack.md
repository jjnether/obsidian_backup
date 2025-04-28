## Summary

[![](https://ck.uesp.net/w/images/thumb/0/0f/ActorPackages.jpg/300px-ActorPackages.jpg)](https://ck.uesp.net/wiki/File:ActorPackages.jpg)

A Package Stack is the term used to describe the stack of packages that "live on" an actor reference.

This stack is formed by adding Alias Package Lists to the top of Actor Package Lists which are added on top of default package lists.

After processing all the packages' schedule and [conditions](https://ck.uesp.net/wiki/Category:Conditions "Category:Conditions") and removing ones which are unavailable during the current day/time or whose conditions evaluate to false, the actor picks the top most package left on the stack.

This is a very powerful (if at first confusing) way to organize an actors set of behaviors, because you don't have to poke an actor every time he needs to do something else. The dynamic stack of packages is constantly updating based on schedules and conditions of individual packages causing them to be removed or returned to the stack.

The basic approach is to put "default" or fall through behavior, like "HangOutAtHome," at the bottom of the stack. And put very specific things like "EscortPlayerToDungeon" on top of the stack. In this method, you use conditions to turn off the specific things, and use the bottom of the stack to make sure the actor has something to do at all times that makes sense.

[![](https://ck.uesp.net/w/images/thumb/e/e7/PackageSchedule.jpg/300px-PackageSchedule.jpg)](https://ck.uesp.net/wiki/File:PackageSchedule.jpg)

Example of Package Schedule

[![](https://ck.uesp.net/w/images/thumb/5/53/PackageConditions.jpg/300px-PackageConditions.jpg)](https://ck.uesp.net/wiki/File:PackageConditions.jpg)

Example of Package Conditions

## Example of stack

For example, a stack might look like:

1.  Escort Player to Dungeon : IF QuestStage MyQuest == 120
2.  Eat at tavern : 12:00 for 2 hours
3.  Sleep in bed : 20:00 for 8 hours
4.  Sandbox at home : no conditions or schedule

So no matter what, if MyQuest is stage 120, he will run the Escort Player to Dungeon package, otherwise if it's lunch time he'll be eating at the tavern, or sleeping at night, and if all else fails, will be hanging out at his house.

## Various Stacks

In Oblivion and Fallout, each actor only had a single stack of packages that lived on his base NPC form. In TESV an Actor form has a stack of packages, but also, an actor's reference can pick up packages from any quest Alias he happens to be in at the time.

Quest Alias Package Stacks sit on top of an Actors base package list, and if an Actor is in multiple Aliases at the same time, the alias a package stacks are arranged according the quests' priority data field. (Higher priority quest's have their alias package stacks sitting higher up on the actor's package stack)

Additionally, and actor has a "default package list" which is a [FormList](https://ck.uesp.net/wiki/FormList "FormList") of packages that acts as a package stack. This sits underneath the actor form's AI Packages stack. And below that, lives a default default package stack which is defined by the [Default Object](https://ck.uesp.net/w/index.php?title=Default_Object&action=edit&redlink=1 "Default Object (page does not exist)") "Default Pack List" which in the shipped game is set to the Form List named "Default MasterPackageList"

And lastly, on top of everything, sit any packages that are running on the actor because he is in a [Scene](https://ck.uesp.net/wiki/Category:Scenes "Category:Scenes").

## Stack Order Overview

[![](https://ck.uesp.net/w/images/thumb/0/0f/ActorPackages.jpg/300px-ActorPackages.jpg)](https://ck.uesp.net/wiki/File:ActorPackages.jpg)

[![](https://ck.uesp.net/w/images/thumb/8/8e/AliasPackages.jpg/300px-AliasPackages.jpg)](https://ck.uesp.net/wiki/File:AliasPackages.jpg)

[![](https://ck.uesp.net/w/images/thumb/d/da/ActorDefaultPackages.jpg/300px-ActorDefaultPackages.jpg)](https://ck.uesp.net/wiki/File:ActorDefaultPackages.jpg)

Actor Default Package List

[![](https://ck.uesp.net/w/images/thumb/6/63/DefaultPackages.jpg/300px-DefaultPackages.jpg)](https://ck.uesp.net/wiki/File:DefaultPackages.jpg)

Default Default Package List

  
So the stacking order of the various package lists that will ultimately live on an actor reference is as follows (see images to right):

1.  Packages in currently running [Scene Actions](https://ck.uesp.net/wiki/Scenes_Tab#Package_Action "Scenes Tab").
2.  Quest Alias Package List (if multiple aliases, use quest priority to sort)
3.  Actor Form AI Package Tab main list
4.  Packages in the Form List selected in the AI Package Tab's "Default Package List" drop down
5.  Packages in the Form List set to be the Default Object "Default Pack List"

## Best Practice

Because packages can be dynamically added at run time via quest aliases, it's best practice to put all important quest packages inside alias package lists, rather than directly on an actor, so that the quest priority data can assist in determining which packages are on top of the stack. This is also why it so important to carefully conditionalize quest aliases so you don't grab someone important who might be busy doing something else and why it's so important to reserve your aliases in your quests. See [Category: Radiant Story](https://ck.uesp.net/wiki/Category:Radiant_Story "Category:Radiant Story") for more information on aliases.