Message Objects are used to create localizable text strings. Messages are used for:

-   **Message Boxes**, such as the message boxes that appear when you interact with a Standing Stone (doomThiefMSG)
-   **Notifications**, such as the Rested message (RestedMessage)
-   **Text Overrides**, used for overriding names on objects like Doors (dunMarkarthWizardBalconyDoorLoc) and Reference Aliases (TG09Name).
-   **Help Text**, such as the text that appears in the Help Menu and in in-game tutorial messages (HelpAlchemyLong).

Messages can be displayed with the [Message Script's](https://ck.uesp.net/wiki/Message_Script "Message Script") [Show](https://ck.uesp.net/wiki/Show_-_Message "Show - Message") function.

## Message Dialog

[![](https://ck.uesp.net/w/images/thumb/f/f7/MessageDialog.jpg/300px-MessageDialog.jpg)](https://ck.uesp.net/wiki/File:MessageDialog.jpg)

Message Window in the Creation Kit editor

-   **ID:** The ID of the message.
-   **Icon:** Not used.
-   **Owner Quest:** Optionally, the [Quest](https://ck.uesp.net/wiki/Category:Quest "Category:Quest") that owns this message, if it contains [Text Replacement](https://ck.uesp.net/wiki/Text_Replacement "Text Replacement") formatting that needs to extract data from the quest.
-   **Title:** The title of the message. For _Text Overrides_, fill in the Title and leave the Message Text blank.
-   **Message Text:** The body text of the message. For _Notifications_, fill in the Message Text and leave the Title blank.
-   **Message Box:** When checked, the message is displayed as a dialog box that pauses the game and waits for a response. Otherwise the message will be briefly displayed at the top left of the screen.
-   **Auto-display:** Not used.
-   **Display Time:** The number of seconds the message will be displayed. Only applicable when the message box option is unchecked.
-   **Menu Buttons:** A list of buttons on the message form. Right click to create a new one.
-   **Item Text:** The text on the selected button.
-   **Item Conditions:** A list of [conditions](https://ck.uesp.net/wiki/Category:Condition_Functions "Category:Condition Functions") that must be satisfied for the selected button to show.

## Notes
-   Message titles have a character limit of 259.
-   Message boxes have a 1023 character limit, any longer and Skyrim will crash to desktop when attempting to display the message. This limit is based on the number of characters entered into the editor, including numerical formatting characters and quest text substitution tags.
-   The display time is ignored by the game. Messages remain on the screen for the same time as Debug.Notification messages, regardless of the value set.

<table><tbody><tr><th><b><a href="https://ck.uesp.net/wiki/CreationKit:Language_policy" title="CreationKit:Language policy">Language:</a></b></th><td><b><a>English</a></b> <span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>&nbsp;• <span lang="uk"><a href="https://ck.uesp.net/wiki/Message/uk" title="Message/uk">українська</a></span><span></span><span></span><span></span><span></span><span></span><span></span></td></tr></tbody></table>