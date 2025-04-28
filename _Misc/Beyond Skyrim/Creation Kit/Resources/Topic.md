Topics are data structures that hold and organize [Infos](https://ck.uesp.net/wiki/Topic_Info "Topic Info").

## Topic Base Data

A Topic contains the following data:

-   **ID:** The Topic's Editor ID.
-   **Subtype:** Rarely used, a Topic's Subtype allows dialogue topics to stack across multiple quests. The available subtypes are:
    -   **Custom:** The default, each Custom topic is treated separately.
    -   **ForceGreet:** A subtype used by guards when attempting to arrest the player. Note that Topics do not need to be tagged as Forcegreets in order for you to use them in [Forcegreet Packages](https://ck.uesp.net/wiki/ForceGreet_(Package_Template) "ForceGreet (Package Template)").
    -   **Rumors:** A subtype used to create cross-quest Rumor topics. Valid TopicInfos belonging to topics with this Subtype will be combined into one stack. If the originating Topic has no Topic Text, then the game setting sTopicSubtypeTextPlayerDialogueRumors ("Heard any rumors lately?") will be displayed. If a Topic Text or Prompt does exist, then that will be displayed instead, but only when that Info is next in line, at which point it will replace the default dialogue choice. In vanilla, rumor TopicInfos have the Random flag and a 24 hour reset timer, and are either conditioned on the JobInnkeeperFaction or on specific NPCs, as well as other situational conditions.
-   **Topic Text:** Optionally, when this Topic has a qualifying Info, this prompt will be displayed in the dialogue menu. If the player selects it, the Topic's Info will play. Note that if the Info has its own prompt, the Info's prompt will override this one.
-   **Do all before repeating:** Used with [Random Infos](https://ck.uesp.net/wiki/Topic_Info "Topic Info"), when checked, the game will not repeat the same random info until all currently valid infos in the topic have been spoken.
-   **Priority:** Used to determine the sorting order for topics displayed in a [Topic List](https://ck.uesp.net/wiki/Topic_List "Topic List"). Note that this has no effect on topics used in [Choice Lists](https://ck.uesp.net/w/index.php?title=Choice_Lists&action=edit&redlink=1 "Choice Lists (page does not exist)").

## Topic Info Stack

The list of [Topic Info](https://ck.uesp.net/wiki/Topic_Info "Topic Info") attached to a Topic is an ordered list (a stack). The game evaluates a Topic by evaluating each Info in the stack, beginning at the top and working its way down. The first Info whose conditions return true is the Info the NPC will say.

When the game encounters a valid [Info](https://ck.uesp.net/wiki/Topic_Info "Topic Info") marked "Random", it begins building a list of valid random Infos. If the next Info is also Random, it's put into the list. This list continues to grow until an Info that is not marked Random is found, or an Info marked "Random End" is found. That last Info is added to the list, and then one of the Infos in the list will be selected at random.