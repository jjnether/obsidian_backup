| Bethesda Tutorial Story Manager |
| --- |
| Intermediate Quest Design Series, Chapter 6 |
| [Return to Tutorial Hub](https://ck.uesp.net/wiki/Category:Tutorials "Category:Tutorials") |
| [![LeftArrow.png](https://ck.uesp.net/w/images/9/97/LeftArrow.png)](https://ck.uesp.net/wiki/Bethesda_Tutorial_Radiant_Quests "Bethesda Tutorial Radiant Quests") [Previous Tutorial](https://ck.uesp.net/wiki/Bethesda_Tutorial_Radiant_Quests "Bethesda Tutorial Radiant Quests") | [Next Tutorial](https://ck.uesp.net/wiki/Category:Tutorials "Category:Tutorials")[![RightArrow.png](https://ck.uesp.net/w/images/c/cc/RightArrow.png)](https://ck.uesp.net/wiki/Category:Tutorials "Category:Tutorials") |

## Overview\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Story_Manager&veaction=edit&section=1 "Edit section: Overview") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Story_Manager&action=edit&section=1 "Edit section: Overview")\]

This chapter will explain the story manager and how it can be used to create new responsive content on the fly in an event-driven fashion.

The reader will learn:

-   What the story manager is.
-   The idea behind how it works.
-   Nothing else -- there's no good way to make our existing tutorial content into something initiated by the story manager, so it's here that we're going to to leave the intrepid modder to explore.

## Nodes On Top of Nodes On Top of Nodes On Top Of\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Story_Manager&veaction=edit&section=2 "Edit section: Nodes On Top of Nodes On Top of Nodes On Top Of") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Story_Manager&action=edit&section=2 "Edit section: Nodes On Top of Nodes On Top of Nodes On Top Of")\]

In the Object Window, under Character, navigate to the "SM Event Node" object type.

[![](https://ck.uesp.net/w/images/c/c9/SMEventNodes.png)](https://ck.uesp.net/wiki/File:SMEventNodes.png)

Can **you** spot the typo?!

What you're looking at is the root set of events that can autonomously kick off radiant quests. They are fairly self-explanatory and very player-centric. Double click on the "Kill Actor Event" and try not to get scared.

[![KillActorEvent.png](https://ck.uesp.net/w/images/e/e8/KillActorEvent.png)](https://ck.uesp.net/wiki/File:KillActorEvent.png)

Ok, nothing too strange so far. Double-click where it says "Stacked Event Node: Kill Actor Event," start to behold the madness, and I'll explain.

[![KillActorEventExpanded.png](https://ck.uesp.net/w/images/3/39/KillActorEventExpanded.png)](https://ck.uesp.net/wiki/File:KillActorEventExpanded.png)

The story manager works on a system of nodes. Much like the package or info stacks you've already learned about, when a story manager event kicks off, it begins churning down this list from top to bottom. This is a new fold, though, because instead of just a straight up stack, we actually have a tree-like structure where each node can have its own logic that makes it valid or invalid. Click the plus-sign at the top of the tree to expand the node labeled "DA08KillFriendNode," then click on it to select it. You window should now look like this:

[![KillActorExample.png](https://ck.uesp.net/w/images/6/6d/KillActorExample.png)](https://ck.uesp.net/wiki/File:KillActorExample.png)

We're looking at the system the game uses to tell that the player has killed a friend with the Ebony Blade, as part of the post-quest activity for DA08. Note the conditions in the bottom right, and the "E" listed in the Target column. Double-click on the first condition to explore further.

[![EventDataKiller.png](https://ck.uesp.net/w/images/7/79/EventDataKiller.png)](https://ck.uesp.net/wiki/File:EventDataKiller.png)

Note that we now have the option of running this condition on "Event Data: Killer" -- this is a crucial concept. Each kind of story manager event defines its own set of event data that we can test with conditions. We're checking that the player is the one doing the killing, and that he is currently wielding the Ebony Blade.

There is so much data getting pumped through this system that it would be folly to try and explain it all here. You can explore the various events and their data in the [story manager documentation](https://ck.uesp.net/wiki/Category:Story_Manager "Category:Story Manager").

The important idea here is that this node has a quest attached to it -- if the node passes, the quest will be started. Note that not just any quest can be put into the story manager; it has to be specifically defined in its Quest Data tab as responding to an event.

[![SMQuest.png](https://ck.uesp.net/w/images/7/73/SMQuest.png)](https://ck.uesp.net/wiki/File:SMQuest.png)

The quest can then fill aliases from the event data, and thus do interesting things like respond to each event in a particular way. This is how children return the player's dropped items, how victims of theft will set bounties on the player, how mysterious benefactors will reward you for killing their enemies, etc.

## On Top of Nodes On Top of\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Story_Manager&veaction=edit&section=3 "Edit section: On Top of Nodes On Top of") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Story_Manager&action=edit&section=3 "Edit section: On Top of Nodes On Top of")\]

In addition to housing arbitrarily complicated quests, nodes can be nested to form complicated logical structures of event responses. There are two types of nodes: Branch nodes (which contain other nodes) and Quest nodes (which contain quests). Either one of these nodes can be either stacked (in which case the game churns through them from top to bottom) or random (in which case it will choose one of its child nodes randomly).

In almost all circumstances, you'll want to check the box for "Shares Event" on a node -- without this box, if a node actually manages to fire a quest, the event will not go through the rest of the tree, meaning unrelated nodes below you might not receive important notifications. So be a good Story Manager citizen, and share your events.

## That's All Folks\[[edit](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Story_Manager&veaction=edit&section=4 "Edit section: That's All Folks") | [edit source](https://ck.uesp.net/w/index.php?title=Bethesda_Tutorial_Story_Manager&action=edit&section=4 "Edit section: That's All Folks")\]

If you've completed the Quest Design Fundamentals series and the Intermediate Quest Design series, you are now armed with a solid knowledge of how to make quest and radiant content with the Creation Kit. To get Bendu into an Story Manager Node visit [here](https://ck.uesp.net/wiki/Bendu_and_S_M_Nodes "Bendu and S M Nodes"). If you're interested in exploring further, you may want to dive more into [Papyrus](https://ck.uesp.net/wiki/Bethesda_Tutorial_Papyrus_Hello_World "Bethesda Tutorial Papyrus Hello World"), our new scripting language.

Good luck out there! Please make fantastic content, and share it! We always look forward to seeing what the community creates with these tools.

<table><tbody><tr><th><b><a href="https://ck.uesp.net/wiki/CreationKit:Language_policy" title="CreationKit:Language policy">Language:</a></b></th><td><b><a>English</a></b> <span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="fr"><a href="https://ck.uesp.net/wiki/Bethesda_Tutorial_Story_Manager/fr" title="Bethesda Tutorial Story Manager/fr">français</a></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></td></tr></tbody></table>