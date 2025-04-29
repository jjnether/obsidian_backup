## The Arcane University's guide to xEdit

### What is xEdit exactly?

xEdit, also known as SSEEdit or TES5Edit, is a handy little program that’ll let you open any .esp / .esm / .esl file and see exactly which information it contains. In this guide we’ll only cover how to understand what you’re looking at and how to clean a plugin for any unwanted edits. To learn how to use it for checking for, and resolving conflicts in your LO I suggest you take your time and read _the Tome of xEdit_ found [here](https://tes5edit.github.io/docs/). You can grab xEdit [here](https://www.nexusmods.com/skyrimspecialedition/mods/164)

### Why do we need to clean our plugins?

When we’re working in the Creation kit we mess around with a bunch of stuff, we might go looking in Vanilla locations, quests etc. to see how they’ve done certain things and to get inspiration. We might move an object in a Vanilla location without even noticing it and BAM, we’ve made an edit to a Vanilla location that is now stored in our plugin. We might move an object in a Vanilla location but we press CTRL+Z (undo) and move the asset back into the original place, BUT the Creation kit still stores the information about that asset being messed with. This is what we call Dirty edits. These dirty edits can cause issues for people using our mods because of conflicts with other mods. So to limit possible unwanted conflicts, we need to clean our plugins, every single time.

### How to understand what you’re looking at.

Everything you see under your plugin in xEdit is an edit. Your plugin may add cells, worldspaces, references, forms, and so on. It can also modify any of these things. Good practice generally for creating a plugin is to avoid editing anything from vanilla Skyrim. If you need a container to contain a certain item and no vanilla chest has it, make a new container record. (This can be done quite easily by duplicating an existing chest and modifying the contents.) This is not always the case of course, if you're making a house, that house needs to go somewhere, so you'll need to edit Tamriel (the Skyrim worldspace) to place it. You could make a new worldspace, but the player will need a way to get there too, so you'll need to add a boat or portal of some kind to Tamriel or another cell. Any edits that are unintentional or unnecessary should be cleaned from your plugin.

[![Conflicts.png](https://wiki.beyondskyrim.org/w/images/3/39/Conflicts.png)](https://wiki.beyondskyrim.org/wiki/File:Conflicts.png)

[![XEditExamplePlugin.PNG](https://wiki.beyondskyrim.org/w/images/1/13/XEditExamplePlugin.PNG)](https://wiki.beyondskyrim.org/wiki/File:XEditExamplePlugin.PNG)

Here is a dummy plugin made for the purposes of this tutorial. As you can see, there are many edits. Some of these edits are intentional, but some of them are not. How can you tell the difference? Ultimately, only you know what you intended to change, but xEdit has features to help. My plugin creates a small farmhouse, which has an interior cell (aaaBSTestCell) and an exterior that it's linked to. I also created a custom knapsack with specific items to go in my house.

[![XEditExampleProblemEdits.png](https://wiki.beyondskyrim.org/w/images/0/01/XEditExampleProblemEdits.png)](https://wiki.beyondskyrim.org/wiki/File:XEditExampleProblemEdits.png)

What you'll notice is that various entries are marked with colors. Dark green, seen on the WarehouseAmbushes cell means that the record was declared in a different file and is marked as edited by another, but that record does not have any changed data. In this instance, this is because an object in the cell was moved, but the cell data itself is unchanged. Regardless, this is a dirty edit, and needs to be cleaned. The yellow color seen on PersonalChestSmall means something about the record, which was created in Skyrim.esm, was changed by your file. This could be the name, the contents of the chest, or just about anything. Regardless, it is a dirty edit. Lastly you'll see the red color on Tamriel. This is the Skyrim worldspace, and it will always show up as red. All this means is there were edits made in one file, which were reverted in another. For Tamriel specifically, blame Bethesda, but in other cases, you should investigate why it shows as red. Any record that shows the plain background color is a record that was created/placed by your plugin, and in most cases these will be intentional, but there can be exceptions. Only you will know these exceptions, as only you will know if something created in your plugin was intended.

[![XEditExampleRemove.png](https://wiki.beyondskyrim.org/w/images/5/51/XEditExampleRemove.png)](https://wiki.beyondskyrim.org/wiki/File:XEditExampleRemove.png)

To remove a dirty edit, simply right click and Remove.

[![XEditExampleWarning.png](https://wiki.beyondskyrim.org/w/images/9/97/XEditExampleWarning.png)](https://wiki.beyondskyrim.org/wiki/File:XEditExampleWarning.png)

xEdit will give a warning after the first time you click remove, this is just informing you that it's dangerous to edit files like this. Click yes. This will happen every time you reopen xEdit and try to make an edit. Cleaning plugins as outlined in this document shouldn't result in dangerous changes, but it's always good practice to backup your plugins before cleaning them. xEdit creates backups by default as well. If you are ever unsure if an edit is safe, you can always ask in the AU or ask someone more experienced with xEdit and the Skyrim engine.

[![XEditExamplePluginCleaned.PNG](https://wiki.beyondskyrim.org/w/images/c/c8/XEditExamplePluginCleaned.PNG)](https://wiki.beyondskyrim.org/wiki/File:XEditExamplePluginCleaned.PNG)

This is the same plugin after being cleaned. As you can see, the cell I created remained, the container I made also remained, and the door and farmhouse I placed in Skyrim remained while all other changes were removed. One last note is the Navigation Mesh Info Map. This is navmesh data. This will never be highlighted with a color, and is slightly harder to determine whether it's a dirty edit. In this case, it was not, this is simply the navmesh in my cell. However, Sometimes the Creation Kit will erroneously edit this record. If this record is present in your plugin but you didn't edit any navmeshes, you are safe to remove it.

### Can't I just use QuickAutoClean on my plugin?\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:XEdit_Tutorial&action=edit&section=5 "Edit section: Can't I just use QuickAutoClean on my plugin?")\]

If you are creating a standalone mod to release to the public, or you are cleaning a mod for your own load order, QuickAutoClean is safe and encouraged, but do mind that QuickAutoClean only removes ITM (Identical To Master) + ITPO (Identical To Previous Overwrite) (the dark green) records. **You should always do the manual cleaning first**. However, if you are a developer on a project such as Beyond Skyrim which uses the merge to master workflow, do not use QuickAutoClean. The reason for this is QuickAutoClean is designed to be used on plugins that will be enabled as the game is played, not for plugins that will be merged to a master file. Using QuickAutoClean on a file meant for merge will ultimately create problems that will need to be fixed down the line.

### I accidentally added a master file I didn't want. How do I remove it?\[[edit](https://wiki.beyondskyrim.org/w/index.php?title=Arcane_University:XEdit_Tutorial&action=edit&section=6 "Edit section: I accidentally added a master file I didn't want. How do I remove it?")\]

xEdit allows you to remove unneeded master files from your plugin, but it's not quite as simple as removing an edit. Firstly, you need to ensure your file does not use anything from the unneeded master file. This means any asset, cell, worldspace, quest, or anything else declared in that master file, must not be placed or edited by your plugin. Once you have ensured this, right click your plugin and click Clean Masters.

[![XEditExampleMasters.png](https://wiki.beyondskyrim.org/w/images/7/72/XEditExampleMasters.png)](https://wiki.beyondskyrim.org/wiki/File:XEditExampleMasters.png)

[![XEditExampleCleanedMasters.png](https://wiki.beyondskyrim.org/w/images/f/f3/XEditExampleCleanedMasters.png)](https://wiki.beyondskyrim.org/wiki/File:XEditExampleCleanedMasters.png)

As you can see, doing this removed Update.esm, Dawnguard.esm, HearthFires.esm, and Dragonborn.esm from my plugin's master list, as I did not use any references from any of these masters. For the purposes of Beyond Skyrim, all of these masters are okay to have on your plugin, as well as BSAssets.esm and whatever project you're editing. Your plugin cannot have multiple Beyond Skyrim projects as a master, and if your plugin aims to add or edit something in BSAssets, it is best practice to not have any Beyond Skyrim project as a master, only BSAssets.esm. Additionally, it is not acceptable to have another plugin as a master for your plugin unless the person doing merges for your project explicitly gave you permission to do so. This is because merging a plugin that uses another plugin as master makes the merge process significantly more complicated.

### Cleaning masters doesn’t remove all plugins that I want it to Remove, what do I do ?

It’s because your plugin is using something from that master file. Depending on what your mod does, this can be anything. But it’s relatively easy to find by using a simple script on your plugin. In this example I’ve loaded two of my own dungeons, Kagzulift and Ljungvunde. Ljungvunde was set as the active file. I then made a few edits to Kagzulift.

Right click your plugin and press on **Apply Script**

[![Apply Script.jpg](https://wiki.beyondskyrim.org/w/images/2/27/Apply_Script.jpg)](https://wiki.beyondskyrim.org/wiki/File:Apply_Script.jpg)

You’ll then get this window. In the dropdown menu, find **Report masters** and press **OK**

[![Report Masters.jpg](https://wiki.beyondskyrim.org/w/images/e/e1/Report_Masters.jpg)](https://wiki.beyondskyrim.org/wiki/File:Report_Masters.jpg)

Select the master you want to remove

[![Select Plugin.jpg](https://wiki.beyondskyrim.org/w/images/5/5a/Select_Plugin.jpg)](https://wiki.beyondskyrim.org/wiki/File:Select_Plugin.jpg)

Once the script has finished, you can see the formID(s) \[REFR:xxxxxxxx\] that’s causing you to not be able to remove the master. Now search for that FormID.

[![Reference ID.jpg](https://wiki.beyondskyrim.org/w/images/4/4b/Reference_ID.jpg)](https://wiki.beyondskyrim.org/wiki/File:Reference_ID.jpg)

Now you can see the exact changes, and remove them if you need to. Now run the Clean Masters again.

[![Dirty Edits.jpg](https://wiki.beyondskyrim.org/w/images/4/4d/Dirty_Edits.jpg)](https://wiki.beyondskyrim.org/wiki/File:Dirty_Edits.jpg)

### I’ve edited the Vanilla navmesh and now I have deleted vanilla navmesh records shown in xEdit, what do I do?

Check Kasala’s lecture found [here](https://www.youtube.com/watch?v=xtKh6UhK5RQ) at timestamp 2:21:08