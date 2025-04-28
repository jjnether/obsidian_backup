<table><tbody><tr><th><b><a href="https://ck.uesp.net/wiki/CreationKit:Language_policy" title="CreationKit:Language policy">Language:</a></b></th><td><b><a>English</a></b> <span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="ru"><a href="https://ck.uesp.net/wiki/Weather/ru" title="Weather/ru">русский</a></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></td></tr></tbody></table>

## Weather Object\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=1 "Edit section: Weather Object") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=1 "Edit section: Weather Object")\]

**Weather** objects are found in the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window") under [WorldData](https://ck.uesp.net/wiki/Category:WorldData "Category:WorldData").

To create a new Weather, right-click in the list of Weathers in the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window") and select "new" from the popup. To create a new Weather based off an existing one, right-click the Weather you wish to use as a basis and select "duplicate". To delete an existing Weather, right-click that Weather and select delete.

## Weather Dialog\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=2 "Edit section: Weather Dialog") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=2 "Edit section: Weather Dialog")\]

[![Jb Weather01a.jpg](https://ck.uesp.net/w/images/e/e2/Jb_Weather01a.jpg)](https://ck.uesp.net/wiki/File:Jb_Weather01a.jpg)

## ID\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=3 "Edit section: ID") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=3 "Edit section: ID")\]

The editor ID of the Weather Object.

Note: The ID field of the Weather dialog does not save properly. To name your weather, edit the name using the Object window (left-click).

## Show Color In Render Window\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=4 "Edit section: Show Color In Render Window") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=4 "Edit section: Show Color In Render Window")\]

## General Tab\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=5 "Edit section: General Tab") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=5 "Edit section: General Tab")\]

### Type\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=6 "Edit section: Type") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=6 "Edit section: Type")\]

-   **Ambient**: An underlying color for the scene.
-   **Cloud Layer**: Color of the cloud texture currently selected in the "Cloud Textures" section.
-   **Cloud LOD Ambient**:
-   **Cloud LOD Diffuse**:
-   **Effect Lighting**: The color used for object reference [External Emittance](https://ck.uesp.net/wiki/Glossary#External_Emittance "Glossary") which is determined by the active weather in a [Region](https://ck.uesp.net/wiki/Glossary#Regions "Glossary").
-   **Fog Far/Near**: Fog color. This also adjusts the color of water reflections.
-   **Horizon**: The color of the sky at the horizon.
-   **Moon Glare**:
-   **Sky Statics**: The color of the static cloud objects that can be placed independently in the render window.
-   **Sky-Lower/Upper**: The color of the sky at lower and upper levels. (horizon color blends into lower sky color and lower sky blends into upper sky color)
-   **Stars**: The color of the stars.
-   **Sun**: The color of the sun disc.
-   **Sun Glare**:
-   **Sunlight**: The color of the sunlight. This is the directional light color for the scene.
-   **Water Multiplier**:

### Time\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=7 "Edit section: Time") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=7 "Edit section: Time")\]

-   **Day**: The color of the specified component during the daytime.
-   **Night**: The color of the specified component at nighttime.
-   **Sunrise**: The color of the specified component at sunrise.
-   **Sunset**: The color of the specified component at sunset. (see [Climate](https://ck.uesp.net/wiki/Climate "Climate") pageon how to define these times of day)

### Color\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=8 "Edit section: Color") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=8 "Edit section: Color")\]

Enter specific RGB values or press "Select Color" and use the color picker.

### ImageSpace\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=9 "Edit section: ImageSpace") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=9 "Edit section: ImageSpace")\]

Choose an [ImageSpace](https://ck.uesp.net/wiki/ImageSpace "ImageSpace") from the drop down list that is used the weather type.

### Aurora\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=10 "Edit section: Aurora") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=10 "Edit section: Aurora")\]

### Fog Distance Day/Night\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=11 "Edit section: Fog Distance Day/Night") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=11 "Edit section: Fog Distance Day/Night")\]

Specify near and far clip planes for fog during different times of day. These also effect how water reflects the fog color.  

-   **Near/Far**:
-   **Pow**:
-   **Max**:

### Cloud Textures\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=12 "Edit section: Cloud Textures") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=12 "Edit section: Cloud Textures")\]

Click "Edit" to choose a cloud texture (.dds) for current layer.

-   **Layer**:Selects which cloud layer to make changes to.
    -   Layer 0: Layer for "upper" cloud textures. Works with "CloudsUpper01\_d", "CloudsUpper02\_d", "SkyrimCloudsUpper01", and "SkyrimCloudsUpper02".
    -   Layer 1: Used for "upper" cloud textures as well. Works with the same textures as Layer 0, but they actual clouds appear in different positions in the sky.
    -   Layer 2: Only works with "CloudsLower04\_d" and "SkyrimCloudsLower04".
    -   Layer 3: Only works with "CloudsHorizon01\_d" and "SkyrimCloudsHorizon01".
    -   Layer 4:
    -   Layer 5:
    -   Layer 6:
    -   Level 7:
    -   Level 8: Only works with "CloudsHorizon01\_d" and "SkyrimCloudsHorizon01".
    -   Level 9: Only works with "CloudsHorizon01\_d" and "SkyrimCloudsHorizon01".
    -   Level 10:
    -   Level 11:
    -   Level 12: Only works with "Clouds\_Fill\_d" and "SkyrimCloudsFill".
    -   Level 13: Only works with "CloudsHorizonLight01\_d".
    -   Level 14: Only works with "CloudsLowerLight01\_d" and "CloudsLowerLightB01\_d".
    -   Level 15: Only works with "CloudsLowerLight01\_d" and "CloudsLowerLightB01\_d".
-   **Disabled**:
-   **Cloud Speed**: Selects the speed the clouds move on the current layer.
-   **Alpha**:

### Wind Direction\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=13 "Edit section: Wind Direction") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=13 "Edit section: Wind Direction")\]

### Wind Dir Range\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=14 "Edit section: Wind Dir Range") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=14 "Edit section: Wind Dir Range")\]

### Wind Speed\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=15 "Edit section: Wind Speed") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=15 "Edit section: Wind Speed")\]

How windy it is. Affects tree and grass movement.

### Trans Delta\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=16 "Edit section: Trans Delta") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=16 "Edit section: Trans Delta")\]

In game hours, how long it takes to fully transition into this weather type once a transition begins.

### Sun Glare\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=17 "Edit section: Sun Glare") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=17 "Edit section: Sun Glare")\]

How much glare there is around the sun disc.

### Sun Damage\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=18 "Edit section: Sun Damage") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=18 "Edit section: Sun Damage")\]

How much damage the sun does to vampires during daytime hours.

## Direction Ambient Tab\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=19 "Edit section: Direction Ambient Tab") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=19 "Edit section: Direction Ambient Tab")\]

Choose from Day, Night, Sunrise, and Sunset.

### Set From Ambient\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=20 "Edit section: Set From Ambient") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=20 "Edit section: Set From Ambient")\]

### X+/-\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=21 "Edit section: X+/-") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=21 "Edit section: X+/-")\]

### Y+/-\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=22 "Edit section: Y+/-") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=22 "Edit section: Y+/-")\]

### Z+/-\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=23 "Edit section: Z+/-") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=23 "Edit section: Z+/-")\]

### Specular\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=24 "Edit section: Specular") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=24 "Edit section: Specular")\]

-   Enter specific RGB values or press "Select Color" and use the color picker.
-   **Fresnel Power**:

## Precipitation Tab\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=25 "Edit section: Precipitation Tab") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=25 "Edit section: Precipitation Tab")\]

### Precipitation\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=26 "Edit section: Precipitation") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=26 "Edit section: Precipitation")\]

-   Choose a [Shader Particle Geometry](https://ck.uesp.net/wiki/Shader_Particle_Geometry "Shader Particle Geometry") from the drop down to be used as the precipitation model (.nif).
-   **Begin Fade In**: Slider specifies the point in time along a transition _into_ this weather type when particles will begin to enter the scene.
    -   Example: A value of 0.8 means that you will begin seeing precipitation particles after this weather is 80% transitioned in.
-   **End Fade Out**: Slider specifies the point in time along a transition _out of_ this weather type when particles will no longer appear in the scene.
    -   Example: A value of 0.2 means that you will no longer see precipitation once a transition out of this weather type into another one is 20% complete.

### Thunder/Lightning\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=27 "Edit section: Thunder/Lightning") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=27 "Edit section: Thunder/Lightning")\]

-   **Begin Fade In:** Slider specifies the point in time along a transition _into_ this weather type when particles will begin to enter the scene.
    -   Example: A value of 0.8 means that you will begin seeing precipitation particles after this weather is 80% transitioned in.
-   **End Fade Out:** Slider specifies the point in time along a transition _out of_ this weather type when particles will no longer appear in the scene.
    -   Example: A value of 0.2 means that you will no longer see precipitation once a transition out of this weather type into another one is 20% complete.
-   **Frequency:** Slider determines how frequently you will see thunder/lightning.

### Weather Classification\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=28 "Edit section: Weather Classification") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=28 "Edit section: Weather Classification")\]

Choose the appropriate classification for this weather type. This will affect things such as water surfaces, NPC dialogue, and other game logic.

-   **Pleasant**:
-   **Cloudy**:
-   **Rainy**:
-   **Snow**:
-   **None**:

### Lightning Color\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=29 "Edit section: Lightning Color") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=29 "Edit section: Lightning Color")\]

Choose a color for lightning flashes. (Enter specific RGB values or press "Select Color" and use the color picker.)

## Sound Tab\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=30 "Edit section: Sound Tab") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=30 "Edit section: Sound Tab")\]

Drag and drop sounds from the [Object Window](https://ck.uesp.net/wiki/Object_Window "Object Window") into this list. Double-click a sound to toggle its type.

-   The list box defines every sound associated with this weather type.
-   Wind and precipitation sounds play as looping sounds while thunder sounds will play as a one-time sound when a lightning strike is initiated by the system.
-   To delete a sound, right-click the sound and select delete.

## Effects Tab\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=31 "Edit section: Effects Tab") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=31 "Edit section: Effects Tab")\]

### Visual Effect\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=32 "Edit section: Visual Effect") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=32 "Edit section: Visual Effect")\]

Choose a [Visual Effect](https://ck.uesp.net/wiki/Visual_Effect "Visual Effect") from the drop down list.

-   **Begin Effect**:
-   **End Effect**:

### Sky Statics\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=33 "Edit section: Sky Statics") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=33 "Edit section: Sky Statics")\]

## See Also\[[edit](https://ck.uesp.net/w/index.php?title=Weather&veaction=edit&section=34 "Edit section: See Also") | [edit source](https://ck.uesp.net/w/index.php?title=Weather&action=edit&section=34 "Edit section: See Also")\]

-   [Weather Script](https://ck.uesp.net/wiki/Weather_Script "Weather Script")