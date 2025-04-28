## World Spaces Dialog

A world space is simply an entire world, with its own landscape, sky and weather. All [exterior cells](https://ck.uesp.net/wiki/Exterior_cells "Exterior cells") belong to a worldspace -- in Skyrim, most of the exterior is in the Tamriel worldspace, but there are many more worldspaces used in the game, and adding a new worldspace is relatively simple.

Worldspaces can share landscape with a Parent worldspace (for example, all the city worldspaces in Skyrim have Tamriel as a parent), or they can use an entirely different landscape (for example, the Sovngarde worldspace).

-   **Name:** Editor ID of the worldspace
-   **Parent Worldspace:** If you select NONE, the worldspace will have its own, editable landscape. Otherwise, this worldspace will use the landscape of its parent.
-   **Use Sky Cell**: Uses the sky cell of the parent worldspace. This will allow flying creatures to enter the worldspace from the parent space.

**Sharable Data:** The following fields are only available if this worldspace has a Parent.

-   **Use LOD Data:** If checked, LOD Data is enabled for World Space
    -   **LOD Water Height:** Elevation that LOD water appears
    -   **LOD Water Type:** Editor ID of water type
-   **Use Water Data:** If checked, specified IS data will be enabled for World Space
    -   **Water:** Select the [WaterType](https://ck.uesp.net/wiki/WaterType "WaterType") used in this worldspace.
-   **Use Climate Data:** If checked, specified climate data will be enabled for World Space
    -   **Climate:** Select the Climate for this worldspace.
-   **Use Land Data:** If checked, land data will be enabled for World Space
    -   **Default Land Height:** Specifies land elevation value
    -   **Default Water Height:** Specifies default water elevation value

**Use Map Data:** If you want a custom world map, select the DDS file here.

-   **Map Image:**
-   **Usable Dimensions:** Set the limits of the playable area of the worldspace (NW corner to SE corner).
-   **Cell Coordinates:**

**World Map Offset Data:** The offset of the location for the Parent's world map. These are used to line up the map marker with where the worldspace would be on the world map

-   **Cell X Offset:**
-   **Cell Y Offset:**
-   **World Map Scale:**

-   **Canopy Shadow:** Not used
-   **Water Environment Map:** Not used

-   **No LOD Water:** Disable LOD water (for worldspaces where there is no water or where the view is restricted)
-   **No Landscape:** Disables landscape in the worldspace
-   **No Sky:** Disables sky in the worldspace (for worldspaces that are interiors)
-   **No Grass:** Disables grass in the worldspace
-   **Can't Fast Travel From Here:** No Fast Travel from this worldspace
-   **Can't Wait:** No waiting in this worldspace

-   **Music:** Default music type used in this worldspace
-   **Encounter Zone:** Specify an [Encounter Zone](https://ck.uesp.net/wiki/Encounter_Zone "Encounter Zone") for the entire worldspace
-   **Location:** Specify a [Location](https://ck.uesp.net/wiki/Location "Location") for the entire worldspace
-   **Interior Lighting:** The lighting template to apply to the space

-   **HD LOD Diffuse:** Diffuse map for the LOD
-   **HD LOD Normal:** Normal map for the LOD

-   **Small World:** Mark this as a small worldspace (speeds up certain processing for small worldspaces)
-   **Fixed Dimensions**: Limits the size of the worldspace

-   **Output Cell Ref Counts:**