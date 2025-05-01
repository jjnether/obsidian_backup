- Quest priority? - placed this one at 50

- 0 - Initial
- 20 - Vasenarus is killed
	- end of quest
- 30 - Vasenarus is convinced to kill his skeletons
	- end of quest
- 40 - PC read the graverobber note
	- unlock dialogue with Septima Strabo
- 50 - PC went to septima and reported the graverobbing
- 55 - PC waited a few days and will receive letter of gratitude, with the grotto cleared out
	- end of quest



CYRWICourier.SendLetterAlias(Alias_Letter)
BSKDefaultSetStageAfterDelay 
BSKDefaultSetStageOnDeath 
defaultSetStageOnDeathRefAlias


CompleteAllObjectives()
Stop()

int Property DialogueFlag Auto ; Default is 0

tdetect
defaultRefOnTrigger
SCENE.start()
Debug.Notification("")


Scriptname CYRVensinGrottoVarScript extends Quest  Conditional
int Property FLAG1 Auto Conditional; flag for FIND keyword in dialogue


Utility.WaitGameTime(1.5)