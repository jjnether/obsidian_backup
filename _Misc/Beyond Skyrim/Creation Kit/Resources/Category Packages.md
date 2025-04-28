_For the Editor form, see [Package (Form)](https://ck.uesp.net/wiki/Package_(Form) "Package (Form)")._

## Overview\[[edit](https://ck.uesp.net/w/index.php?title=Category:Packages&veaction=edit&section=1 "Edit section: Overview") | [edit source](https://ck.uesp.net/w/index.php?title=Category:Packages&action=edit&section=1 "Edit section: Overview")\]

Packages are the main way in which you can control an [Actor's](https://ck.uesp.net/wiki/Category:Actor "Category:Actor") behavior. Each Package represents a behavior that the Actor will perform under certain conditions.

The Package system consists of a number of components:

-   All **[Actors](https://ck.uesp.net/wiki/Category:Actor "Category:Actor")** have a **[Package Stack](https://ck.uesp.net/wiki/Package_Stack "Package Stack")**, an ordered list of potential behaviors.
-   These stacks are composed of [**Packages**](https://ck.uesp.net/wiki/Package_(Form) "Package (Form)"), individual behaviors that the Actor can perform.
    -   Most Packages are instances of a **[Package Template](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates")**, which provides standardized, reusable functionality for common behaviors.
    -   Packages can modify the behavior inherited from their [Templates](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates") in predefined ways, such as specifying data values.
-   [Package Templates](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates"), in turn, are composed of a structured **[Tree](https://ck.uesp.net/wiki/Category:Package_Templates#Procedure_Trees "Category:Package Templates")** of **[Procedures](https://ck.uesp.net/wiki/Category:Procedures "Category:Procedures")**, the atomic actions that make up the behavior.
-   Periodically, the game will reevaluate each [Actor's](https://ck.uesp.net/wiki/Category:Actor "Category:Actor") [Package Stack](https://ck.uesp.net/wiki/Package_Stack "Package Stack"). The topmost package in the stack whose conditions are satisfied will be run.

  
For example, say the game updates the AI for Faendal, an [Actor](https://ck.uesp.net/wiki/Category:Actor "Category:Actor") in Riverwood, at midnight. It evaluates his [Package Stack](https://ck.uesp.net/wiki/Package_Stack "Package Stack"), checking the conditions on each Package from the top of the stack down. The first one whose conditions are satisfied happens to be \[FaendalSleepHome23x5\]. This Package is an instance of the \[Sleep\] [Package Template](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates"), and specifies a piece of data used by that template (where Faendal should sleep: in his house). The \[Sleep\] [Template](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates"), in turn, specifies the atomic actions needed to carry out the behavior, telling the AI that Faendal needs to walk home, lock his door, find a bed, and sleep in it.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td>The basic concepts of Package System and <a href="https://ck.uesp.net/wiki/Package_Stack" title="Package Stack">Package Stack</a> are unchanged from Fallout 3. However, the system has a number of new features, as described below.</td></tr></tbody></table>

## Additional Information\[[edit](https://ck.uesp.net/w/index.php?title=Category:Packages&veaction=edit&section=2 "Edit section: Additional Information") | [edit source](https://ck.uesp.net/w/index.php?title=Category:Packages&action=edit&section=2 "Edit section: Additional Information")\]

### Radiant Story Alias Packages\[[edit](https://ck.uesp.net/w/index.php?title=Category:Packages&veaction=edit&section=3 "Edit section: Radiant Story Alias Packages") | [edit source](https://ck.uesp.net/w/index.php?title=Category:Packages&action=edit&section=3 "Edit section: Radiant Story Alias Packages")\]

The Radiant Story system makes it possible to add Packages to a [Quest Alias](https://ck.uesp.net/wiki/Quest_Alias_Tab "Quest Alias Tab"), and then apply that Alias (along with those packages) to an Actor (in some cases, potentially to ANY Actor) at runtime. This means that, depending on what Alias an Actor might have attached to him, he may have more packages on his stack than you can see by looking at the Actor's form directly. For more, see [Category:Radiant Story](https://ck.uesp.net/wiki/Category:Radiant_Story "Category:Radiant Story").

### Default Packages\[[edit](https://ck.uesp.net/w/index.php?title=Category:Packages&veaction=edit&section=4 "Edit section: Default Packages") | [edit source](https://ck.uesp.net/w/index.php?title=Category:Packages&action=edit&section=4 "Edit section: Default Packages")\]

All Actors can have a Default Package List, a list of Packages that are added to the bottom of the Actor's [Package Stack](https://ck.uesp.net/wiki/Package_Stack "Package Stack") and typically function as 'fallbacks' when none of the Actor's specific packages apply. For more details, see the [Package Stack](https://ck.uesp.net/wiki/Package_Stack "Package Stack") and [AI Packages Tab](https://ck.uesp.net/wiki/AI_Packages_Tab "AI Packages Tab") articles.

### Interrupt Behavior Override Packages

Some systems, such as [Combat](https://ck.uesp.net/wiki/Combat "Combat"), will preempt an Actor's package-driven AI behavior. You can interrupt and override those systems by explicitly specifying a package or list of packages to run instead. For example, you can specify that when a particular NPC enters combat, they will perform some specific behavior (like running over to a lever and pulling it). For more details, see the [Interrupt Override Packages](https://ck.uesp.net/wiki/Interrupt_Override_Packages "Interrupt Override Packages") and [AI Packages Tab](https://ck.uesp.net/wiki/AI_Packages_Tab "AI Packages Tab") articles.

### Procedures
Procedures, the building blocks of Packages, are now exposed in the Editor. Procedures are atomic actions that take _inputs_ or _parameters_ that further define behavior. For example, a _Travel_ procedure takes a piece of data that defines the location to travel to. See [Procedures](https://ck.uesp.net/wiki/Category:Procedures "Category:Procedures") for details.

### Procedure Tree

Procedures in a package are connected together by a procedure tree.

A Procedure Tree is a stack of Branches (or "Nodes") that contain procedures. Because Branches and Procedures can all have Conditions, you can create very complex switches to route AI behavior through. So by looking at a package's procedure tree structure, you can intuit the "thought process" of the actor as he goes about doing what the package asks him.

For example, you could build a package that first tries to "FIND" a chair, and if it finds one, causes the NPC to "SIT" in the chair. If it doesn't find a chair, it can cause the NPC to "WANDER" around instead. This is what the "Sit" package template does.

Because you usually manipulate Procedure Trees while designing new Templates, see [Package Templates](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates") for more details.

### Package Templates

Package Templates are prebuilt Procedure Trees and data inputs, whose data can be changed, but whose structure and logic cannot. The vast majority of the packages in the game are derived from a small handful of Templates.

For more details on building your own Package Template, see [Package Templates](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates"), or the example in [Creating a new Package Template](https://ck.uesp.net/wiki/Creating_a_new_Package_Template "Creating a new Package Template").

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:NewFeature.jpg"><img alt="NewFeature.jpg" src="https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/d/dc/NewFeature.jpg 1.5x"></a></td><td>You can think of packages from Fallout 3 as Templates in Skyrim. Most of the old packages have been rebuilt and exist for easy use as Package Templates.</td></tr></tbody></table>

### One-Off Packages

If desired, you can build a custom package with its own procedure tree and not make that package a Template for reuse. But this is rarely necessary or desirable- if you are going through the trouble of creating new behavior, you might as well make it a Template so you can reuse it later. Since creating a stand-alone package is identical to creating a template, except you don't mark it as a Template, See [Package Templates](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates") for more info.