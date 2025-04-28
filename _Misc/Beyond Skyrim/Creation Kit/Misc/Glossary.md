#### Activation
Activation is the interaction between two objects in the Creation Engine. For example, when the player opens a door, this is an _activation_ event between the player object and the door object in question. Many object types react to an activation with some default behavior. Doors will open/shut, containers display their contents, and NPCs will converse. [Activation Events](https://ck.uesp.net/wiki/OnActivate_-_ObjectReference "OnActivate - ObjectReference") are script-accessible as well, allowing content creators to implement advanced interactions.

#### Archive
Archives are compressed .bsa files used by Creation Engine to store certain types of data, such as 3D models, sound, meshes, and textures, efficiently. The Creation Kit allows users to create these archives by hand or automatically when uploading mods to the Steam Workshop. See also: [File Menu > Create Archive](https://ck.uesp.net/wiki/File_Menu#Create_Archive "File Menu")

#### Artifact
In computer graphics, an artifact is a visual glitch introduced by some technical process. [Non-game specific examples on wikipedia](http://en.wikipedia.org/wiki/Compression_artifact)


#### Base Object
The term for any [Object](https://ck.uesp.net/wiki/Glossary#Object) listed in the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window"). Objects can have any number of [References](https://ck.uesp.net/wiki/Glossary#Object_Reference) placed into the game world.

_For example, the **Base Object** Actor "Alvor" has a single Reference with the EditorID of "AlvorRef" that is in the RiverwoodAlvorsHouse cell._

_The **Base Object** Kit Piece "NorRmSmMid01" has many References, found throughout most Nordic ruins._


#### Cleared Location
A [Location](https://ck.uesp.net/wiki/Location "Location") can be cleared. By default, a location is cleared when any/all reference(s) with the "Boss" [Location Reference Type](https://ck.uesp.net/wiki/Glossary#LocRefType "Glossary") is killed. A location can also be cleared [via script](https://ck.uesp.net/wiki/SetCleared_-_Location "SetCleared - Location").

Locations that are cleared are indicated as such on the world map. If the player re-visits the Location after the area has had time to reset, it may re-populated.

#### Culling
To cull, to pick out : in computer science, culling is a term used for objects which are prevented from rendering.

#### Default Master Package

The [Default Master Package](https://ck.uesp.net/wiki/Default_Master_Package "Default Master Package") is a special package which gives content creators quick access to commonly used AI behaviors without needing to create custom packages each time.

#### Default Objects
Default objects are permanent objects that the programs needs to access reliably. Assign the appropriate game object to the default Use.

#### Depth Bias

Depth bias enables coplanar geometry to not z-fight, offsetting decal geometry when depth-bias is on so that it appears in front of the geometry it is on top of.

Depth bias (on shadow lights) is a method to account for insufficient depth precision in shadowmaps. Small depth bias can result in striping artifacts on the surface of objects, large depth bias can result in a lack of contact shadows.

#### DMP
Acronym shorthand for [Default Master Package](https://ck.uesp.net/wiki/Default_Master_Package "Default Master Package")


#### Edge
Term used to describe the edge of a polygon. Usually used in reference to [navmesh](https://ck.uesp.net/wiki/Category:Navmesh "Category:Navmesh")

#### EOF
When seen in the context of [Papyrus Compiler Errors](https://ck.uesp.net/wiki/Papyrus_Compiler_Errors "Papyrus Compiler Errors") this means **E**vent **O**r **F**unction.

(Generally in computing this would mean End Of File)

#### Exterior Cells

Exterior cells belong to a [Worldspaces](https://ck.uesp.net/wiki/World_Spaces "World Spaces"), and are part of the worldspace's landscape, which is basically a grid that extends infinitely in all directions. Each exterior cell is 4096 units by 4096 [units](https://ck.uesp.net/wiki/Unit "Unit") (or approximately 192x192ft or 58.5x58.5m). Each vertex in an exterior cell is 128 units (6ft) apart.

All exterior cells are automatically given a grid number that represents their \[X,Y\] position from the center of the world. You will see this in the Render Window title as you select objects.

#### External Emittance
External emmitance is when an object gets its emmitance color from an external source. External Emittance can be set to a specific light color, but can also inherit the sky color from a specific region of the world, allowing the emittance color to change to reflect time-of-day.


#### Form
Each of the objects in the currently loaded [masterfiles](https://ck.uesp.net/wiki/Masterfile "Masterfile") and[plug-ins](https://ck.uesp.net/wiki/Plug-in "Plug-in"), including those found in the Object Window as well as not found there. (Actors, factions, packages, cells, references, etc. are all forms)

#### Frustum
In games, a [Frustum](http://en.wikipedia.org/wiki/Frustum) generally refers to the "view frustum" of the game camera. Imagine the 3D space of the game-world, and a camera floating in that space. The frustrum of that camera, a cone-shaped field, would include all visible objects within that 3D space. Frustums can also be used to describe the area which an NPC can see.

#### FX
Shorthand for "Effects", usually "Special Effects". In the Creation Kit, FX objects usually are particle systems such as fire, smoke or fog.


#### Glow Fill
Glow Fills are a kind of Special Effects object. These are designed to simulate the glowing haze surrounding a source of light. They are typically used to create ambiance in interiors as well as obscure visual tricks such as Sun Holes.The object **FXAmbBeamDust03** is one example of a glow fill.


#### Imagespace
An imagespace applies post-processing effects to the image. Images space can control elements such as contrast, tinting, how bright objects must be for bloom lighting, the intensity of the sky/sun, depth of field and more. More information is available in this wiki: [Imagespace reference article](https://ck.uesp.net/wiki/ImageSpace "ImageSpace").

#### Interior Cells

Interior Cells are entered through a load door linked to another cell (interior or exterior). When in an interior, the exterior world is no longer visible. Each interior cell is essentially its own universe.


#### Leaky Faucet Pacing
Term used to describe a level design pacing problem. Imagine the annoying persistence of a leaking faucet - it's easy to fall into a pattern of placing encounters into a level at very regular intervals. This problem is usually addressed very simply by removing entire encounters, as many designers will tend towards too much combat in early iterations. The issue can also be addressed by paying attention to relative intensity of encounters, and making sure there is an interesting progression rather than a linear one.

#### LinkedRef
Shorthand for "Linked Reference". Refers to the target of a Linked Reference relationship, which can be set in the Reference Properties of most references, from the Linked Ref tab. LinkedRefs may optionally have a keyword specified, which is helpful for references that need multiple associations/relationships. This is commonly used in package building and scripting.

#### LocRefType
Shorthand for Location Reference Type. This is a tag that can be applied to a reference, used by the [Radiant Story](https://ck.uesp.net/wiki/Radiant_Story "Radiant Story") system to populate variable with appropriate objects and locations.



#### [Navmesh](https://ck.uesp.net/wiki/Category:Navmesh "Category:Navmesh")

[Navmesh](https://ck.uesp.net/wiki/Category:Navmesh "Category:Navmesh") is an editor-created three-dimensional shape which exists for the purpose of providing AI with navigation details in 3D space. The primary function of navmesh is simply to define where an actor can path, but navmesh can also include meta-data such as cover, ledges, water, and preferred routes.



#### Object
Can mean different things depending on context. Usually refers to a [form](https://ck.uesp.net/w/index.php?title=Form&action=edit&redlink=1 "Form (page does not exist)") in the [masterfile](https://ck.uesp.net/wiki/Masterfile "Masterfile") or added by a mod. Often (but not always) either a [Base Object](https://ck.uesp.net/wiki/Glossary#Base_Object) or an [Object Reference](https://ck.uesp.net/wiki/Glossary#Object_Reference).

When discussing Papyrus Scripting, an Object can refer to any of the [Script Objects](https://ck.uesp.net/wiki/Script_Objects "Script Objects") (which correlate closely to forms.)

#### Object Reference
Generally referred to as a "Reference" or "Ref", an Object Reference is an instance of an Object, placed in the world. For example, there is only one **NorRmSmWallSideExSm01** Base Object - but you can place as many instances of that object as you like. Each of these instances is a reference to the Base Object: so, each one is an Object Reference. References are explained in more depth on their own page: see [Reference](https://ck.uesp.net/wiki/Reference "Reference").

#### Orthographic View

Sometimes shortened to "Ortho", orthographic view is a type of rendering/projection which displays a 3D space with no vanishing point. This is extremely useful for a blueprint-type view where walls appear as straight lines, allowing for very precise placement of objects in a space.

Orthographic view can be toggled in the Creation Kit with the "**0**" (zero) hotkey.

[More information is available on wikipedia.](http://en.wikipedia.org/wiki/Orthographic_projection)


#### Pisa Problem
A problem in visual design. The term refers to the [Leaning Tower of Pisa](http://en.wikipedia.org/wiki/Leaning_Tower_of_Pisa), which is remarkable specifically because remains standing although it doesn't look like it should remain standing. Because videogame locations are not required to obey the laws of physics, a structure such as the Tower would simply look ill-conceived.

In general, the Pisa problem is a reminder to build spaces that look physically grounded and feasible.

#### Prefab
Prefab is a shorthand term used to refer to a collection of objects which can be easily copied to provide some complex functionality, such as multi-object traps, puzzles and creature ambushes. These are provided in interior cells with the _warehouse_ prefix.

Note that "prefab" is not a form type in the Creation Kit. It's just the term applied by the team to these kinds of pre-configured setups.


#### Quest Item
The Quest Item check box is available on most base objects. Objects marked as Quest Item cannot be dropped from the player's inventory, are not counted against encumbrance, and are not cleaned up when a cell is reset (and are not cleared from reset inventories). Actors marked as quest items update more frequently.


#### Reference
Also known as "Ref"s, there are various types of reference in the Creation Kit. Generally, though, when speaking about references, people will mean [Object References](https://ck.uesp.net/wiki/Glossary#Object_Reference "Glossary").

#### [Regions](https://ck.uesp.net/wiki/Region "Region")
Regions are a means of storing data about blocks of cells in [[World Spaces]]. In _Skyrim_, they are primarily used as a way to assign [Weather](https://ck.uesp.net/wiki/Weather "Weather") to exterior cells.

#### Rendering
Rendering is a computer science term for drawing an image on-screen. On this wiki, it refers to any 3D objects which the Creation Engine is currently displaying. It is important to note that a rendered image is not always visible. This is why optimization is important: it helps content creators cut down on the amount of wasted rendering by ensuring that as few objects as possible are unnecessarily rendered.

For more information, check out the [Rendering article on wikipedia](http://en.wikipedia.org/wiki/Rendering_(computer_graphics))

#### Roombound
A synonym for "Room Marker"

#### Room-Hall-Room
Refers to a pacing problem in level design. It's very easy for a level to fall into a rut where the space simply feels like a series of random rooms connected by repetitive hallways. This is usually the sign of a level in early stages of design. Room-Hall-Room can be addressed by replacing bland hallways with more interesting traversal spaces, giving rooms a sense of cohesive purpose in the larger meaning of a level, and tuning encounter pacing.

#### Room Marker
A cube used to encompass references for the sake of manual occlusion. Room Markers are linked to each other via portals, helping the Creation Engine make better decisions about what to cull and render. [More information is available in this tutorial.](https://ck.uesp.net/wiki/Bethesda_Tutorial_Optimization "Bethesda Tutorial Optimization")


#### Skybox
A common game development term for an unreachable area created as a sort of diorama to create the illusion of an opening to sky. In Skyrim these usually consist of ceiling holes where a patch of sky can be seen, and additional clutter such as foliage is often used to make the illusion more convincing.


#### Triangle
In the context of [navmesh](https://ck.uesp.net/wiki/Category:Navmesh "Category:Navmesh"), a triangle or "tri" is a 3-sided polygon.


#### UI
Common acronym for "User Interface". Used interchangeably with GUI and HUD, or "Graphical User Interface", and "Heads-Up Display", respectively.


#### Vertex
A vertex, or "vert", is a point in 3D space. When working with [navmesh](https://ck.uesp.net/wiki/Category:Navmesh "Category:Navmesh"), vertices(plural) are used to create the corners of triangular polygons.


#### Z-Fighting
In videogames, this term refers to a common visual bug where a surface flickers erratically because two objects are co-planar. Z-Fighting in the Creation Kit is commonly caused by the accidental duplication of static objects, or placement of decal objects directly on a surface with no offset.