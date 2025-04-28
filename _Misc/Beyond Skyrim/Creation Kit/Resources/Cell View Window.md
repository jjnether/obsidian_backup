## The Cell View Window

[![Cell View Window](https://ck.uesp.net/w/images/thumb/a/a3/CellView.jpg/325px-CellView.jpg)](https://ck.uesp.net/wiki/File:CellView.jpg "Cell View Window")

The Cell View Window allows you to view, edit, and move between [Cells](https://ck.uesp.net/wiki/Category:Cells "Category:Cells") in the world, both [interior](https://ck.uesp.net/wiki/Glossary#I "Glossary") and [exterior](https://ck.uesp.net/wiki/Glossary#E "Glossary"). It is the most efficient way to switch the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window") to a new cell, and serves as a quick way of jumping around the world.

The Cell View Window has two panels. The first lists all of the cells, along with their names and coordinates. The second panel lists all of the objects within the selected cell.

## World Space Dropdown
The World Space Dropdown at the top of the Cell View Window allows you to select the collection of Cells to view in the Cell List. All of the [Worldspaces](https://ck.uesp.net/wiki/Worldspaces "Worldspaces") in the game are listed in this dropdown, along with a special entry for Interior cells.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Note that ' Interior' has a space before it, which keeps it sorted at the top of this dropdown. The fastest way to switch to the list of Interior cells is to click on the dropdown, then hit the spacebar.</td></tr></tbody></table>

## Cell List

At the top of the Cell List are two navigation options that are helpful in Exteriors:

-   **X** and **Y** can be used to easily jump to a specific coordinate. Just enter the numbers and click the "Go" button and the cell will immediately load as if selected in the cell view window.
-   **Loaded at Top:** If checked, the Cell List will automatically sort all of the currently loaded cells to the top of the list. This is primarily helpful when you want to have the nearby loaded cells easily accessible.

The Cell List itself is a sortable table of cells. You can resort the table by clicking on any of the column headers. You can also right-click on any cell in the Cell List to edit its [Cell Data](https://ck.uesp.net/wiki/Category:Cells "Category:Cells"), duplicate it, or delete it.

The Cell List has the following columns:

-   **EditorID:** The Editor ID of the cell.
    -   In Interiors, this is typically of the form <Path><Name><Cell#>
        -   Arcadia's Cauldron in Whiterun is 'WhiterunArcadiasCauldron'.
        -   The third level of Tovald's Cave is 'TolvaldsCave03'.
    -   In [Worldspaces](https://ck.uesp.net/wiki/Worldspaces "Worldspaces"), significant cells are usually named, while other cells retain the default name ('Wilderness').
-   **FormID:** The Form ID of the cell. This column is usually collapsed unless you choose to expand it.
-   **Name:** The name of the cell.
-   **Loaded:** Whether the cell is currently loaded in the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window").
-   **Coords:** For Exteriors, the \[X, Y\] coordinates of the cell.
-   **Location:** The [Location](https://ck.uesp.net/wiki/Location "Location") of the cell.
-   **Owner:** The [Actor](https://ck.uesp.net/wiki/Actor "Actor") or [Faction](https://ck.uesp.net/wiki/Faction "Faction") that owns the cell.

## Object List

Like the Cell List, the Object List is a sortable table of objects. You can resort the table by clicking on any of the column headers, or type text into the filter box above the Object List to filter for specific objects.

The Object List has the following columns:

-   **EditorID:** The Editor ID of the object.
-   **FormID:** The Form ID of the object.
-   **Type:** The object's [type](https://ck.uesp.net/wiki/Category:Object_Classes "Category:Object Classes").
-   **Owner:** The [Actor](https://ck.uesp.net/wiki/Actor "Actor") or [Faction](https://ck.uesp.net/wiki/Faction "Faction") that owns the object.
-   **Lock Level:** For [Doors](https://ck.uesp.net/wiki/Door "Door") and [Containers](https://ck.uesp.net/wiki/Container "Container"), the lock level of the object.
-   **Loc Ref Type:** The object's [Location Ref Type](https://ck.uesp.net/wiki/Location_Ref_Type "Location Ref Type"), if any.
-   **Persist Location:** Where the object will be persistent.
-   **Initially Disabled:** Whether this object is initially disabled.
-   **Leveled Item:** The leveled list, if any, that will substitute for this object in the game.

## Common Tasks

## Loading/Moving to a Cell

Double-click on a cell in the Cell List, and the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window") will switch to an overhead view of that cell. This may take several seconds if the cell is not currently loaded in memory.

## Switch View to an Object

Double-click on an object in the Object List, and the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window") will switch to this object, placing it in the center of the screen (like pressing C from the Render Window). The object will also be selected. This is one of the fastest ways of finding and editing objects.

## Renaming a Cell

To rename a cell, select it, and then click its name (or hit \[F2\]). Remember that all [interior cells](https://ck.uesp.net/wiki/Glossary#Interior_Cells "Glossary") must have unique names.

## Quickly Hide all Effects

To quickly hide all visual effects in a cell, type "FX" in the filter box above the Object Window, left-click on the first object in the Object List, and Shift-Click on the last object in the list. Then select the [Render Window](https://ck.uesp.net/wiki/Render_Window "Render Window") and press \[1\] twice to hide all effects in the cell. This is useful if you often find yourself accidentally selecting effects while working in the Render Window. To see the effects again, reload the view by pressing \[F5\].