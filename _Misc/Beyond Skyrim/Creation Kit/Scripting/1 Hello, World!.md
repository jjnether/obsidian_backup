## Overview

This tutorial introduces the basics of Papyrus, the Creation Kit's scripting language.

You will learn:

-   How to create a new script and attach it to an object.
-   How to get your script to respond to an event.

## Creating a Script

The first thing we're going to do is to create a new script and attach it to an object in the world. Run the Creation Kit and load up a test cell of your choice. I'll be using MolagBalVoiceCell simply because it's a nice empty cell without any clutter to distract us.

Let's put an object in the cell - use **WETempActivator** from the Activator list. It's a simple glowing pillar that we used as a temporary object during development.

[![Papyrus Tutorial1 Activator.jpg](https://ck.uesp.net/w/images/thumb/4/43/Papyrus_Tutorial1_Activator.jpg/300px-Papyrus_Tutorial1_Activator.jpg)](https://ck.uesp.net/wiki/File:Papyrus_Tutorial1_Activator.jpg)

Double-click on the object to open the Reference window. Switch to the Scripts tab. This is where you can add scripts to any object in the game.

[![Papyrus Tutorial1 Ref.jpg](https://ck.uesp.net/w/images/8/8d/Papyrus_Tutorial1_Ref.jpg)](https://ck.uesp.net/wiki/File:Papyrus_Tutorial1_Ref.jpg)

  
Click the Add button to bring up the "Add script" window.

[![Papyrus Tutorial1 AddScript.jpg](https://ck.uesp.net/w/images/8/80/Papyrus_Tutorial1_AddScript.jpg)](https://ck.uesp.net/wiki/File:Papyrus_Tutorial1_AddScript.jpg)

Double-click "\[New Script\]" at the top of the list to create your new script. Change the Name field to "HelloWorldScript" (this will be the script's name), and hit "OK".

<table><tbody><tr><td><a href="https://ck.uesp.net/wiki/File:Achtung.png"><img alt="Achtung.png" src="https://ck.uesp.net/w/images/f/f0/Achtung.png" decoding="async" width="32" height="32"></a></td><td>If you get this error: "The extends script does not exist, please pick one that does" This seems to be due to the new update it has removed the loose papyrus source files and placed them in a .rar file ("scripts.rar") in the base Data folder of the Skyrim installation. You'll have to extract the rar back into their original folder again for CK to work correctly.</td></tr></tbody></table>

[![Papyrus Tutorial1 NewScript.jpg](https://ck.uesp.net/w/images/7/77/Papyrus_Tutorial1_NewScript.jpg)](https://ck.uesp.net/wiki/File:Papyrus_Tutorial1_NewScript.jpg)

Please Note: the field labelled "Documentation String". Your script does not go here! The 'Documentation String' is a tool-tip primarily used to provide some quick information on the nature of the script. What it does, what objects it may apply to etc. You'll now see that your new script has been added to the pillar's script list:

[![Papyrus Tutorial1 Ref WithScript.jpg](https://ck.uesp.net/w/images/f/f1/Papyrus_Tutorial1_Ref_WithScript.jpg)](https://ck.uesp.net/wiki/File:Papyrus_Tutorial1_Ref_WithScript.jpg)

Hit "OK" to save the changes to the pillar reference. Congratulations! You've just created your first script and attached it to something in the world.

## Adding an Event

Of course, your script doesn't do anything yet - it's just an empty shell waiting to be given something to do.

Because this object is an Activator, it can respond to being clicked on ("activated") by the player. So let's tell our script to show us a message when the player clicks on the pillar.

Reopen the pillar's Reference window, and right-click on the HelloWorldScript on the Script tab. Select "Edit Source", which will bring up the script editing window.

Now we need to tell the script to respond to being activated, which means we need to add the [[ObjectReference Script#^e1a952|OnActivate event]] to our script. Add the following lines to your script:

```
 Event OnActivate(ObjectReference akActionRef)

 endEvent
```

For now, don't worry about how we knew what syntax to use here when we defined the OnActivate event - we'll go into more detail on that in a later tutorial. For now, let's just see if we can get our script to do something in the game.

At this point, our script is ready to respond to the OnActivate event, so let's tell it to show a simple message box:

```
 Event OnActivate(ObjectReference akActionRef)
    Debug.MessageBox("Hello, World!")
 endEvent
```

To explain this last step a bit more, the syntax of the line breaks down as follows:

**Debug.**MessageBox("Hello, World!"): This is telling the script that we're calling a function on a different script (in this case the special default [[Debug Script|Debug script object]].

Debug.**MessageBox**("Hello, World!"): [[Debug Script#^29ea68|MessageBox]] is a function that pops up a message box.

Debug.MessageBox**("Hello, World!")**: The parentheses show that we're calling a function; whatever's inside the parentheses is the data that we're passing to the function (in this case, the text that we want to be displayed in the message box).

Save and compile your script by selecting "Save" from the File menu on the script editing window (or CTRL-S). If you typed everything correctly, you should see this:

[![Papyrus Tutorial1 CompiledScript.jpg](https://ck.uesp.net/w/images/9/91/Papyrus_Tutorial1_CompiledScript.jpg)](https://ck.uesp.net/wiki/File:Papyrus_Tutorial1_CompiledScript.jpg)

## "Hello, World"

Now to go into the game and try it out. (Make sure to [[Getting Started#Creating and saving plugins|save your plugin]], and set up the game to load it first.)

Once you're in the game, hit ~ to bring up the console. Type:

```
coc MolagBalVoiceCell

```

to move to the cell. Walk over to the pillar and activate it. You should see your new message box:

[![Papyrus Tutorial1 HelloWorld.jpg](https://ck.uesp.net/w/images/thumb/2/2d/Papyrus_Tutorial1_HelloWorld.jpg/800px-Papyrus_Tutorial1_HelloWorld.jpg)](https://ck.uesp.net/wiki/File:Papyrus_Tutorial1_HelloWorld.jpg)

That's it. You've made an object that can respond to the player's actions!

Next, you can learn [[2 Variables and Conditionals|how to use variables and conditional statements]] to make your script a bit more sophisticated.