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


Questions:
- Distance between player and enemies for scene condition?
- Default package for actors to move to certain point?
- Default script to use a trigger box to activate a scene? Or to set stage for quest?
- For unique actors, what's the easiest way to populate all the fields (faction, AI package, inventory, etc) or do you just have to manually each time?
- How to do persuade dialogue? (What is the amulet, and what is the script fragment for?)