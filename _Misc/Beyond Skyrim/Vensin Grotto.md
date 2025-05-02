- Quest priority? - placed this one at 50

- 0 - Initial
- 10 - encounter start
- 15 - FIND keyword hit
- 20 - Vasenarus is killed
	- end of quest
- 30 - Vasenarus is convinced to kill his skeletons
	- end of quest
- 40 - PC read the graverobber note
	- unlock dialogue with Septima Strabo
- 50 - PC went to septima and reported the graverobbing
- 55 - PC waited a few days and will receive letter of gratitude, with the grotto cleared out
- 60 - end of quest



CYRWICourier.SendLetterAlias(Alias_Letter)
BSKDefaultSetStageAfterDelay 
BSKDefaultSetStageOnDeath 
defaultSetStageOnDeathRefAlias


CompleteAllObjectives()
Stop()

int Property DialogueFlag Auto ; Default is 0

defaultRefOnTrigger
SCENE.start()
Debug.Notification("")


Scriptname CYRVensinGrottoVarScript extends Quest  Conditional
int Property FLAG1 Auto Conditional; flag for FIND keyword in dialogue


Utility.WaitGameTime(1.5)


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