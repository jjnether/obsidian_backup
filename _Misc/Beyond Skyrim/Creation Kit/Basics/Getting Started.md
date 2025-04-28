This first chapter of the tutorial will go over the basics of getting up and running with the Creation Kit.

Throughout these tutorials, the following symbols will be used to call out different kinds of special notes. Take note of the symbols associated with each type of callout box: you may wish to take special note of certain type in particular, depending on your expertise level.

| [![NewFeature.jpg](https://ck.uesp.net/w/images/thumb/d/dc/NewFeature.jpg/48px-NewFeature.jpg)](https://ck.uesp.net/wiki/File:NewFeature.jpg) | This symbol indicates a new tool or technique that users of previous Bethesda toolsets may want to take note of. |
| --------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |

| [![InDepth.jpg](https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg)](https://ck.uesp.net/wiki/File:InDepth.jpg) | These notes will go in depth to explain a term or the reasoning behind a specific technique. Most users can skim these notes, but advanced users may wish to come back and study them later. |
| --------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| [![Protip.jpg](https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg)](https://ck.uesp.net/wiki/File:Protip.jpg) | These are helpful tips and shortcuts. They are often useful for speeding up workflow after learning the basics. |
| ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |

| [![Achtung.png](https://ck.uesp.net/w/images/f/f0/Achtung.png)](https://ck.uesp.net/wiki/File:Achtung.png) | These are quick warnings - gotchas, common errors and stuff to watch out for. |
| ---------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |

## Installing the Creation Kit
[![](https://ck.uesp.net/w/images/thumb/0/02/SteamCreationKit.jpg/300px-SteamCreationKit.jpg)](https://ck.uesp.net/wiki/File:SteamCreationKit.jpg)

Locating the Creation Kit in Steam Tools

Whether you have ambitious mod plans, a simple tweak idea, or just want to fool around, you'll need to install the Creation Kit first. Since the release of Skyrim: Special Edition, there are two different versions of the Creation Kit available.

### For the original version of Skyrim

Make sure you have a [Steam account](http://store.steampowered.com/about/) and [the original version of Skyrim](http://store.steampowered.com/app/72850/).

1.  Install Steam
2.  Login
3.  Hover over the "LIBRARY" button.
4.  Select "Tools"
5.  Double-click "Skyrim Creation Kit" in the list
6.  Follow the instructions in the installation dialog

### For Skyrim: Special Edition

1.  Install Steam
2.  Login
3.  Hover over the "LIBRARY" button
4.  Select "Software"
5.  Double-click "Skyrim Special Edition: Creation Kit" in the list
6.  Follow the instructions in the installation dialog

Creation Kit: Skyrim will normally be installed to the same folder as your Skyrim: Special Edition folder.

## Creating and saving plugins

Let's talk about how to load some data.

#### Understanding the Creation Engine Data Format

The Creation Engine uses the same data format as previous Bethesda Game Studios titles. **Master Files**, which use the ".esm" extension, are large collections of data. Skyrim.esm is the master file which contains all the data used by the base game.

**Plugins**, or ".esp" files, are smaller collections of data which can be loaded "on top" of master files. These plugins may modify or reference data contained within a master file, or they may introduce entirely new data. Multiple plugins may be loaded by the game or editor. When working in the Creation Kit, only one plugin may be considered the **"active file"**, meaning any changes will be saved to that plugin when the user saves.

The important thing to remember is that a plugin will be the primary save file for your mod. We'll create one now.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>Loading multiple plugins can introduce conflicts. For example, if you load two mods which customize <i>EncTrollFrost</i>, only one of those mods will be permitted to "win". Generally, this is the last-loaded plugin, making load order an important consideration for larger mod projects or playing with several mods active at once.</td></tr></tbody></table>

#### Creating Your First Plugin

When the editor starts up for the first time, there will be no data loaded. You'll probably want to use the Skyrim.esm and Update.esm files as your plugin's master files, so you should load them first. (The plugin that you're creating will **not** overwrite the master files.) To get started, navigate to **File>Data** from the [Main Toolbar](https://ck.uesp.net/wiki/Main_Toolbar "Main Toolbar"). You should see a dialog box similar to Fig. 1, shown below. Double-click the Skyrim.esm master file for loading, then double click the Update.esm master file. They should each have an "X" in the box on the left. Then click **OK**. Skyrim.esm will take some time to load. Be patient, as this process can take a minute or two, depending on your hardware.

Note that some warnings will appear when loading Skyrim.esm. These are normal and can be ignored. Just select **Yes to All** or press Escape to dismiss them.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>If the warning popup window pops up too often and is distracting you, you can move the window behind eg. the object window. This way it will not popup every time something is reported.<p>When you need to check the warning window, drag the object window aside and bring the warning window to front.</p></td></tr></tbody></table>

  
Once loading is complete, the very first thing to do is create a "plugin", which is the mod file where your work will be saved. To do this, simply navigate to **"File>Save"** from the main toolbar. Since you have no active plugin (.esp) file specified, the Creation Kit will prompt you to create a new one. For this series of tutorials, save a file called _testquest.esp._

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>If you are <b>not</b> prompted to create a new plugin when saving, you probably already have an active file set, which will be overwritten if you leave it open. Reopen <b>File&gt;Data</b> to ensure you have no active file selected when loading Skyrim.esm. The Creation Kit has no "save as" feature, and all saves will re-write the active plugin.</td></tr></tbody></table>

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:InDepth.jpg"><img alt="InDepth.jpg" src="https://ck.uesp.net/w/images/thumb/0/0b/InDepth.jpg/48px-InDepth.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/0/0b/InDepth.jpg 1.5x"></a></td><td>If you wish to make a backup of your plugin file or install one from another source, you will find the plugins in the Data subfolder of wherever Steam is installed on your hard drive.<p>For 64bit systems this is normally: <code>C:\Program Files (x86)\Steam\SteamApps\common\Skyrim\Data\..</code><br>For the more common 32bit system, this will be: <code>C:\Program Files\Steam\SteamApps\common\Skyrim\Data\..</code></p></td></tr></tbody></table>

-   [![](https://ck.uesp.net/w/images/thumb/c/c5/DataFilesDialog01.jpg/270px-DataFilesDialog01.jpg)](https://ck.uesp.net/wiki/File:DataFilesDialog01.jpg)
    
    **Fig. 1**: Choosing and loading data files. This is what you'll see after you create _testquest.esp_ when you load both Skyrim.esm and your new plugin. Note that _testquest.esp_ is labeled "Active File", which means that it's the file to which all changes will be saved.
    

## Loading a plugin in the game

Even though your plugin is currently empty, let's go over how to load it up in-game.

First, you'll need to tell Skyrim to load your plugin when the game starts. There are two ways to do this:

1.  From the main game launcher, select "Data" and double-click your plugin. If using Skyrim Special Edition, go to the game's Main Menu, click MODS then click LOAD ORDER to find your plugin.
2.  Advanced users may prefer to append to the %LocalAppData%/Skyrim Special Edition/plugins.txt file the following line:

```
*testquest.esp

```

For now, just use the launcher to select the plugin you just created.

Run the game as usual. Once skyrim has started up, use **"~"** to open the [console](https://ck.uesp.net/wiki/Category:Console_Commands "Category:Console Commands"). (You can close it again with the ~ key, too) This allows us access to many special debugging commands which are important for testing our plugins. The console is available from the main menu and at any point while running the game except during loading screens.

We don't have anything in our plugin yet, but we can still use a few [Console Commands](https://ck.uesp.net/wiki/Console_Commands "Console Commands"). Try entering the following lines, hitting **Enter** after each line:

```
TGM
TWF
COC RiverwoodSleepingGiantInn

```

We've just enabled invincibility (`TGM`: [ToggleGodMode](https://ck.uesp.net/wiki/ToggleGodMode "ToggleGodMode")), turned on a wireframe view (`TWF`: [ToggleWireframe](https://ck.uesp.net/wiki/ToggleWireframe "ToggleWireframe")), and teleported into the Inn at Riverwood (`COC`: [CenterOnCell](https://ck.uesp.net/wiki/CenterOnCell "CenterOnCell")). There are a lot of other [console commands](https://ck.uesp.net/wiki/Category:Console_Commands "Category:Console Commands"), and these are just a few examples to give you an idea how it works; there are many more console commands available.

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Protip.jpg"><img alt="Protip.jpg" src="https://ck.uesp.net/w/images/thumb/6/6a/Protip.jpg/48px-Protip.jpg" decoding="async" width="48" height="48" srcset="https://ck.uesp.net/w/images/6/6a/Protip.jpg 1.5x"></a></td><td>Using mods and console commands, it is quite easy to "break" the game, and savegames (and autosaves!) made in that state may be unusable, so do ensure that any saves you care about are in a safe save slot before testing, and are not saved to during testing.<p>You can also open the console while at the main menu and use the <code>COC</code> command without even loading a savegame: this will start you as a basic starting character.</p></td></tr></tbody></table>

-   [![](https://ck.uesp.net/w/images/thumb/e/ea/UsingLauncherToLoadPlugin.jpg/270px-UsingLauncherToLoadPlugin.jpg)](https://ck.uesp.net/wiki/File:UsingLauncherToLoadPlugin.jpg)
    
    **Fig. 2**: The Skyrim Launcher. Plugins can be loaded/unloaded from the **Data Files** menu option.
    

## What Now?

Once you have the Creation Kit installed and running, you're ready to start modding. If you have experience with previous modding tools for Bethesda Game Studios games such as Morrowind, Oblivion or Fallout 3, you may want to spend some time simply exploring the tool to see what's new and what's familiar. You may also like to look over our [What's New?](https://ck.uesp.net/wiki/What%27s_New%3F "What's New?") page for an overview.

If you aren't an experienced modder, we recommend browsing the [Tutorials Hub](https://ck.uesp.net/wiki/Category:Tutorials "Category:Tutorials"), which includes tutorial series designed to take a complete novice through the process of creating a new dungeon and simple quest. Those with modding experience or specific interests may wish to skim these tutorials for specific subject matter they're interested in as well. Example plugins are provided at every stage, so you can simply jump in where your interest lies if you don't wish to do the entire tutorial series.

If you've got a question that isn't answered on the wiki, or if you're just looking for someplace to discuss mod ideas with the community, be sure to check out [the official forums](http://forums.bethsoft.com/index.php?/forum/117-v-skyrim/), or any of the other great Elder Scrolls and Fallout modding communities out there!

Bethesda Game Studios has long enjoyed a thriving and vibrant mod community, which we owe to the creativity and ingenuity of people just like you. It is our sincere hope that you find everything you need here and within the Creation Engine modding community to realize your creative visions. We can't wait to see what you come up with. Good luck!