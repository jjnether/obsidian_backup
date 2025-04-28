The Dialogue Views Tab is the primary way to create and edit dialogue in a [Quest](https://ck.uesp.net/wiki/Category:Quest "Category:Quest"). You can create any number of Dialogue Views in a quest, and use them to visually organize your dialogue. Any dialogue created in this tab can still be accessed through the other list-based tabs (the [Player Dialogue Tab](https://ck.uesp.net/wiki/Player_Dialogue_Tab "Player Dialogue Tab"), [Combat Tab](https://ck.uesp.net/wiki/Combat_Tab "Combat Tab"), [Favors Tab](https://ck.uesp.net/wiki/Favors_Tab "Favors Tab"), [Detection Tab](https://ck.uesp.net/wiki/Detection_Tab "Detection Tab"), and [Misc Tab](https://ck.uesp.net/wiki/Misc_Tab "Misc Tab")).

In addition, an .xml file containing named with the formid of the Dialogue View is saved in \\\\Data\\DialogueViews. If you are collaborating with another modder or wish to make it easier for others to alter your work, you should distribute them with your .esp file as it is necessary to correctly display the chart in the Dialogue Views window. Keep in mind, however, that the name of the .xml file will include the load order for the .esp, so if the .esp is fifth in your load order but will be seventh in your collaborator's, your collaborator will be unable to see your dialogue views unless he or she renames the .xml file (e.g., from **05**00769C.xml to **07**00769C.xml).

Normally, Views are used to organize dialogue within the current quest, but they can display dialogue from multiple quests if desired.

[![QuestDialogueViewsWindow.png](https://ck.uesp.net/w/images/thumb/4/44/QuestDialogueViewsWindow.png/900px-QuestDialogueViewsWindow.png)](https://ck.uesp.net/wiki/File:QuestDialogueViewsWindow.png)

## Dialogue View List
The left column contains a list of the Dialogue Views in this quest. Right-click on the list to add or delete a view.

A Dialogue View is simply a collection of dialogue, an Editor construct designed to make viewing and organizing it easier. Dialogue Views do not have any in-game functional effect.

## Dialogue View Pane

After you have selected a view, the main pane will show you the dialogue that you've assigned to it. (A new view will be blank until you create or insert dialogue into it.)

Right-clicking in an empty part of the view will bring up the following options:

-   **Create branch:** This will create a new Dialogue Branch and insert it into this view.
-   **Insert branch into current view:** This allows you to select one or more existing Dialogue Branches and display them in this view.

In the Dialogue View Pane, the large colored boxes are [Dialogue Branches](https://ck.uesp.net/wiki/Dialogue_Branch "Dialogue Branch"). Each Branch contains one or more [Topics](https://ck.uesp.net/wiki/Topic "Topic"), which in turn contain one or more [Infos](https://ck.uesp.net/wiki/Topic_Info "Topic Info"). This hierarchy is visually displayed in the dialogue view.

### [Branches](https://ck.uesp.net/wiki/Dialogue_Branch "Dialogue Branch")

[Branches](https://ck.uesp.net/wiki/Dialogue_Branch "Dialogue Branch") cannot be moved directly in the Dialogue View Pane. Instead, the branch is automatically drawn to surround all of its topics. In order to move a branch, you move its topics.

The color of the Branch box indicates its [type](https://ck.uesp.net/wiki/Dialogue_Branch "Dialogue Branch"):

-   **Blocking** branches are green.
-   **Top Level** branches are yellow.
-   **Normal** branches are blue.

Right-clicking on a Branch brings up the following options:

-   **Edit Branch**: Opens the [Branch Form](https://ck.uesp.net/wiki/Dialogue_Branch "Dialogue Branch") for editing. Double-clicking on the Branch will also open this form.
-   **Add Topic:** allows you to create a new [Topic](https://ck.uesp.net/wiki/Topic "Topic") in this branch.
-   **Remove branch from current view:** Removes this branch and all connected branches from the Dialogue View. Note that this does not delete the branch - it simply stops displaying it in this view. You can still edit the dialogue by finding it in the appropriate [dialogue tab](https://ck.uesp.net/wiki/Category:Dialogue "Category:Dialogue"), or by inserting it into another view.
-   **Delete branch:** Deletes the branch, and also removes all connected branches from the view. (Note that the connected branches are NOT deleted, just removed from the view.)
-   **Use Info:** Displays the [Use Info](https://ck.uesp.net/wiki/Use_Info "Use Info") for this branch.

### [Topics](https://ck.uesp.net/wiki/Topic "Topic")

All [Topics](https://ck.uesp.net/wiki/Topic "Topic") are contained within a Branch. Topics can be moved around the view by left-clicking and dragging on the colored title bar.

The color of the Topic's title bar indicates its type:

-   If this Topic is the Branch's Starting Topic, it has a yellow title bar.
-   Otherwise, it has a grey title bar.

Right-clicking on a Topic brings up the following options:

-   **Delete Topic:** Deletes the Topic entirely.
-   **Edit Topic:** Opens the [Topic Form](https://ck.uesp.net/wiki/Topic "Topic") for editing. Double-clicking on the Topic will also open this form.
-   **New Info:** Creates a new [Info](https://ck.uesp.net/wiki/Topic_Info "Topic Info") at the end of the current Topic's stack.
-   **Use Info:** Displays the [Use Info](https://ck.uesp.net/wiki/Use_Info "Use Info") for this topic.

### [Infos](https://ck.uesp.net/wiki/Topic_Info "Topic Info")

All [Infos](https://ck.uesp.net/wiki/Topic_Info "Topic Info") are contained within a Topic. Infos can only be moved by using the 'Move to Topic' command.

Right-clicking on an Info brings up the following options:

-   **Edit Info:** Opens the [Info Form](https://ck.uesp.net/wiki/Topic_Info "Topic Info") for editing. Double-clicking on the Info will also open this form.
-   **New Info:** Creates a new [Info](https://ck.uesp.net/wiki/Topic_Info "Topic Info") at the end of the current Topic's stack.
-   **Delete Info:** Deletes the selected Info.
-   **Copy Info:** Copies the selected Info (including any conditions or scripts attached to it), placing it in the current topic.
-   **Move to Topic:** Moves the selected Info to the indicated Topic.
-   **Use Info:** Displays the [Use Info](https://ck.uesp.net/wiki/Use_Info "Use Info") for this topic.

### Choice Arrows

The dialogue's structure is visually represented by arrows that connect [Infos](https://ck.uesp.net/wiki/Topic_Info "Topic Info") to [Topics](https://ck.uesp.net/wiki/Topic "Topic"). These arrows represent the [choices](https://ck.uesp.net/wiki/Choice_List "Choice List") that will be presented to the player when this dialogue is displayed in game.

Choice Arrows are color-coded as follows:

-   **Black:** A normal choice.
-   **Green:** An "Invisible Continue". The player does not see this choice; in the game, the dialogue proceeds automatically from one info to the next if connected by an Invisible Continue.
-   **Red:** A "Walk-Away Topic". This choice will be automatically "selected" if the player exits dialogue without selecting any choice.

Right-clicking on a Choice Arrow brings up the following options:

-   **Break Link:** Deletes the connection.
-   **Mark as Walk-Away:** Tags the current link as a Walk-Away Topic.
-   **Mark as Invisible Continue:** Marks the selected arrow as an Invisible Continue.