Sublime Text is a new text editor that has a lot of modern features, a pretty cool dev community, and a very slick feel to it. We've made a package for it that makes it a good tool for developing Papyrus scripts.

## Loading syntax highlighting and auto-complete

1.  Go to [the Sublime Text website](http://www.sublimetext.com/2) and install the latest release of version 2.
2.  Run the program at least once so it will set up its preferences and whatnots.
3.  Copy the Papyrus folder from [this zip file](https://ck.uesp.net/w/images/3/33/Papyrus.zip "Papyrus.zip") to your local drive: `%AppData%\Sublime Text 2\Packages` or `\Sublime Text 2\Data\Packages`, if the portable version of Sublime Text 2 is used.
4.  If you have Skyrim installed somewhere outside of `C:\Program Files\Steam\steamapps\common\` or `C:\Program Files (x86)\Steam\steamapps\common\`, then you need to set the correct paths in SublimePapyrus.ini, which can be created by running the command "Papyrus INI: Create default INI file" in Sublime Text's Command Palette (CTRL+SHIFT+P).

> [SublimePapyrus](https://github.com/Kapiainen/SublimePapyrus) is an updated version, which also supports Sublime Text 3, of the package linked above. An archived version can be downloaded [here](http://www.creationkit.com/images/4/42/SublimePapyrus.zip) (updated December 18, 2014), if the GitHub repository is inaccessible. SublimePapyrus includes snippets for Skyrim (1.9.32.0.8), SKSE (1.7.1), SkyUI SDK (4.1), FISS (1.21), NetImmerse Override (2.9.6), DienesTools (1.0), JContainers (3.1.1), PapyrusUtil (2.8), and SkyUILib (1).

## Quick Compile

Assuming that your copy of the Papyrus Compiler and its associated batch files are in their default locations and "Tools" > "Build System" > "Papyrus" has been selected, you should be able to hit F7 or Ctrl+B while looking at a Papyrus file to run it through the compiler. (The output will appear in the bottom panel, so be sure to check for any errors!)

-   See [Papyrus Compiler Reference](https://ck.uesp.net/wiki/Papyrus_Compiler_Reference "Papyrus Compiler Reference") for more information.

## Updating the snippets

The existing Papyrus package for Sublime Text includes a number of snippets that will auto-complete to frequently used things (like typing "onhit" and then tab will create a proper OnHit event so you don't have to constantly be looking up the syntax). If you want to make more of these, you can simply add another .sublime-snippet file to the Package directory. Documentation on snippets is available at [Sublime Text docs site](http://www.sublimetext.com/docs/2/).

-   [Papyrus Event Snippets](https://ck.uesp.net/w/images/6/6f/Papyrus_Event_Snippets.zip "Papyrus Event Snippets.zip").

## Viewing Papyrus Assembly

If you're interested in viewing Papyrus assembly files (the midway point between source and compiled scripts, file extension .pas), a package is available that provides syntax highlighting and a build system for the Papyrus assembly language.

This package is currently available on Skyrim Nexus - [Papyrus Assembly package for Sublime Text 2](http://skyrim.nexusmods.com/mods/24009)