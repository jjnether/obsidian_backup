- Use `Actor Property PlayerRef Auto` instead of `Game.GetPlayer()`
- Use `Event OnInit()` for when something loads
- `tmm 1` to Toggle map markers
- `sgtm <value>`  to set timescale
- `tdetect` to toggle AI detection
- place `Stop()` at the end of a quest to stop the scripts from running
- utility wait scripts should never be used in quest stages if possible. Use the `BSKDefaultSetStageAfterDelay` script instead
- For calling functions in other scripts, you typecast:
	- Courier script example:
		- With the courier there was a courier quest using the script, so we added that as a property (quest)
		- Then, we typecast: `(CYRWICourier as CYRWICourierScript).AddAliasToContainer(Alias_NoteAlias)`
			- “Treat this quest (`CYRWICourier`) as if it’s running a script named `CYRWICourierScript`.”
	- BSKDefaultSetStageAfterDelay example:
		- This is only a script with no quest associated
		- For our quest, we have to add the script (scripts tab, auto-fill)
		- Then in a fragment, we can do: `(GetOwningQuest() as BSKDefaultSetStageAfterDelay).SetStageAfterGameTimeDelay(55,72)`
			- “Treat this quest (`GetOwningQuest()`) as if it’s running a script named `BSKDefaultSetStageAfterDelay`.”
- For starting combat:
```
CYRdunRenrijraKrinBanditFaction.SetEnemy(PlayerFaction)
Alias_Renrijra.GetActorRef().StartCombat(PlayerRef)
```
- Speech check: `player.setav speechcraft 100`


```
Debug.Trace("This message is written to the papyrus log file.")
Debug.Notification("This message is displayed on the HUD menu.")
Debug.MessageBox("This message is displayed in a message box.")
Debug.CenterOnCell("QASmoke")
Debug.DumpEventRegistrations(self)
```