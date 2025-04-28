## Type

Topic Info fragment scripts extend [TopicInfo](https://ck.uesp.net/wiki/TopicInfo_Script_(Papyrus) "TopicInfo Script (Papyrus)").

## Run Time

Topic Info fragments are run when the topic begins, and when the topic ends.

## Special Variables

-   akSpeaker: This is the [Actor](https://ck.uesp.net/wiki/Actor_Script_(Papyrus) "Actor Script (Papyrus)") that is speaking the topic. (May be None if the speaker isn't an Actor - in which case, check akSpeakerRef)
-   akSpeakerRef: This is the [ObjectReference](https://ck.uesp.net/wiki/ObjectReference_Script_(Papyrus) "ObjectReference Script (Papyrus)") that is speaking the topic. Will be the same object as akSpeaker.

## Notes

-   To get the Target of a line of dialogue you can do this:
    
    ```
    akSpeaker.GetDialogueTarget()
    ```
    
-   Do not have any properties or variables pointing at a topic info fragment script. For memory reasons, these do not stick around and may cause odd behavior if you try to hold onto them.
-   When a topic info script is first created, it isn't possible to add properties to it. You must first close the Topic Info dialog window and then reopen it before adding properties to the script.
-   You can use GetOwningQuest() to access the current quest object. You can also cast this quest inline if you want to access specific functions from the quest -- for instance:
    
    ```
    (GetOwningQuest() as DialogueFollowerScript).AnimalFollow()
    ```