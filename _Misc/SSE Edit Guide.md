- Ensure you have automation tools for TES5Edit installed (mod works for Oldrim, SE, and FO4)
- Load the plugin you want to base the mod off of, as well as its dependencies
- On the left, select the records you want to copy over to begin building the new mod
- For file type, select .esp flagged as a .esl (espfe)
- Select the records from your newly created mod that you want to batch edit, right click, and hit apply script
- Select AT - QuickDisplay and hit ok
- For the three fields, use the following (example): Record Header\FormID      EDID       DATA - Weight
- Select Export as .csv
- Exported.csv file will now be placed in the Edit Scripts folder of your SSEEdit Installation
- Edit the .csv to the state you would like, and close it
- Select the same records and apply the AT - QuickChange script
- Select Import, and place the path of the .csv you edited
- Hit Ok, and it should replace every record you edited
- Hit ctrl + s to save, then grab your new .esp from the game data folder (or overwrite directory if using MO2)
- For uploading to nexus, folder convention must be:
    `<top level folder>`
	    - `Data`
		    - `<.esp file>`
- Zip the top level folder, and that is what you upload to nexus

[Guide for script editing in SSEEdit](https://www.youtube.com/watch?v=5wMl6TY_Oqg&list=LL&index=1172)


For adding a FOMOD to your mod:
- First download FOMOD Creation Tool from FO4 nexus

[Guide](https://www.youtube.com/watch?v=rr79YmimJW0)