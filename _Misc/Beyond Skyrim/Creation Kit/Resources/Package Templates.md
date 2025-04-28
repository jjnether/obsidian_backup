## Introduction

For an overview of the Package system in general, and to see what's new in Creation Kit, see [Category:Packages](https://ck.uesp.net/wiki/Category:Packages "Category:Packages")

A _Package Template_ is the cookie-cutter version of how to define behavior for AI. It is essentially a _Package_ whose purpose is to be the basis for other _Packages_ that need to keep the same basic behavior, but change a few details.

99% of the time, you will want a package that does the same basic thing on one actor, as it does for another. This is what Package Templates are for.

For example when you tell Actor A to travel to some place, he is essentially doing the same thing that Actor B needs to do when traveling someplace else. The only particular difference is WHERE he is traveling to.

Templates are perfect for this, because a template defines the overall behavior for an actor, and supplies data where you can specifiy the specifics for the behavior.

For example, there is a package template called **Travel** that you can use to tell an actor to go to a specific location. You can use the **Travel** template to make your own package, and then define specific pieces of data, such as where to travel and how close the actor must get to the destination before the package is considered "done".

Therefore, we create a "Template" travel package, which anyone can derive their own packages from. The template provides the procedure tree, and exposes "public" data the derived package can set. In the case of the Travel Template package, it exposes the Location to travel to. ("Private" data is not exposed. This is data used by the procedure tree that does not want to be changed by users of the template.)

In Oblivion and Fallout, ALL packages were based on templates. You just never saw those templates in the editor. Now you can create a package and declare it a template so that you can use it to derive other packages.

## Summary

**A _Package_**:

-   is made up of _procedures_ arranged in a procedure tree.
    -   Example Procedure: _Travel_ which takes a data input of where to travel
-   Uses _Data_ inputs that are used by the procedures to define various parameters the procedures will use to get the desired behavior.
    -   Example: "Desintation" data to feed to a _Travel_ procedure.
-   May or may not be based on a _Package Template_
    -   When a _Package_ derives from a _Template_
        -   Package Template Data _Data_ is either:
            -   _Public_ meaning exposed to packages that use the Template so users can supply "paramters" to procedures
            -   _Private_ meaning not exposed, so that users can not supply their own values for these "parameters

**A _Package Template_**

-   is a _Package_ that is marked as a "Template"
-   is intended to be reused in a more generic fashion
-   it's data becomes the default data for future packages based on this template.

