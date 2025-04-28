[![The Object Window w/collapsed list.](https://ck.uesp.net/w/images/4/43/Learn_Filter.jpg)](https://ck.uesp.net/wiki/File:Learn_Filter.jpg "The Object Window w/collapsed list.")

## Overview

The Object Window is the window from which the [objects](https://ck.uesp.net/wiki/Object "Object") in the currently loaded [Masterfiles](https://ck.uesp.net/wiki/Masterfile "Masterfile") and [Plug-ins](https://ck.uesp.net/wiki/Plug-in "Plug-in") can be viewed and edited. It is also the window from which objects are dropped into the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window") (such as adding a hut to a village).

### Opening the Object Window

The object window is opened by selecting View \\ Object Window. It remains on screen until it is closed. It is a nested node structure that allows you to view all object types, Characters, and creatures. Object types are the nodes at the highest level. Clicking one opens the list of those objects in the hierarchy.

Right clicking on an object in the list will bring up a context menu where you can Create a new object, edit the existing object, duplicate the existing object, or delete the existing object. You can also "Create New Object Window" if you want multiple object windows open at once (a handy feature), or "Use Info" to find all the places that use the object.

### Placing an Item in the World

To place an object in the world, select it, and then drag and drop it into an open [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window"). You must drag from actual text, as trying to grab empty space will result in the object not being grabbed. The object will appear in the world at the point you let it go, and the Render Window will now be selected so you can place the object correctly. Note that only certain types of objects can be dragged into the world.

### The Object Count

Every object has a Count field. This is the number of [references](https://ck.uesp.net/wiki/References "References") in the world that derive from this object. Loading extra [Masterfiles](https://ck.uesp.net/wiki/Masterfile "Masterfile") or [plug-ins](https://ck.uesp.net/wiki/Plug-in "Plug-in") will change this number if the object is also used in them. Keep in mind that including an object in a Leveled/Random list will only count once per list, not each time that list is referenced.

If you Right Click and choose "Use Info" it will list all the Users and all the References (if any) of the object.

### Users

This is the number of other forms that in some way point to the form. For example, if an object is in a leveled list, that leveled list object will be included in the count of users.

If you Right Click and choose "Use Info" it will list all the Users and all the References (if any) of the object.

### Object Use Information

To get information about how and where an object is used in the world, select it and press F1 to bring up the Use Report dialog. The bottom pane displays a list of the references to this object in the world. Double-click on an item in the list to go to that reference in the Render Window. The top pane displays a list of other objects that use this object in some way. This includes leveled lists which contain the item, Containers and actors who have the item in their inventory or spellbook, and even actors who have an AI Package related to this item. The Use Report dialog can also be opened by right-clicking on an item and selecting Info from the popup menu.

### Editing Object Data

The object ID can be edited directly in here by clicking on the selected item (like renaming a Windows file). You can double-click the object to open a window showing all of its data. This is the most useful way of editing items such as scripts, art, etc. This window can also be opened by right-clicking on an item and selecting Edit from the popup menu.

### Sorting Object Data

Each object type has certain data such as ID, type, name, health, etc. Clicking any of these field names will sort the list by that field. Clicking the field name again will sort by that field in the opposite direction (ascending or descending).

### Adding an Object

To add an item to the database, simply select the category you want with the tabs, and press the INSERT key. This will open a window containing the object data. This window can also be opened by right-clicking in the Object Window and selecting New from the popup menu.

### Deleting Objects from the Database

Pressing delete will remove the selected item. If this object has been used in the world the deletion is confirmed. This can also be accomplished by right-clicking and selecting Delete from the popup menu.

#### Help! I accidently deleted an object from my database!

Accidently deleting an object from the database and then saving your .esp file before you realize what happened can be a tricky problem to fix. One solution is to load your .esp file but do not set it as active. Then duplicate all your cells and objects. Finally, save your work and you will be prompted to create a new .esp file. You should end up with a .esp file that has all the work you duplicated but does not contain any deletions.

Another technique, which in most cases is more efficient then duplicating everything, relies upon the fact that « _if you know what you have modified, then you know what should not be modified_ » (do the following in sequence):

-   On the Data window that appears when clicking the open button, select the ESM files dependencies (usually Skyrim.esm and Update.esm), and then your mod set as "Active", but do not click on the "Ok" button yet.

-   With your mod still selected, click on the "Details..." button. A "File Details" window will pop-up : this lists all the modifications of your mod.

-   Expand the window to the right so that you see more columns. On the left of the "Offset" column, a hidden column can be noticed because of 2 vertical little bars : expand the rightmost of these 2 vertical bars so as to expose the "Form ID" column. Click on the column label ("Form ID") so as to sort them out.

-   Look for any object that should NOT be listed and that you know you didn't want to modify : for each one of them, select then press the "Delete" keyboard key so that the specific modification is marked to not get loaded. A "I" will then appear in the "Ignore" column for all of these objects you've "deleted" in that window. **Be very careful here**, since a modification you do on an object can cascade to some other database reference. e.g. if you modify objects in a cell, that cell will also be marked as "modded" (appearing in the Data list), thus you wouldn't want to delete (mark for not loading) that cell reference...

-   When you have finished selecting/deleting those objects that shouldn't get "modded", click "Close", then on the Data window click "Ok"

-   After the mod has been loaded, click the save button and exit : mod cleaning completed.

Even more efficiently in regards to deleted "vanilla" objects (or deleted objects from an ESM dependency):

-   After clicking the "Details..." button on the Data window, click on the column label "Deleted" (second column from left) : this will show all the deleted objects from the original game or specific ESM dependency (with a "D" symbol).

-   Since there shouldn't be any vanilla object deleted, simply select each one of them and press your keyboard's "Delete" key (which will tag the corresponding modification to be ignored, putting a "I" flag symbol in the "Ignored" column).

-   Then Click "Close", then "Ok" on the Data Window, then save the mod after it's been loaded and close the CK : cleanup completed.