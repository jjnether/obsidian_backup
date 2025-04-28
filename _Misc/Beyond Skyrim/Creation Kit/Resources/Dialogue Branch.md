Dialogue Branches are data structures that group [Topics](https://ck.uesp.net/wiki/Topic "Topic") together. They allow the dialogue system to:

-   Organize and distinguish between dialogue trees. In essence, each Branch represents a 'thread' of the conversation.
-   Account for the fact that the player can enter and exit dialogue at any time, providing a means for the player to reenter an interrupted conversation.

## Dialogue Branch Data

A Dialogue Branch has the following data:

-   **EditorID:** The form's Editor ID.
-   **Starting Topic:** The Starting Topic serves as the automatic "entry point" for the dialogue in the branch. For Top-Level Branches, the Starting Topic's prompt is what will appear in the topic list. For Blocking Branches, its [Info](https://ck.uesp.net/wiki/Topic_Info "Topic Info") will be used by the NPC as a greeting. All Branches must contain exactly one Starting Topic; if a branch has multiple topics, any of them can be selected as the Starting Topic.
-   **Branch Type:**
    -   **Normal:** Normal Branches never appear in the [topic list](https://ck.uesp.net/wiki/Topic_list "Topic list"). They only appear in the menu if accessed indirectly (through a [choice list](https://ck.uesp.net/wiki/Choice_list "Choice list"), or from another Branch), or if they are used in a [ForceGreet Package](https://ck.uesp.net/wiki/ForceGreet_(Package_Template) "ForceGreet (Package Template)").
    -   **Top-Level:** The Starting Topic of a Top-Level Branch will appear in the NPC's initial [topic list](https://ck.uesp.net/wiki/Topic_list "Topic list") (assuming there is a valid info in the Starting Topic for that NPC).
    -   **Blocking:** The Starting Topic of a Blocking Branch preempts all other dialogue if it contains a valid info. See below.
-   **Exclusive:** Once entered, the Branch effectively becomes a Blocking Branch until exited. See below.

## Blocking Branches

Blocking Branches are used to override an NPC's normal topic list. When an NPC has a valid info in a Blocking Branch's Starting Topic, the NPC will use that info as his greeting (and Hello, unless the [info](https://ck.uesp.net/wiki/Topic_Info "Topic Info") is conditioned only to be valid in the dialogue menu, such as with [IsInDialogueWithPlayer](https://ck.uesp.net/wiki/IsInDialogueWithPlayer "IsInDialogueWithPlayer")).

When the player speaks to an NPC with a valid Blocking Branch:

-   If the [info](https://ck.uesp.net/wiki/Topic_Info "Topic Info") has a choice list, those choices will be displayed instead of the normal topic list.
-   If the [info](https://ck.uesp.net/wiki/Topic_Info "Topic Info") is marked as a "Force Goodbye", the dialogue menu will not come up, and the NPC will simply say the info from the branch's Starting Topic.
-   If the [info](https://ck.uesp.net/wiki/Topic_Info "Topic Info") has no choice list and is NOT a "Force Goodbye", the dialogue menu will be displayed with a single topic - the prompt on the branch's Starting Topic.

If an NPC has multiple Blocking Branches with valid starting topics, the branch from the quest with the highest priority will "win". When there are multiple valid blocking branches from the same quest, one of them will be "win", but results may be unpredictable. This is usually an error.

## Exclusive Branches

These are similar to Blocking Topics, but they take over the topic list once you "enter" the branch (by the NPC saying a line from any of the Exclusive branch's topics).

Once the NPC is marked as "in" the Exclusive Branch, he will act as if that branch is a valid Blocking branch (see above) until he says a line of dialogue from a different (non-Exclusive) branch. For example, if you exit dialogue and then speak to the NPC again, his greeting will be the Exclusive branch's Starting Topic. This can result in blocking all dialogue if there is no topic in the Exclusive Branch that the NPC can speak.