**Conditions**: You can add control through the use of [Conditions](https://ck.uesp.net/wiki/Category:Conditions "Category:Conditions") at the package level, or on [Procedures](https://ck.uesp.net/wiki/Category:Procedures "Category:Procedures") and branches in the [procedure tree](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Trees).

Note: adding a condition to the conditions tab of a Package Template is meaningless.

## Using Package Templates

Most of the time when you need a new package, you will be using an existing template. If you have used packages in Fallout, choosing from a list of package templates is very similar to choosing from the list of packages available to you in Fallout.

The vast majority of things you will want actors to do can be achieved by using one of the Templates that the base game has shipped with. From Traveling, Eating, to Patroling a path of markers, to Escorting, and Forcegreeting the player with dialogue, to more complex things like Sandboxing at multiple locations has all been created as Templates and ready for use.

## Make a New Package Using an Existing Template

Most of your package creation needs will follow this method:

In the **Object Window**, go to **Character -> Package**. Right click on the window and select **New**.  
Name your package, and then go to the **Package Template** dropdown menu. Select an appropriate template to use for your package.

[![PackageFromTemplate01.jpg](https://ck.uesp.net/w/images/thumb/8/85/PackageFromTemplate01.jpg/300px-PackageFromTemplate01.jpg)](https://ck.uesp.net/wiki/File:PackageFromTemplate01.jpg)

You will see that the **Procedure Tree** box is grayed out, but now has data in it. You will also note that **Public Package Data** also has data in it. This is the data that you can change in your package that will make it specific to your purposes. In the example below, there is one piece of Public Package Data called **Place to Travel**. It uses the data type **Location** which you can edit for your specific package.

[![PackageFromTemplate02.jpg](https://ck.uesp.net/w/images/thumb/4/4d/PackageFromTemplate02.jpg/300px-PackageFromTemplate02.jpg)](https://ck.uesp.net/wiki/File:PackageFromTemplate02.jpg)

## Creating a Package Without Using a Template
If for some reason the current available templates aren't sufficient to get the job done, you can make your own package. There are a few ways to go about doing this, but starting out with a templated package and removing the template is the easiest method. If the package you want to make is totally unlike any package template out there, then you'll want to start making your package from scratch. When creating your own packages, there are various building blocks that you can use. There is a full list and description of them see [Category:Procedures](https://ck.uesp.net/wiki/Category:Procedures "Category:Procedures").

## Removing a Template From a Templated Package

If there's a package that exists that is very similar to one that you need, you could first template the package that's similar to the one you want, and then set the template field to "None".

You'll notice that the procedure tree that used to be gray is no longer gray. You can now edit the procedure tree. You also have total control over altering all aspects of the public package data instead of just the values. Thunder rumbles in the distance.

[Tutorial - One-off Package based on Existing Template](https://ck.uesp.net/wiki/Tutorial_-_One-off_Package_based_on_Existing_Template "Tutorial - One-off Package based on Existing Template")

## Starting From Scratch

This is very similar to removing the template from a package, but instead you start with a clean slate. Right click on the Procedure Tree window to add procedures and branches.

## Creating a Package Template

If you have been working on a new package and want to make it a Template, all you need to do is change the Package Type dropdown from "Package" to "Package Template" when you decide that there is a package that is worthy of becoming a template.

  
**Guidelines for making a Package Template:**

-   Many new packages don't need to become a template. If you plan on making a package and constantly renaming that package for twenty variations of essentially the same package, then it's appropriate to make a new template.
-   When setting up a template, make sure that the public package data makes sense in a generic manner.
    -   Set travel destinations to generic thing like "Editor Location" or "Linked Ref". If someone templates a Package Template and forgets to set, for example, a travel destination, it would be better for that actor to travel to their editor location instead of an xMarker in the center of Whiterun.
    -   Set Location radii (and other radii) to small values (32 ~ 256). If they are left at 0, Actors often have a tough time traveling to **exactly** that xMarker.
    -   Set radii for searches to reasonable default search values.

## Procedure Trees

When creating your own packages, there are two basic building blocks that you can use. Procedures, which are the building blocks of specific behavior, and Branches, which are nodes in which you can collect procedures. The type of node determines the logic of how the procedures inside them are processed.

Both procedures and branches can have conditions, which, in conjunction with careful use of branch types, can make for an extremely powerful tool for creating complex behaviors.

## Procedures

Procedures are the main components of how a package is put together. These define what behaviors the package will make an actor do.

For a list of procedures, see the pages in [Category:Procedures](https://ck.uesp.net/wiki/Category:Procedures "Category:Procedures")

## Branches

Branches arrange procedures in a logical fashion.

-   **Random** - This branch will run and pick one and only one valid branch or procedure to do. Once it does that branch or procedure, the branch will finish.
-   **Sequence** - This branch will do all branches and procedures in a sequence. Once it gets to the last thing, the whole sequence branch will finish.
-   **Simultaneous** - This branch is sort of tricky. You can currently make any procedures run at the same time (although you should be careful with this). Usually, you would want to do a combo of something like Patrol and Find, which would make an Actor patrol until he finds the thing he's looking for. A simultaneous branch is finished when **any** of its child procedures or branches is completed. A simultaneous branch will not end if one of its procedures becomes invalid due to conditions causing the procedure to become invalid.
-   **Stacked** - This is very similar to the package stack. When a stack branch is run, it picks the first valid branch or procedure in the stack and does it. After that, the stacked branch is considered complete.

  
What happens when the whole series of branches and procedures is complete? The package runs again as long as it remains the top-most package on the package stack.  

## Package Data

Package data is used by procedures in order to carry out behavior in specific ways. Data can be of various types. Each procedure "parameter" requires specific types of data. Many data types like **int** and **float** are fairly common, while others such as **ObjectList** and **TargetSelector** are very specific to packages.

-   **Bool** - This is represented by a checkbox in the editor. A checked box means "True".
-   **Float** - This is a numerical value that can take a decimal place. It is often used for time and distance.
-   **Int** - This is a numerical value that does not allow decimal places. It is often used for counting.
-   **Location** - This is a more procedure-specific data type. It is often defined as a reference combined with a radius, and is usually used as an area that AI uses to search, or some sort of destination. There is often a radius which is included as part of the location, and should usually be set to some small number rather than zero. If set to zero (or when using a Ref as a location) a default radius is assigned from a gamesetting, based on the ref's type:

```
XMarker and XMarkerHeading:fAIMarkerDestinationRadius.
Furniture:fAIFurnitureDestinationRadius.
Actors:fAIDistanceRadiusMinLocation + the Actor's radius.
Everything else:fAIDistanceRadiusMinLocation.

```

("Everything else" includes non-ref-based locations, like "current location")

-   **ObjectList** - This is a tricky one. If you are only using package templates, you won't have to know what this does. This object list stores data that is placed in the list by a procedure inside the package. For example, if you're trying to find a place to sit, an object list will be used by the find procedure to remember any chairs that were found by the find procedure. In a sit procedure, you can use the object list as the piece of furniture to sit in. If the object list is empty, the sit procedure would **fail**.
-   **Ref** - This is a reference in the editor.
-   **TargetSelector** - A target selector is most often used when the actor is trying to find something. It is the answer to the question "What type of thing would you like to find?" This answer could be any sort of thing, like beds, ammo, food, something with a particular base ID, or a specific reference.

## Procedure Parameter Types

Prepare for a bit of deja vu. As stated in the Package Data section immediately above, you tell a procedure what to do by assigning package data to procedure parameters. So of course you are expecting, quite reasonably, that procedures are asking for exactly the same types of data that the package data provides. And you would be right -- with one additional bit of coolness, which is: some procedure parameter types can accept more than one type of package data.

-   _Bool_ - Bool parameters accept only Bool package data.
-   _Float_ - Float parameters accept only Float package data.
-   _Int_ - Int parameters accept only Int package data.
-   _Target_ - Here is where things get interesting. You'll note that there is no single package data type named "Target." This is because _several_ package data types are valid for use when a procedure wants a Target:
    -   **ObjectList** - Use an ObjectList as a Target when you want the actor to Find multiple potential targets based on their type. There are two ways that procedures can handle an ObjectList:
        -   Some procedures are specifically able to act on multiple targets (e.g. Acquire, which can pick up multiple objects, or Escort, which can escort multiple actors). These will work through the ObjectList over time, automatically removing any items that are no longer valid (e.g. something the player picked up before the NPC could get to it) and acting on the valid targets, until they have acted on the requested number of targets (e.g. until Acquire has picked up the requested number of items, or until Escort has gathered the requested number of followers).
        -   Other procedures only ever need a single target. These can still accept an ObjectList as their Target; they will simply try each item in the ObjectList until they find one that is valid for their purposes; they will then operate on that object.
    -   **Ref** - use a Ref as a target if you want to create a simpler package (or template) in which the target must be specified explicitly (by name, linked-ref, quest alias, etc.) rather than by being found at run-time with a Find procedure.
-   _Location_ - This, too, can accept more than one type of package data.
    -   **Location** - Naturally, when a procedure wants a Location, it can accept a Location.
    -   **Ref** - In addition, anything that is a valid Target can also be used as a Location. For instance, you could set up a Travel package that accepts a Ref as a destination. However, be cautious when you do this, because the location's radius is assigned automatically, from a game settting, based on the ref's type:

```
XMarker and XMarkerHeading:fAIMarkerDestinationRadius.
Furniture:fAIFurnitureDestinationRadius.
Actors:fAIDistanceRadiusMinLocation + the Actor's radius.
Everything else:fAIDistanceRadiusMinLocation.

```

("Everything else" includes non-ref-based locations, like "current location")

-   -   **ObjectList** - If you provide an ObjectList as a location, the location will be the first valid entry in the list. **Note**: an ObjectList can now define a radius, for use when using it as a Location. However, if you leave the radius set to the default (zero) then the location's radius is assigned automatically, from a game settting, based on the ref's type: (See above.)
-   _TargetSelector_ - TargetSelector parameters accept only TargetSelector package data. When a procedure has a TargetSelector parameter, it is for the purpose of specifying a general type of object. For instance, an **Eat** procedure accepts a TargetSelector for specifying what type of food to eat.

## Flag Overrides

You can also override any package flags on a per procedure basis (click a procedure in the tree, and look to the right for the override flags). Click the button to the left to unlock the override, then set the value.

If using overrides in this way, consider creating a bool data field, and using the "GetNumericPackageData" condition function to control different versions of the procedure, one with the override, and one without, so that users of the package template can explicitly decide whether to override the package level flag.

## Common Setups

There are some common ways that certain procedures and branches are combined. Feel free to fill this area with useful combinations of procedures and branches.

### Simultaneous Find and Another Procedure

If you need to find something, you could create a simultaneous branch with a find procedure combined with something else that's natural looking, such as a patrol, sandbox, travel, etc. Find on its own can look bad because they don't do anything except detect nearby things. Combining Find with some sort of active procedure lets them walk around and look busy while trying to do something else. Because they are both in a simultaneous branch, as soon as they find what they're looking for, they'll stop and do something else.

### Simultaneous Wait and Another Procedure
If you have a procedure that doesn't end or takes a long time to do(like eat), you can combine that procedure with a wait. When the wait timer is up, the entire simultaneous branch ends as well, causing the persistent procedure to stop as well.

## Troubleshooting

## Fixing Common Warnings

This section is for warnings that should be fixed by the designer who created the package.

### "Procedure Has Too Few Parameters"

More verbosely: BGSProcedureBase::ParameterArray::Load: procedure has too few parameters.

Sometimes we need to change the code for an existing procedure, so that it accepts an additional parameter. We might need to do this even though some packages have already been built using that procedure. For instance, we added a "start at nearest point" parameter to the Patrol procedure.

To fix a warning like this:

1.  As with all package warnings, look for it in EditorWarnings.txt to figure out which package is causing it.
2.  In the editor, open that package and check its procedures. At least one of them will contain a parameter.
3.  Assign a package-data variable to that parameter. (It will probably be necessary to add new package data for this purpose.)