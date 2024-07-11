Using AE version (1.6.640.0)

**Have BethINI and SSEEdit in MO2 folder (use BethINI for launch options, then SSEEdit as needed)**

- se-heartlandsLOD (download from discord link)
- CYRSynthVoices (download from discord link)
- Better Jumping SE
- SkyUI
- Address Library for SKSE Plugins
- UIExtensions
- AddItemMenu - Ultimate Mod Explorer
- AddItemMenu - NG
- ConsolePlusPlus
- Display Enemy Level
- powerofthree's Tweaks
- Console Commands Extender
- HelpExtender
- More Informative Console
- Fuz Ro D-oh - Silent Voice
- Crash Logger SSE AE VR - PDB support
- No More Creation Club News ANNIVERSARY EDITION
- Immersive Loading Icon
- se-assets (download from github sync)
- se-heartlands (download from github sync)

For Github Sync:
- Install GitHub for desktop
- Clone a repository from the Internet
- Select URL, and enter the following for each repository:
	- https://gitlab.beyondskyrim.org/beyond-skyrim/bs-assets/se-assets.git
	- https://gitlab.beyondskyrim.org/beyond-skyrim/heartlands/se-heartlands.git
- For local path, place each repository in its own folder that you'll reference for MO2

For downgrading to 1.6.640 (from 1.6.1130):
**Some were having issues with the normal downgrader on nexus, so these are the steps to do it manually**

- Press Win+R and enter steam://open/console
- Go into Steam, you should see a console tab at the top
- Enter these one at a time
	- download_depot 489830 489831 3660787314279169352
	- download_depot 489830 489832 2756691988703496654
	- download_depot 489830 489833 5291801952219815735
- Navigate to Steam\steamapps\content\app_489830 and copy the contents of the three depots into your Skyrim folder

For stopping the game from updating:
- right click the game in your steam library, go to updates, and select "only update this game when I launch it"
	- this will make it so it only updates when you launch from steam (can still launch with skse)
- For a more foolproof solution, navigate to steamapps folder, then find appmanifest_489830.acf and mark it as read-only in properties
	- Undo this if you want to update
	
NOTE: Be sure to delete _ResourcePack.esl if you downgrade to 1.6.640. This was added in 1.6.1130 for creation kit stuff