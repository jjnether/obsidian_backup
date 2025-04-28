Infos represent one or more lines of dialogue to be spoken by an NPC.

## The Info Form

[![](https://ck.uesp.net/w/images/thumb/6/62/ScriptedDialogue.png/220px-ScriptedDialogue.png)](https://ck.uesp.net/wiki/File:ScriptedDialogue.png)

-   **Topic Text:** The Topic Text inherited from the Info's [Topic](https://ck.uesp.net/wiki/Topic "Topic"), if any.
-   **Prompt:** If left blank, the prompt leading to this Info will be the [Topic's](https://ck.uesp.net/wiki/Topic "Topic") **Topic Text**. If filled in, this text will be used instead.
-   **Requires Post-Processing:** An export flag that indicates whether these responses will need additional post-processing. Required when talking to a non-NPC speaker (ex:. Augur of Dunlain). Speaker type also must be defined. Selecting this flag will narrow down the voice type to that defined speaker, otherwise it loads for all voice types.
-   **Speaker:** Optionally, you can select an NPC. If selected, the dialogue will be treated as though the selected NPC is the one saying it. This can be used, for example, to make an XMarker or other object speak with an NPC's voice. This will also control the voice type of the dialogue, based on the voice type of the selected NPC.
-   **Share Response Data From Info:** Select a [SharedInfo](https://ck.uesp.net/wiki/SharedInfo "SharedInfo") ID to acquire the response lines from that Info. This allows you to reuse the same lines in multiple places.
    -   The **Filter** box, immediately above the dropdown, filters the [SharedInfo](https://ck.uesp.net/wiki/SharedInfo "SharedInfo") IDs by the text you specify.
    -   The **...** box, immediately to the right, will open the selected [SharedInfo](https://ck.uesp.net/wiki/SharedInfo "SharedInfo") form.
-   **[Responses](https://ck.uesp.net/wiki/Topic_Info#The_Response_Form "Topic Info"):** The list of Responses (individual, sequential lines) that the NPC will say.
-   **Flags:**
    -   **Has LIP File:** Whether the game should expect a lip-data file for this line. Should usually be checked for [Actors](https://ck.uesp.net/wiki/Category:Actor "Category:Actor") and left unchecked for [TalkingActivators](https://ck.uesp.net/wiki/TalkingActivator "TalkingActivator").
    -   **On Activator:** Not used.
    -   **Say Once:** If checked, this Info can only be said once by any given [Actor](https://ck.uesp.net/wiki/Category:Actor "Category:Actor"). Once spoken, that actor will never say it again. However, a different actor that qualifies may say it.
        -   Either by design or due to an engine issue, the "Say Once" flag for dialogue in quests not marked as "Start Game Enabled" in the Quest Data tab will be reset after exiting Skyrim. Make sure to use script properties as flag substitutes for critical dialogue that should not be repeated.
    -   **Goodbye:** If checked, when this Info is completed, the actor leaves dialogue.
    -   **Force Subtitle:** If checked, the subtitle for this line will always be displayed, regardless of the player character's distance from the speaker.
    -   **Random:** If a Random Info qualifies, it isn't said immediately. Instead, the Info is put onto a stack. If the next Info is also Random, it's put on the stack. The stack keeps building until an Info that is not marked Random is found, or an info marked Random End is found. The final Info is then added to the stack, and one of the Infos is selected randomly.
    -   **Can Move While Greeting:** If checked, if this Info is a [Hello](https://ck.uesp.net/wiki/Misc_Tab "Misc Tab"), the [Actor](https://ck.uesp.net/wiki/Category:Actor "Category:Actor") can continue to move while speaking the line. Has no effect on any other line.
    -   **Random End:** Used to mark the end of a set of Random Infos. Technically, Random End is only necessary if the next qualifying info is also Random. However, it's good practice to end all Random Info sets with a Random End. In order for Random End to function properly, the info must have both Random _and_ Random End ticked.
    -   **Spends Favor Points:** Not used.
    -   **Favor Level:** Not used.
    -   **Audio Output Override:** Allows you to select an Audio Output Override. The most common use of this feature is to select a different audio falloff radius (for example, SOMDialogue3D8000), which will allow the dialogue to be audible at a much larger radius than usual.
    -   **Hours Until Reset:** After this line is spoken, the speaker will not say it again until the specified time has elapsed.
-   **[Conditions](https://ck.uesp.net/wiki/Category:Condition_Functions "Category:Condition Functions"):** The conditions that must be satisfied before this line will be spoken.
-   **Link To:** The Topic(s) that can follow this Info. When this Info is finished:
    -   If there are no Topics in this list, or none of the Topics have a valid Info, the Actor's top-level [Topic List](https://ck.uesp.net/wiki/Topic_List "Topic List") will be displayed.
    -   If one or more Topics with valid Infos in this list, a [Choice List](https://ck.uesp.net/wiki/Choice_List "Choice List") will be presented, allowing the player to select the next Info.
    -   If **Invisible Continue** is checked, only one Topic may be placed in this list. When this Info is finished, the next Info will begin automatically; no player prompt will be displayed.
    -   If **Walk Away** is checked, the dropdown becomes enabled, allowing you to select one of the Topics from the list above. If the player backs out of this Info's [Choice List](https://ck.uesp.net/wiki/Choice_List "Choice List"), the Walk Away Topic will be spoken as dialogue ends.
    -   If **Walk Away Invisible in Menu** is checked, the Walk Away Topic will not appear in the [Choice List](https://ck.uesp.net/wiki/Choice_List "Choice List").
-   **Scripts:**
    -   **Begin Script:** This script runs when the Info is played, when the Actor starts saying the line.
    -   **End Script:** This script runs when the Info is finished, when the Actor finishes speaking. In practice, it may take a second or two after dialogue has ended for this script to trigger.
    -   **Script Add/Remove/Properties:** Allows you to add, remove, or edit the properties on any [Papyrus](https://ck.uesp.net/wiki/Category:Papyrus "Category:Papyrus") scripts attached to this Info. See [Scripts](https://ck.uesp.net/wiki/Scripts "Scripts") for more details on the user interface.

## The Response Form

[![](https://ck.uesp.net/w/images/thumb/4/47/FO4_CK_Edit_Response_Window.png/220px-FO4_CK_Edit_Response_Window.png)](https://ck.uesp.net/wiki/File:FO4_CK_Edit_Response_Window.png)

The **Response Form** includes all the data related to a single line of dialogue.

-   **Response Text:** The text of the line. This is included in the export, and appears as the line's subtitle in game.
-   **Script Notes:** A comment field that is included in the export. Does not appear in game.
-   **Edits:** A comment field that is not included in the export. Rarely used.
-   **Idle Animations:** Animations performed during the dialogue.
    -   **Speaker:** The animation the speaker will perform during the line.
    -   **Listener:** The animation the listener will perform during the line.
    -   **Use Emotion Animation:** If checked, the dialogue system may choose to use an animation based on the Emotion and Emotion Value, below.
    -   **Emotion Type:** The type of emotion the line is meant to convey. This is included in the export, and used to determine what Facial or Emotion Animations should accompany the line.
    -   **Emotion Value:** The strength of the emotion on a scale of 0-100, with 100 being the strongest. This is included in the export, and used to determine what Facial or Emotion Animations should accompany the line.
-   **Voice Filename:** The name of the audio file associated with the line.
-   **Sound:** Select a sound object. This will play _instead of_ any voice that's also attached to the info.
-   **[Voicetype List](https://ck.uesp.net/wiki/Voicetype "Voicetype"):** The list of [Voicetypes](https://ck.uesp.net/wiki/Voicetypes "Voicetypes") that qualify for the line based on the Info's conditions. This list cannot be edited directly- if there are more or fewer Voicetypes listed here than you expected, you may need to correct the conditions on the Topic Info.
-   **View Valid NPCs for this Voice Type:** Displays a complete list of NPCs who can qualify for this line based on its Voicetypes and conditions.
-   **Record:** Allows you to record this line of dialogue.
-   **Preview:** Plays the most recently recorded line of dialogue.
    -   If you want to play the line of dialogue associated with this response, double-click on any of the Voicetypes in the list above.
-   **Save:** Saves the recorded line.
-   **Configure:** Brings up the Select Audio Capture Device and Select Audio Format windows.
-   **Generate Lip File:** Once a line of dialogue has been recorded, press this button to generate a Lip File for the line.
    -   **From WAV:** Synchronizes lip animation to .wav audio.
    -   **From LTF:** Use a lip animation created by hand (an LTF file).