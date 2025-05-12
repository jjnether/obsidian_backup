- Quest priority? - placed this one at 50

- 0 - Initial
- 5 - pc killed graverobber
- 10 - encounter start
- 11 - FIND keyword hit -- 14
- 12 - encounter end -- 15
- 13 - PC talked to Septima -- 54
- 15 - Necro 1,2 scene
- 16 - Necro 3,4 scene
- 17 - Necro 5, dog scene
- 18 - vasenarus entrance scene
- 19 - vas forcegreet
- 20 - QUESTIONS hit
- 21 - Vas pre-kill skeleton scene
- 22 - Vas attacks skeletons
- 23 - skeleton1 killed
- 24 - skeleton2 killed
- 25 - vas attack PC
- 26 - vas is killed
- 27 - vas killed skeletons, sad boi
- 55 - PC will receive letter of gratitude, with the grotto cleared out

CompleteAllObjectives()

int Property DialogueFlag Auto ; Default is 0

defaultRefOnTrigger
SCENE.start()
Debug.Notification("")


Debug.Trace("This message is written to the papyrus log file.")
Debug.Notification("This message is displayed on the HUD menu.")
Debug.MessageBox("This message is displayed in a message box.")
Debug.CenterOnCell("QASmoke")
Debug.DumpEventRegistrations(self)

```
bool ranOnce    ; a boolean control variable.  By default, it is FALSE

EVENT onActivate(ObjectReference akActionRef)
     if (ranOnce == FALSE)      ; see if we've run this loop before
          ranOnce = TRUE        ; set the control variable to TRUE
     endif
endEVENT
```

TO FIX:
- Vasenarus foolhardy - intimidate check failure