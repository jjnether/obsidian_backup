A [Quest's](https://ck.uesp.net/wiki/Category:Quest "Category:Quest") Player Dialogue Tab contains all of the quest-specific or unique [Dialogue Branches](https://ck.uesp.net/wiki/Dialogue_Branch "Dialogue Branch"), [Topics](https://ck.uesp.net/wiki/Topic "Topic"), and [Infos](https://ck.uesp.net/wiki/Topic_Info "Topic Info") associated with the quest. The dialogue in this tab will play as a part of player-initiated or [Forcegreet](https://ck.uesp.net/w/index.php?title=Forcegreet_Packages&action=edit&redlink=1 "Forcegreet Packages (page does not exist)") dialogue; it will not normally be triggered by other game systems or events.

[![QuestPlayerDialogueViewsWindow.png](https://ck.uesp.net/w/images/thumb/8/8a/QuestPlayerDialogueViewsWindow.png/900px-QuestPlayerDialogueViewsWindow.png)](https://ck.uesp.net/wiki/File:QuestPlayerDialogueViewsWindow.png)

## Topic list

The **Topics** list shows the following information for each topic in the selected branch:

-   **Editor ID**
-   **Starting:** A lefthand angle bracket in this column marks the branch's starting topic. Think of the bracket as an arrow pointing to the topic's editor ID.
-   **Form ID:** This column is initially collapsed out of view.
-   **Priority**
-   **Display Text**

## Info list

The info list shows the following information for each info in the selected topic:

-   **Text:** All of the info's Responses, concatenated together with a pipe symbol.
    -   If the info is deleted, then "DELETED - " is prepended.
    -   If the info pulls its text from a SharedInfo, then "<<Shared>>" is prepended.
-   **Form ID:** This column is initially collapsed out of view.
-   **Editor ID:** This column is initially collapsed out of view.
-   **Flags**
    -   **C:** The info has any Link To topics.
    -   **E:** The info has the Random End flag set. (If "E" shows, then "R" will never show.)
    -   **F:** The info has the Spends Favor Points flag set.
    -   **G:** The info has the Goodbye flag set.
    -   **I:** The info has the On Activation flag set.
    -   **O:** If the info has a non-zero Hours Until Reset, that gets shown here, e.g. "O(0.50)".
    -   **P:** The info has its own Prompt text, overriding the topic's display text.
    -   **R:** The info has the Random flag set.
    -   **S:** The info has the Say Once flag set.
    -   **V:** The info has the Walk Away Invisible In Menu flag set.
    -   **W:** The info has the Walk Away topic flag set (even if no topic has been selected).
-   **\# Responses**
-   **Speaker NPC:** If the info has a _Subject.GetIsID_ condition, then this column shows the condition's form parameter. It doesn't display the info's "Speaker" option, because the goal is to tell you who is allowed to say the info, not whose voice will be used to say it.
    -   The column only displays the first _Subject.GetIsID_ condition in the info.
    -   The column doesn't check whether the condition has "Swap Subject and Target" enabled.
    -   If the _Subject.GetIsID_ condition requires that its result equal zero, then the column shows this as a negation, e.g. displaying "NOT Maul" for _Subject.GetIsID(Maul) == 0_.
-   **Target NPC:** If the info has a _Target.GetIsID_ condition, then this column shows the condition's form parameter.
    -   This column uses the same logic as the Speaker NPC column in how it checks and displays conditions.
-   **Is Voice Type:** If the info has a _Subject.GetIsVoiceType_ condition, then this column shows the condition's [Voicetype](https://ck.uesp.net/wiki/Voicetype "Voicetype") or [FormList](https://ck.uesp.net/wiki/FormList "FormList") parameter.
    -   This column uses the same logic as the Speaker NPC column in how it checks and displays conditions.
-   **In Faction:** If the info has a _Subject.GetInFaction_ condition, then this column shows the condition's [Faction](https://ck.uesp.net/wiki/Faction "Faction") parameter.
    -   This column uses the same logic as the Speaker NPC column in how it checks and displays conditions.
-   **Conditions:** All of the info's conditions.
-   **Has Result Script:** If the info has an "End" Papyrus fragment, then this column shows the letter "Y." Otherwise, the column is blank.