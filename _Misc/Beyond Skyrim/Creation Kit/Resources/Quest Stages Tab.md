Setting a quest stage (see [SetStage](https://ck.uesp.net/wiki/SetCurrentStageID_-_Quest "SetCurrentStageID - Quest")) starts the quest (if it is not currently running) and evaluates the conditions on each of the stage items. Each stage item whose conditions evaluate to true runs its result script.

[![QuestStagesWindow.png](https://ck.uesp.net/w/images/thumb/d/d2/QuestStagesWindow.png/900px-QuestStagesWindow.png)](https://ck.uesp.net/wiki/File:QuestStagesWindow.png)

## Quest Stage:

-   **Index:** Each stage has an index number from 0 to 65535.
-   **Start Up Stage:** If checked, this stage will be run each time the quest starts. (even if the quest was started by calling SetStage on a different stage)
-   **Shut Down Stage:** If checked, this stage will be run each time the quest stops.
-   **Keep Instance Data From Here On:** This checkbox was introduced with version 1.5.24.0 of the Creation Kit. It preserves text replacement data across save games.
-   **Quest Stage Items:** Each stage can have 1 or more "stage items", which are used to run result scripts. Multiple stage items are often conditionalized so that only one actually runs when a stage is set.

## Quest Stage Items:

When a quest stage is set using the [SetStage](https://ck.uesp.net/wiki/SetStage "SetStage") script command, each quest stage item may be applied: if it passes the specified conditions, the Result Script is run. A maximum of 255 quest stage item per quest stage is acceptable.

-   **Log Entry:** If a stage item has log entry text, that text becomes the quest summary in the player's quest list. Only the most recent log entry is displayed to the player.
-   **Result Script:** These script commands are run when the stage item is applied. See [Papyrus](https://ck.uesp.net/wiki/Category:Papyrus "Category:Papyrus") for full information on writing scripts.
-   **[Conditions](https://ck.uesp.net/wiki/Category:Conditions "Category:Conditions"):** The conditions must be true for the quest stage item to be applied. Note that most reference functions are invalid when attached to a quest stage, since the stage is not a reference. Note also that "Run on Target" is invalid for conditions attached to quest stages. When setting a variable in a script as a condition, the variable must be changed before SetStage is called.
    -   _Note: The script fragments will be run for all entries where the conditions pass. Make sure to ensure quest stages are mutually exclusive!_
-   **Complete Quest:** If this box is checked, setting this stage will trigger the "Quest Completed" message, and move the quest from the active to completed portions of the player's quest list. Note that a completed quest can still be running.
-   **Fail Quest:** The same as Complete Quest, but triggers the "Quest Failed" message.
-   **Next Quest:** This dropdown is currently not used in the game code.