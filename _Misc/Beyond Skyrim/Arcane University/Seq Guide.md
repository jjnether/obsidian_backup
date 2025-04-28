What is the function of an SEQ file? If you've ever created a new quest entry in the Creation Kit only to find that it mysteriously doesn't run in-game, this is because the game needs a file associated with it to recognize the new data. (Ticking Start Game Enabled doesn't do anything on its own.)

Luckily, this is very quick and easy to do.

## Install xEdit

Install [TES5Edit](https://www.nexusmods.com/skyrim/mods/25859/) for Classic Skyrim (LE), or [SSEEdit](https://www.nexusmods.com/skyrimspecialedition/mods/164) for Skyrim Special Edition. This tool is incredibly useful for many purposes. Leave an endorsement if you like.

## Load your mod

Open TES5Edit and make sure that the .esp you've been working on is ticked. Let the loader run until everything is shown on the left.

## Create SEQ file
Right click on your .esp, go down to Other and then click 'Create SEQ File'.

[![SEQMenu.png](https://wiki.beyondskyrim.org/w/images/8/8e/SEQMenu.png)](https://wiki.beyondskyrim.org/wiki/File:SEQMenu.png)

## Success message

Wait a moment and you should see the log post a successful message. If not, try again or relaunch xEdit.

[![SeqSuccessMessage.png](https://wiki.beyondskyrim.org/w/images/c/ce/SeqSuccessMessage.png)](https://wiki.beyondskyrim.org/wiki/File:SeqSuccessMessage.png)

## Check and distribution

You are done. Go to `Skyrim\Data\seq` and you should see the name of your .esp. You can now run it in-game, provided you've set it up properly in the CK, of course. Remember to include this file with the archive when uploading to the Nexus or Steam Workshop.

## When to generate the SEQ file again

You should generate the SEQ file again if you add or remove a Start Game Enabled quest from your mod. You do not need to generate it again simply because you added more dialogue to a Start Game Enabled quest. A SEQ file is essentially just a list of the quests that are marked as Start Game Enabled, so you only need to generate the file again when that list changes.