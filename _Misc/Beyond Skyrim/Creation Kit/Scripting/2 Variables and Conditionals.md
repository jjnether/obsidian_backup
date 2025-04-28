| Bethesda Tutorial Papyrus Variables and Conditionals |
| --- |
| Scripting Series, Chapter 2 |
| [Return to Tutorial Hub](https://ck.uesp.net/wiki/Category:Tutorials "Category:Tutorials") |
| [![LeftArrow.png](https://ck.uesp.net/w/images/9/97/LeftArrow.png)](https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Hello_World "Bethesda Tutorial Papyrus Hello World") [Previous Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Hello_World "Bethesda Tutorial Papyrus Hello World") | [Next Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Introduction_to_Properties_and_Functions "Bethesda Tutorial Papyrus Introduction to Properties and Functions")[![RightArrow.png](https://ck.uesp.net/w/images/c/cc/RightArrow.png)](https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Introduction_to_Properties_and_Functions "Bethesda Tutorial Papyrus Introduction to Properties and Functions") |

## Overview\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&veaction=edit&section=1 "Edit section: Overview") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&action=edit&section=1 "Edit section: Overview")\]

This tutorial assumes you have completed the [Hello World Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Hello_World "Bethesda Tutorial Papyrus Hello World").

You will learn:

-   How to create and use variables.
-   How to create a comment to add notes to your script for future reference
-   How to ask a script running in the game for the values of its variables
-   How to use a conditional if-then-else statement to add logic to your scripting

## Variables\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&veaction=edit&section=2 "Edit section: Variables") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&action=edit&section=2 "Edit section: Variables")\]

You can think of a variable like a container for information or objects. You can set them, you can increment and decrement numeric values, and you can retrieve their contents at a later date.

In this case we are going to give the script we wrote in the [Hello World Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Hello_World "Bethesda Tutorial Papyrus Hello World") a variable we will use to count the number of times the player activated it, and do something different each time.

Reopen the pillar's Reference window, and right-click on the HelloWorldScript on the Script tab. Select "Edit Source", which will bring up the script editing window.

Your script should look something like this:

```
 Scriptname HelloWorldScript extends ObjectReference  
 {This is my very first script!}

 Event OnActivate(ObjectReference akActionRef)
    Debug.MessageBox("Hello, World!")
 endEvent
```

Okay, let's add a variable. Add this line just _above_ the "Event OnActivate" line:

```
 int count  ;stores the number of times this object has been activated
```

-   **int** count ;stores the number... - **int** defines the type of variable. In this case an "**Int**eger," a positive or negative number without a decimal point.
-   int **count** ;stores the number... - **count** is the name we are giving the variable so we can refer to it later.
-   int count **;stores the number...** - anything after a semi-colon (**;**) is treated as a _comment._ That means NOT something that the script should care about, just something for humans looking at your script to be able to read to help understand what you are doing.

Okay, now let's add the line that will do the counting. Between the line "Event OnActivate..." and the line "Debug.MessageBox..." add the following:

Here we are saying, take whatever value is in the variable named "count" add 1 to it, and then take that value and store it back in the "count" variable. In other words, the variable on the left of the equals sign (=) should now be set to the value of the equation on the right side of the equals sign (=).

## Looking at a script's variables at run time\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&veaction=edit&section=3 "Edit section: Looking at a script's variables at run time") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&action=edit&section=3 "Edit section: Looking at a script's variables at run time")\]

Make sure the game isn't currently running. Save the script. Make sure you hit "OK" on the reference form to close it. Then hit the save button on the tool bar to save your plugin.

Start up the game and move to the activator. (Reminder: open the console with the tilde (~) key, and type:)

```
COC MolagBalVoiceCell

```

First we need to check out the value of our "count" variable, which should be 0 before we do anything.

Pull down the console (~) and while the console is "down" select the pillar (by clicking on it with the mouse) so that you see "'WETempActivator'" and a number in parentheses at the top.

Now type this into the console:

```
ShowVars

```

Now you should see the following in the console:

```
--- Papyrus ---------------------
HelloWorldScript:
     Script state = ""
     count = 0

```

You can see that it is reporting that the "count" variable is 0.

Close the console (~) and activate the pillar three times (in other words, get it to display the "Hello World!" message box three times).

Now open the console and type "ShowVars" and you will see that it reports "count = 3"

Great. But so what? Well, now we can use that information in our script to display different messages based on the number of times you clicked it. Exit the game, and get back to editing the script.

## Conditional statements (if-then-else)\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&veaction=edit&section=4 "Edit section: Conditional statements (if-then-else)") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&action=edit&section=4 "Edit section: Conditional statements (if-then-else)")\]

Now we're going to add a "[conditional statement](https://ck.uesp.net/wiki/Statement_Reference#If_Statement "Statement Reference")" that will give us some logical control over what's happening inside the script. Replace the line "Debug.MessageBox("Hello, World!")" with the following

```
 if count == 1
    Debug.MessageBox("Hello, World!")
 elseif count == 2
    Debug.MessageBox("Hello, World. Again!")
 else
    Debug.MessageBox("Hello, World. Enough already!")
 endif
```

Now we can use the value in count to change the behavior of our script. In this case showing different messages. One important thing to note is the double equals sign (==). This is how you TEST for sameness. A single equals sign (=) you may remember is how you SET a variable. This can be tricky at first, and even seasoned scripters will accidentally mess up the two signs and scratch their heads when their script isn't working.

Again:

-   Single equals sign (=) means: Take the what's on the right and shove it into the variable on the left.
-   Double equals sign (==) means: Is the thing on the left the same as the thing on the right

So your script should now look like this:

```
 Scriptname HelloWorldScript extends ObjectReference  
 {This is my very first script!}

 int count  ;stores the number of times this object has been activated

 Event OnActivate(ObjectReference akActionRef)
    count = count + 1
    
    if count == 1
       Debug.MessageBox("Hello, World!")
    elseif count == 2
       Debug.MessageBox("Hello, World. Again!")
    else
       Debug.MessageBox("Hello, World. Enough already!")
    endif
 endEvent
```

Fire up the game again, coc to the cell, and activate the pillar. You should see three different messages each time you activate it!

## For more information\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&veaction=edit&section=5 "Edit section: For more information") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Papyrus_Variables_and_Conditionals&action=edit&section=5 "Edit section: For more information")\]

-   For more information about the types of simple variables you can use (like "int" - these are called Literals), see [Literals Reference](https://ck.uesp.net/wiki/Literals_Reference "Literals Reference")
-   For more information about operators (=, +=. etc.), see... [Operator Reference](https://ck.uesp.net/wiki/Operator_Reference "Operator Reference")
-   For more information about statements like if-then-else, see [Statement Reference](https://ck.uesp.net/wiki/Statement_Reference "Statement Reference")

<table><tbody><tr><th><b><a href="https://ck.uesp.net/wiki/CreationKit:Language_policy" title="CreationKit:Language policy">Language:</a></b></th><td><b><a>English</a></b> <span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="fr"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Variables_and_Conditionals/fr" title="Bethesda Tutorial Papyrus Variables and Conditionals/fr">français</a></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="ja"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Variables_and_Conditionals/ja" title="Bethesda Tutorial Papyrus Variables and Conditionals/ja">日本語</a></span><span></span>&nbsp;• <span lang="ko"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Variables_and_Conditionals/ko" title="Bethesda Tutorial Papyrus Variables and Conditionals/ko">한국어</a></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="pl"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Variables_and_Conditionals/pl" title="Bethesda Tutorial Papyrus Variables and Conditionals/pl">polski</a></span><span></span><span></span><span></span>&nbsp;• <span lang="ru"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Variables_and_Conditionals/ru" title="Bethesda Tutorial Papyrus Variables and Conditionals/ru">русский</a></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></td></tr></tbody></table>