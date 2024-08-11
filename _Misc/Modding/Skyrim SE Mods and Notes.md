NOTES:
- If using a Skyrim SE version 1.6.xxx, use an anniversary edition version of the mod you are adding
- Use Mod Organizer 2 (or Vortex) as a mod manager
- Must manually install SKSE
- Manually install xSHADOWMANx's Dll Loader  for some mods to work
- Many fixes are included in the SSE engine fixes mod (like achievements enabler)
- If not already present, install d3dcompiler_47.dll from SSE Parallax Shader Fix (beta)
- Concerning the whistle mod (now Simple Horse SE), if you mount a non-permanent horse (like a bandit's), but then it despawns and you whistle, it will ctd. To fix, simply re-mount a different horse or buy one and mount it
- If everything is moving at half speed, this is because the game is running at a higher FPS than it can handle, and SSE Display Tweaks could be the cause

- Use [Bethesda Plugin Manager for Mod Organizer](https://www.nexusmods.com/skyrimspecialedition/mods/111236?tab=description) for better load order management
- Use LOOT to sort load order after every time you alter a mod before playing
- Check LOOT and see if it recommends any patches you don't yet have
- For Overwrite category at bottom of MO2, just create blank mods and drag files to them so they are loaded at the bottom, or right click overwrite and click create mod
- Use SSEEdit Quick Auto Clean to clean the mods (Open this through MO2)(Only clean mods LOOT suggests, but NOT FALSKAAR as per its online instructions) (https://www.youtube.com/watch?v=YpRinGULJGw)
- Do the Dawnguard manual clean
- Manually install BethINI for INI tweaks (like 1440p modification and npc's using arrows) (https://www.youtube.com/watch?v=NI8ezwpZQFw)
- For file conflicts when using Mod Organizer 2, the priority level is what dictates which files will be installed (higher number priority loads later, thus overwriting anything previously loaded)
- Be sure to enable plugins even after installing and enabling the mods (mod may be enabled, but plugin not enabled)
- For NetImmersive Override for SSE, follow the procedure in this video: https://www.youtube.com/watch?v=DyQGE3u5rok
- If missing binkw64.dll, simply download from google search and add to main directory

- Create a Merged patch named SSEMerged (https://www.youtube.com/watch?v=j5Tw3t2MvaU)
- Be sure to first disable FNIS and DynDoLOD output, and delete FNIS output (to be remade later)
- If you have more than 253 .esp files, will need to create two different merged patches (split your mods), then select both patches when choosing what to load in SSEEdit, and create a merged patch with the preselected masters only (https://www.loverslab.com/topic/163943-sse-merged-patch-for-more-than-255-plugins/)
- If making a bashed patch afterwards, be sure to delete leveled lists from merged patch and clean masters
- If you get an error when exiting out, delete the cache then try again

- Create a Bashed patch (https://www.youtube.com/watch?v=W1Es06MtAZM)
- Be sure to rerun FNIS and create its output again after merged and bashed patches

- You can find patch outputs inside of the overwrite folder
- Load Merged patch, then Bashed patch, then patchers (like FNIS)

- Load order should be roughly: most mods, merged patch, bashed patch, FNIS and mods, FNIS output, xp32 skeleton mod, dyndolod textures, dyndolod output, realistic hd tree lod textures

- To manually edit loading settings in LOOT, double click a mod and add it to the load after tab
- Load Cutting Room Floor after Relationship Dialogue Overhaul
- Load Weapons Armor Clothing and Clutter Fixes after Guard Dialogue Overhaul
- MLU after Weapons Armor Clothing and Clutter Fixes
- For my lightweight mods, be sure they load after whatever they're replacing (apocalypse or skyrim alchemy fixed)
- Some mods you may need to get from afkmods.com or moddb.com rather than nexus mods (specifically mods by arthmoor)
- If a quest that you should be able to get is glitched out or you can't move on through a quest through a bug, use the setstage command and lookup the code for the next chapter you should be at
- If you need a console command to become vampire lord, use player.addspell 020083b  (hard to find online)
- SSEEdit Bulk Edit: https://www.youtube.com/watch?v=5wMl6TY_Oqg & - https://www.nexusmods.com/skyrim/mods/49373?tab=description 

Mod List

Scripting
Address Library for SKSE Plugins
BethINI (be sure to point BethINI to the custom .ini files associated with your profile for MO2 if that options is selected in MO2)
ConsoleUtilSSE
JContainer SE
PapyrusUtil
Powerofthree's Papyrus extender
SKSE64
xshadowmanx's dll loader
.net script framework


Game Fixes
Bug Fixes sse
Dragonborn Delayed
Face Discoloration Fix
Immersive Loading Icon
Mfg Fix
No BS AI Projectile Dodge
Remove QuickSave Button from SkyUI System Menu (flashing save game button fix included as well) (requires SkyUI)
SkyrimSE.exe Auto-Backup
Skyrim Skill Uncapper
Spell Perk Item Distributor (SPID)
SSE Display Tweaks 
    • To tweak settings, will have to right click in MO2 and open in explorer, then modify the .ini file within
    • If everything is moving at half speed, this is because the game is running at a higher FPS than it can handle, and this mod could be the cause
SSE Engine Fixes (skse64 plugin)
    • After installing part 1 with mod manager, be sure to manually install part 2
    • Also includes achievements enabling and faster wait/rest, but will need to enable the latter
    • To tweak settings, will have to right click in MO2 and open in explorer, then modify the .toml file within (SleepWaitTimeModifier)
SSE Parallax Shader Fix (beta)
Unofficial Skyrim Special Edition Patch
Weapons Armor Clothing and Clutter Fixes
    • If not using a bashed patch, in MO2, hit manual when installing and deselect WACCF_BashedPatchLvlListFix.esp
60 FPS Menus - Buttery Smooth Interface
    • Get skyui version and optional file for no more CC news

Weapons Armor Clothing and Clutter Fixes (WACCF) and Summermyst Enchantments Patch
    • If applicable


Quality of Life
ABT SE - Arrows and Bolts Tweaks
    • You should add some lines to your skyrim.ini (find info and lines on mod website)
All Thieves Guild Jobs Concurrently
A quality world map - classic with all roads
Better Dialogue Controls
Better Messagebox Controls
Even better quest objectives
Faster Horses
iEquip
Immersive HUD
Lightweight Potions and Poisons
Lightweight Scrolls - USSEP Updated
moreHUD
My Home is Your Home
Open Cities Skyrim
    • Get from modDB rather than Nexus
Quick Loot RE
Remember Lockpick angle - updated
Simple Horse SE
SkyUI
Stones of Barenziah Quest Markers SSE
Unread Books Glow
Wider MCM menu for skyui


Gameplay Changes
Alternate Start - Live another Life
    • Get from modDB rather than Nexus
Amazing Follower Tweaks SE
Andromeda - unique standing stones of skyrim
Apocalypse - magic of skyrim (be sure to also get ordinator patch)
Imperious - Races of Skyrim
Morrowloot Ultimate
Mortal enemies
    • Include Smilodon patch if applicable
Ordinator
Skyrim Alchemy Fixed
Smilodon - combat of skyrim
Summermyst - enchantments of skyrim
Tk dodge
Wards Functionalities Extended
    • Cutting Room Floor patch if applicable

Apocalypse - Magic of Skyrim - Lightweight Scrolls Patch
Skyrim Alchemy Fixed - Lightweight Potions and Poisons Patch
Skyrim Skill Uncapper .ini for ordinator
MLU Community Patches (BS Bruma loot cap patch - Morrowloot)
Alternate start options for beyond skyrim – bruma
    • If applicable

Bonus Game Content
After the Civil War - Siege Damage Repairs
Beyond Skyrim Bruma SE
Beyond Skyrim - Bruma - Tweaks Enhancements and Patches
Cutting Room Floor
Dawnguard and Clan Volkihar Epilogues
Falskaar
    • Don’t clean dirty edits (per online instructions)
Falskaar addons and patches
Helgen reborn
Inigo
Legacy of the Dragonborn
Moonpath to Elsweyr
Paarthurnax Dilemma
Relationship Dialogue Overhaul - RDO SE (will need to manually install patch with MO2 and only install the correct .esp)
Relationship Dialogue Overhaul - Update and MCM
The Forgotten City
Unofficial Moonpath to Elsweyr Patch
Beyond Skyrim - Bruma Moonpath to Elsweyr synergy Patch
Bruma Signs SMIM patch - SE
Legacy of the Dragonborn - Followers Patch (Inigo-Auri-Kaidan-M'rissi)
Legacy of the Dragonborn Patches (official)
Ordinator Beyond Skyrim Patch
Bruma Signs SMIM patch – SE


Graphics
Better Dynamic Snow SE
Blended Roads
Dynamic Distant Objects LOD - DynDOLOD (ONLY IF YOU'RE UP TO THE TASK - SEE NOTES BELOW)
Enhanced Lights and FX (ELFX)
ELFX Fixes
ELFX - Exterior Fixes
HD LODs Textures SE
High Poly Project
Majestic Mountains
Realistic Water Two
Skyrim Flora Overhaul
SMIM
Terrain LOD redone
Underground - a dungeon texture overhaul
Vivid Weathers - Definitive Edition

ELFX Exteriors Open Cities Patch
Unofficial Enhanced Lights and FX ELFX SMIM fps patch for SE


Immersion
Armor and Clothing Extension
Auto Hide Ammo
Blowing in the Wind
Castle Volkihar Rebuilt - SSE
Cloaks of Skyrim SSE
Deadly Dragons
Deadly Spell Impacts
Depths of skyrim
Embers HD
Enhanced Blood Textures SE
ETHEREAL CLOUDS - Special Edition
ETHEREAL COSMOS - Special Edition
Expressive Facial Animation -Female Edition-
Expressive Facial Animation -Male Edition-
Fluffy Snow
Footprints
Frozen Electrocuted Combustion (be sure to also install optional update for poison fix)
Gemling Queen Jewelry SE
Guard Dialogue Overhaul SE
HD Road Signs
HQ tree Bark
Illuminated Atronachs -- Atronachs lumineux
Immersive Armors
    • If using guards armor replacer: within immersive armors mcm, deselect varied guard helmets and disable heroic stormcloak armor distribution
Immersive Bookreading and Lockpicking
Immersive Citizens
Immersive College NPCs
Immersive Patrols
Immersive Weapons
Immersive Weapons Patches SE
Improved Weapon Impact EFFECTS Correct Metal SE
Konahrik's Accoutrements
Luminescent Luna Moths SE
Maximum Carnage (be sure to disable spell death effects in MCM if using with FEC)
Misc. College of Winterhold Tweaks
MultiLayer Parallax Soul Gems SSE
M17 Septim Gold Coin Retexture
No Spinning Death Animation
Obscure's College of Winterhold
Obsidian Mountain Fogs
Opulent Thieves Guild
Point the Way
Predator Vision - Night Eye and Thermal Vision Overhaul
Realistic Aspen Trees
Realistic HD Tree LOD Textures
Run for your Lives
Serana Dialogue Add-On
Serana Dialogue Edit - Skyrim Special Edition
Serana's Hood Fix
Silent Sneak Attack
Simply Bigger Trees
Skyrim 3D Landscapes
Skyrim 3D Rocks
Skyrim Immersive Creatures
Skyrim Is Windy
Sounds of Skyrim Complete SE
Ultimate HD Fire Effects SSE
Violens - A Killmove Mod SE
Volcanic Tundra - Heat Wave Effects
Wet and Cold
Winter Is Coming SSE - Cloaks

Cutting Room Floor - No Snow Under the Roof
what777's Castle Volkihar Rebuilt Patches

Textures
A dentist for Orsimers - HD teeth retexture
Astral Aspect
aMidianBorn Book of Silence SE
Cloaks Of Skyrim Retextured SE
DRAGON PRIEST
DRAUGR
Dust Effects by HHaleyy
ELECTRIFY S.E.
FALMER
Giant
Glorious Doors of Skyrim
Guards armor replacer
HAGRAVEN
Heavy Legion
HD Photorealistic Ivy
HD Reworked Baskets
Iconic's Real Hay (Legacy)
Just Ice
MAMMOTH
Mushroom Retextures Revamped
Natural Teeth
Noble Skyrim full pack 2k
Peltapalooza
Realistic HD Mods Remastered Collection
Ruins Clutter Improved
Ruins Clutter Improved - Fixes
Ruins Puzzle Pillar Retexture
RUSTIC ANIMATED POTIONS and POISONS
Rustic Clothing - Speical Edition
RUSTIC COOKING - Special Edition
RUSTIC DAEDRA - Special Edition
RUSTIC DEATH HOUND and GARGOYLE - Special Edition
RUSTIC DRAGON CORPSE - Special Edition
RUSTIC FROSTBITE SPIDER - Special Edition
RUSTIC SPRIGGAN - Special Edition
SABRECAT
SKELETON
Skyrim 2018 (pfuscher)
Skyrim 2019
Skyrim 202X by Pfuscher ( Formerly 2020)
Snazzy Furniture and Clutter Overhaul (SFCO)
Stunning Statues of Skyrim
Total Character Makeover
TROLL
True HD Nightingale
Ultimate Noble Beds.
VHR - Vanilla Hair Replacer
Vlammenzee's Glass weapons retextured
Webs S.E.

Immersive Patrols - Guards Armor Replacer consistency Patch


Patches
QUASIPC - Unified Patch Compendium
    • No need to install the Cloaks patch because it is included in the cloaks mod itself
WiZkiD Patches Compendium
kryptopyr's Patch Hub


CBBE conversion
BodySlide and Outfit Studio
Caliente's Beautiful Bodies Enhancer -CBBE- (Let CBBE overwrite total character makeover)
Immersive armours - sse cbbe bodyslide
Heavy legion cbbe bodyslide
Guard Armor Replacer SE - BHUNP - 3BA - CBBE
Weapons Armor Clothing and Clutter Fixes - CBBE Patch
Bijin NPCs SE
Bijin Warmaidens SE
Bijin Wives SE
Bijin Family Bodyslides - CBBE and UUNP SE

NOTE:
- Be sure to build each of the bodyslide batches to see the CBBE armors:
    - Open Bodyslide
    - Click the magnifying glass in the middle of the top row and select "Choose groups..."
    - Choose which group you want
    - Select the preset you want the outfits to be formed to
    - Click on batch build and then okay
    - If you select build morphs, create mod from overwrite folder and activate (don't need this unless using a mod that needs it)
    - You can also just find a single outfit and hit built with your preset selected


FNIS
Fores New Idles in Skyrim SE - FNIS SE
XP32 Maximum Skeleton Special Extended - XPMSSE
Stronger Swimming Animation SE
Feminine Jarl Sitting Animation SE
Pretty Jump Animations
FNIS Sexy Move SE
Pretty Combat Animations SSE
1hm and Dual Wield Animations Overhaul SSE
Magic Casting Animations Overhaul SSE


NOTES:
- Install FNIS and all other mods, then run GenerateFNISforUsers inside the tools folder of FNIS install, and add the output files to the load order
- After installing XP32 skeleton mod, no need for realistic ragdolls and forces mod
- Install FNIS TK dodge patch when running generate file


--DAR--
Dynamic Animation Replacer
Dynamic Random Female Idles V2
Pretty Sit Idles SE
Pretty Female Idles SSE

NOTES:
- First install DAR and Dynamic Random Female Idles, then only download (not install) other idle animations
- For idle animations, simply rename each .hkx you want and place in the Dynamic Random Female Idles directory (with the .jar), then run the .jar
- For sit idle animations (and all others), add a numbered folder in the correct DAR directory (ex. mods\Dynamic Animation Replacer\meshes\actors\character\animations\DynamicAnimationReplacer\_CustomConditions\4107) (folder will change for different types of animations)
- Place each .hkx you want into its own numbered folder with the correct filetree (female\chair_idlebasevar1.hkx)
- Edit/add the _conditions.txt file as needed (see below or in DAR and Dynamic Random Female Idles Documentation)
- ID's found below are FormID/BaseID


IsFemale() AND                              					<--- This line tells DAR to use the animations on females
NOT IsFemale() AND   											<--- This line tells DAR to exclude females (only males)
NOT IsVoiceType("Skyrim.esm"|0x00013AE2) AND					<--- These lines tell DAR to use these animations for all females EXCEPT elderly
NOT IsVoiceType("Skyrim.esm"|0x00013AE1) AND					<
NOT IsVoiceType("Skyrim.esm"|0x00013AD7) AND					<
NOT IsVoiceType("Skyrim.esm"|0x00013aD6) AND					<
NOT IsRace("Skyrim.esm"|0x00067cd8) AND							<
NOT IsChild() AND												<--- This line tells DAR to exclude children as well
IsActorBase("Skyrim.esm" | 0X000007) AND    					<--- This line tells DAR to only use the animations on the player character (remove if you want to apply animations to NPC's)
Random(1.0000)                                                  <--- This line tells DAR the randomization to use. All numbers WILL NOT be the same. DO NOT EDIT



----DynDOLOD Notes----
- Follow this tutorial for the most part (https://www.youtube.com/watch?v=hMrjXivssso) (Be sure to select all worlds when running dyndolod)
- Billboards from Simply Bigger Trees and Skyrim Flora Overhaul must be downloaded
- For open cities, you need to deviate a bit; follow this video at 36:00 (https://www.youtube.com/watch?v=1_5MWqeHIzw&t=2159s) (be sure to edit DynDOLOD_SSE.ini, not DynDOLOD_TES5.ini)

----ENB----
SkyrimSE Re-Engaged ENB (follow instructions on page for installing ENB)
ENB Helper
ENB (not on nexus)
Skyrim Particle Patch for ENB (not on nexus) (if used with ENB Helper, install everything but .esp)

NOTE: May need to edit enblocal.ini for vsync options and fps unlimiting to go with SSE Display Tweaks

----------------------------------------------------------------

Skyrim Together (STR) Mods

Scripting
Address Library for SKSE Plugins
BethINI 
    • be sure to point BethINI to the custom .ini files associated with your profile for MO2 if that options is selected in MO2
SKSE64
    • Use Anniversary edition if on Skyrim SE 1.6.xxx 


Game Fixes
Bug Fixes sse?
No BS AI Projectile Dodge?
SkyrimSE.exe Auto-Backup
    • Install Manually
SSE Display Tweaks?
    • To tweak settings, will have to right click in MO2 and open in explorer, then modify the .ini file within
        ◦ For STR, you should turn off havok in the .ini so it uses default havok
Unofficial Skyrim Special Edition Patch (use version 266-4-2-6a)
Weapons Armor Clothing and Clutter Fixes
    • If not using a bashed patch, in MO2, hit manual when installing and deselect WACCF_BashedPatchLvlListFix.esp
60 FPS Menus - Buttery Smooth Interface
    • Get skyui version and optional file for no more CC news


Quality of Life
A quality world map - classic with all roads
Better Dialogue Controls
Better Messagebox Controls
Immersive HUD
Lightweight Potions and Poisons
Lightweight Scrolls - USSEP Updated
SkyUI


Gameplay Changes
Skyrim Together Reborn
Open World Loot - Encounter Zone and Loot Overhaul
    • An STR compatible replacement for Morrowloot
    • Include specialized loot (optional)
Alternate Start - Live another Life (every player uses separately, then joins together after loading into the world)
Odin?
Mortal enemies?
Skyrim Alchemy Fixed
Summermyst - enchantments of skyrim
Wards Functionalities Extended?
    • Cutting Room Floor patch if applicable
Skyrim Alchemy Fixed - Lightweight Potions and Poisons Patch
Alternate start options for beyond skyrim – bruma
    • If applicable


Bonus Game Content
Beyond Skyrim – Bruma
Beyond Skyrim - Bruma - Tweaks Enhancements and Patches SSE
Cutting Room Floor – SSE
kryptopyr's Patch Hub

Graphics
Static Mesh Improvement Mod?
Skyrim Flora Overhaul SE

Immersion
Immersive Armors
Immersive Weapons
Immersive Weapons Patches SE
Cloaks of Skyrim SSE


Textures


NOTE:
- If you notice naked NPC’s, just do the command /resetinventory to make clothes reappear
- Be sure to disable CC content (not including _ResourcePack files)
- If Address Library is looking in the wrong place (you have a non-default install directory), you might have to run the following .reg file with proper paths:
----------------------------------------------------------------
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\SOFTWARE\TiltedPhoques\TiltedEvolution\Skyrim Special Edition]
"TitlePath"="C:\\Modding\\MO2_STR\\SKYRIM_INSTALL"
"TitleExe"="C:\\Modding\\MO2_STR\\SKYRIM_INSTALL\\SkyrimSE.exe"
----------------------------------------------------------------

To download and install steamCMD and separate install of skyrim:

- Download steamCMD (https://steamcdn-a.akamaihd.net/client/installer/steamcmd.zip)
- Run it in a dedicated folder (steam folder is ok)
- Run steamCMD
- force_install_dir <where you want to download the game files>
- login <your steam account login name>
- app_update <game's appid, 489830 for SkyrimSE> validate


----------------------------------------------------------------

--Maybe good Mods--
Carlotta Valentia - Happy Ending SSE
Honed Metal
Deadly Mutilation
Display Enemy Level
SPERG (instead of ordinator)
Marry Me Serana
my home is your home
amazing follower tweaks
Skyrim Sizes
TK Hitstop
unique uniques
ENB
YOT - Your Own Thoughts

CONSIDER: https://www.youtube.com/watch?v=3AfN6hGtRi0


Unofficial Skyrim Special Edition Patch – USSEP – OLD LINKS:
    • 266-4-2-6a: https://www.nexusmods.com/skyrimspecialedition/mods/266?tab=files&file_id=241103
        ◦ Last AE pre CC dependent version
    • 266-4-2-9a: https://www.nexusmods.com/skyrimspecialedition/mods/266?tab=files&file_id=392477
        ◦ 1.6.640
    • 266-4-2-5b: https://www.nexusmods.com/skyrimspecialedition/mods/266?tab=files&file_id=209150
        ◦ 1.5.97
        ◦ Also last version that worked with SkyrimVR
    • 266-4-3-0a : https://www.nexusmods.com/skyrimspecialedition/mods/266?tab=files&file_id=449719
        ◦ 1.6.1130