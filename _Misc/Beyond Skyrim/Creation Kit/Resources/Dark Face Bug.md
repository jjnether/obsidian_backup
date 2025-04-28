The **dark face bug**, **gray face bug** or **black face bug** is a bug that happens to actors when their appearance is edited by the Creation Kit. If a new NPC is created or the face of an existing one is edited, then the characters tint masks need to be regenerated. The actor with the new face will have a darker or grayer skin color on the face and head than on the rest of the body. There will be a sharp neck seam line between the two colors of skin.

## Fix
This procedure can be used to solve the problem (**tested on Creation Kit 1.9.32.0**):

-   Select all the actors added by the mod or that have faces edited by the mod, in the Object Window under _Actors_ -> _Actor_ (see note below).

-   Press CTRL + F4; you will be prompted to export the face gen data. This process may take some time depending on the number of actors you have selected. When it is finished, it will display a dialog window stating "Done."

Creation Kit will generate the appropriate files: meshes (.nif files) and textures (.dds files), associated with the mod, that will need to be packaged and uploaded along with the .esp file. Failure to do so will mean that all players who download the mod will have the dark face bug when they use it, even though the problem no longer occurs on the computer the mod was built on.

The mesh and texture files will be in your Data folder:

-   **Example 1: new NPC, ID 000012c4, added by a mod (ExampleMod.esp):**
    -   ...\\Skyrim\\Data\\textures\\actors\\Character\\FaceGenData\\FaceTint\\ExampleMod.esp\\000012C4.dds
    -   ...\\Skyrim\\Data\\meshes\\actors\\Character\\FaceGenData\\FaceGeom\\ExampleMod.esp\\000012C4.nif

-   **Example 2: Vanilla NPC, ID 000918e2 (Uthgerd the Unbroken), edited by a mod:**
    -   ...\\Skyrim\\Data\\textures\\actors\\Character\\FaceGenData\\FaceTint\\Skyrim.esm\\000918e2.dds
    -   ...\\Skyrim\\Data\\meshes\\actors\\Character\\FaceGenData\\FaceGeom\\Skyrim.esm\\000918e2.nif

## Notes

Some .tga texture files are also generated. Apparently, these aren't needed by the game and don't need to be uploaded with the .dds files.

When selecting actors in the Object Window, the CTRL+F4 key binding will not work if the actors are searched through the \*All category. you must navigate and highlight them directly via Actors -> Actor sub tree, although you can use the search there.