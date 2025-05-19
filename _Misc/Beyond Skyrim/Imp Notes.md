- Use `Actor Property PlayerRef Auto` instead of `Game.GetPlayer()`
- Use `Event OnInit()` for when something loads
- `tmm 1` to Toggle map markers
- `ShowRaceMenu` to bring up player configuration
	- `spf <FileName>` to save face data
- `tfc` to toggle free-flying camera
- `sgtm <value>`  to set timescale
- `tdetect` to toggle AI detection
- `player.moveto <NPCrefID>`
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
- Ensure leveled actor min level (stats -> leveling data -> calc min) is at least 1
- You want to have 5 - 10 stages between so you can later add intermediate stages if necessary. For any large update in the quest, start at a new step of 100. So 100 would be the next phase of a quest and 200 the one after that.

---

- To remove masters from a plugin, ensure there aren't any used references, then right click and hit `Clean Masters`
- To add masters, right click and hit `Add Masters`
	- All plugins should have only the following masters in this order:
		- Skyrim.esm
		- Update.esm
		- Dawnguard.esm
		- HearthFires.esm
		- Dragonborn.esm
		- BSAssets.esm
		- BSHeartlands.esm

## Merging Plugin into its Master
- Note that when merging two unrelated plugins, one will have to be added as a master to the other first

**Injecting Forms**
1. Load up xEdit with your plugin,
2. Right click your plugin and select "Inject Forms into Master",
3. Select the master plugin,
4. Click "No" when you are prompted if you want to try and preserve ObjectIDs (Warning, this mean the FormID of copied records can change. When you reference the FormID in a script for some reason, this has to be changed),
5. Click yes for further prompts and let the script run to the end,
6. Now the new forms in your records have been injected into the master,

**Copying Edits to the Master**
1. Select the record groups of your plugin,
2. Right click and select "Deep Copy as override (with overwriting) into",
3. Select the master plugin,
4. When prompted to confirm the overwrite, click Yes to All