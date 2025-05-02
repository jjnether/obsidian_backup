- Create an alias for the quest chest in `CYRHoldingCell`
	- Specific reference - select the chest
- Create an alias for the note (NoteAlias)
	- Create Reference to Object - LetterName - Create In Alias_Chest
	- Script: defaultsetstageonplayeracquire (optional) - NOTE: don't use the script ending in item (we want the one that uses an alias)
		- set quest and stage to set
- Add script properties:
	- Quest - CYRWICourier
	- Book - (NoteName)
- Add in script: `(CYRWICourier as CYRWICourierScript).AddAliasToContainer(Alias_NoteAlias)`

To also have the courier deliver gold:
- Create a MiscObject property for the gold (Gold001) and auto-fill
- add to the script: `(CYRWICourier as BSKWICourierScript).SendForm(Gold001, 100)` where `100` is the amount of gold to add
	- you can substitute `Gold001, 100` with a leveled gold list, or any form for that matter
	- instead of hardcoding the `int` amount, you can make it variable (see below example)
```
int playerLevel = Game.GetPlayer().GetLevel()
int goldToGive = 25 + (playerLevel * 3) ; example formula
if (goldToGive > 200)
    goldToGive = 200
endif
```


For Troubleshooting:
`help CYRWICourier 3` - global variable showing how many letters the courier needs to deliver
`sqv CYRWICourier`