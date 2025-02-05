---For Making Server---
-download and install java 17 (https://adoptium.net/)
-make and name folder for easy access
-download multiplayer server from minecraft website to folder (or instead download paper if you want to use paper server; see below)
-open server file
-wait a bit, then exit out of it
-open eula.txt and change value to true and save
-run server file again
-open the server.properties file and configure properties as prefered for server (see server.properties section for some guidance)
---

NOTE: to transfer a world from multiplayer to singleplayer or vise versa, switch the save folders (multiplayer is 'world' folder while singleplayer is the files under saves)
	---Be sure the name of the world or save matches the name of the level-name within the server.properties file 

-----------DO NOT DO IF YOU DONT KNOW WHAT YOU ARE DOING----------
Modify the system path, enter the following command:
set path=%path%;c:\Program Files\Java\jre7\bin\ (if "c:\Program Files\Java\jre7\bin\" is your Java folder, see above).

Instead of modifying the system path, the Java folder can also be entered as part of the Java command:
"c:\Program Files\Java\jre7\bin\java" -version (again, if "c:\Program Files\Java\jre7\bin\" is your Java folder).

NOTE: when entering the path together with the Java command you need to enclose the command inside quotes, because of the space character in the path (between Program and Files). When modifying the path, the quotes are not required.
------------DO NOT DO IF YOU DONT KNOW WHAT YOU ARE DOING----------

-create a new text document and put the exact line in it: java -Xms1G -Xmx1G -jar minecraft_server.jar
-for the "minecraft_server.jar" part, put what the exact name of your server file is(not the folder, but the file name)
-to increase or decrease RAM usage, change both numbers before the G to whatever value you wish (G for gigabyte or M for megabyte) (Xms is minimum usage and Xmx is maximum)
-save and name the text document this exactly: "start-server.bat" (be sure to add the quotes in the name)(if you get a warning, click ok)
-for the first line, you may shift the other line down and type: @echo off
-for the last line, you may put: pause

Here is an example of the start-server.bat with 1 GB of RAM:

@echo off
java -Xms1024M -Xmx1024M -jar minecraft_server.1.8.exe nogui
pause

-use this batch file to start the server from now on

---creating the port for the server--
-open browser and go to www.whatismyip.com which will give you your ip address which you will need for later
-open start menu, type in cmd, and open command prompt
-type in ipconfig /all and hit enter
-find and write down theI pv4 address, subnet mask, Default Gateway, and both numbers for the DNS Servers
-open control panel then network and sharing center
-hit change adapter settings
-right-click on WIFI and hit properties
-scroll down to the option "Internet Protocal Version 4 (TCP/IPv4)"
-make sure it is checked, click it, and hit properties
-type in all the information you got from the command prompt in each line (keep numbers in case something goes wrong)
-hit ok and exit that all out
-open browser and type in for address the default gateway number
-see modem or router in household for username and password info (default is no username and password is "admin")
-go to port forwarding / port triggering (or something like that - could be applications and gaming, etc.)
-depending on your router, it will be different, but something like Advanced > Configuration > Virtual Server > Port Forwarding.
-name service (can be anything you chose), keep default type (TCP/UDP or both), type in 25565 for both the starting and ending ports (or something like that for port names)
-for the server ip address, type in the last few numbers from the ipv4 address you wrote down earlier
-hit save (or something like that)

NOTE: See section below for playing from another network without port forwardiing
---


---For Gameplay---
-obviously, run the server by opening the main server file
-to connect to it yourself, for the server address, put this exactly- localhost
-for others to connect, they must put for the server address, the exact ip address you got from whatismyip.com (be careful, these numbers are valuable)
-if others are trying to connect on the local network, they can use your local ipv4 address instead of your public address
-to make people admins, type in server command prompt: op (username)
-to stop the server, simply type in server command prompt: stop

NOTE:you may need to make exceptions for the port (25565), javaw.exe, minecraft.exe, or your server in your firewall or your antivirus firewall if it doesn't work
---


---server.properties---
NOTE: Only edit values if you know what they do

- level-name will only change the name of the world directory
- change motd to change how players see the server description
- lower view distance to help with server lag (10 is decent)
- player-idle-timeout will kick players after a certain amount of time (0 is infinity)
---


---Paper Server---
NOTE: Paper server extends and improves the Bukkit and Spigot APIs, so they are basically both included in the paper implementation

- To implement, simply download the latest paper .jar file
- Rename it to match your current server file (<name>.jar)
- Replace current .jar file and run server
---

---Gameplay Without Portforwarding (Zerotier)---
- An alternative to portforwarding is setting up a network with Zerotier and having both the host and connecting device on the network
- The host has to login online to zerotier and setup their network
- To join the network, one must download and install zerotier
- Then they need to join the network while only selecting "Allow Managed IP" using the network ID (found on the site to manage the network)
- You then have to authorize the user on the site to manage the network (user can be identified by the node ID they give you)
- They can then connect to the server by using the ip of the host pc listed on the site to manage the network
---


---Plugins---
NOTE: Plugins folder within main server directory is where mods should be placed

- CoreProtect is a good mod for rollbacks in a server
- NerfPhantoms is good to get rid of phantoms
- For Bedrock implementation, use Geyser-spigot and floodgate-bukkit plugins and see section below
---


---Bedrock Implementation---
- Download Geyser-spigot and floodgate-bukkit plugins and place in plugins folder for server
- Run server to generate files
- Find the file public-key.pem within the newly generated floodgate-bukkit folder and copy it to the newly generated Geyser-Spigot folder
- Open config.yml within the Geyser-Spigot folder and beneath remote, change auth-type to floodgate
- Ensure port 19132 is open
- Java Players will join normally
- Bedrock on PC will join using the public ipv4 address of the server and the port 19132
- For All other versions:
   - Go to network settings, then advanced settings
   - Hit DNS Settings then manual
   - For primary DNS, type in 104.238.130.180 (see https://github.com/Pugmatt/BedrockConnect for available public DNS servers)
   - For secondary DNS, type in 8.8.8.8
   - Restart device
   - In Minecraft, join any of the listed servers
   - Now connect to the server using the public ipv4 address of the server and port 19132 (port 19133 if using BedrockConnect)
   - Select Add to server list for convenience


NOTES:
- By default, bedrock player names will have "*" before their name, disallowing them to be used in console commands
   - Fix by opening config.yml within floodgate-bukkit and change username-prefix to "_" instead of "*" (can also change replace-spaces to false)
- If not portforwarding and only using server on local network, see Local BedrockConnect section for non-pc players to connect
- You can change motd1, motd2, and server-name within the geyser config.yml file for bedrock players to see specific server names
---


---Local BedrockConnect---
- Ensure server is not running
- Download and install mod0Umleitung for DNS server hosting (https://modzero.github.io/mod0Umleitung/)
- Download and unpack BedrockConnect (https://github.com/Pugmatt/BedrockConnect/releases)
- Launch the mod0Umleitung application and start the server - if you can't start the server, refer to the readme in the BedrockConnect directory to disable "DNS Client"
- Stop the server and run the run.bat file in the BedrockConnect folder
- Type in the ipv4 address you have been using
- In the DNS hosting application, hit Load Ruleset and select the newly generated bc_dns.conf file within the BedrockConnect folder
- Hit Start Server in the DNS hosting app
- Open config.yml in the Geyser-Spigot folder and beneath bedrock, change the port to 19133 (this is because the DNS host is now using port 19132)
- For non-computers to join the server, follow the directions beneath the Bedrock Imlementation section, but for the primary DNS, they must now enter the ipv4 address you typed into BedrockConnect
- To connect to the server, these players will also use this same ipv4 address along with the new geyser port we just changed, 19133

NOTE:
- Anyone using this local instance of BedrockConnect must be connected to the local network
---


---Server Datapacks---
- To apply server datapacks, simply place them in the datapacks directory within the world folder (name of your world, but not the nether or end directories)
- Vanilla tweaks has many datapacks that might be useful for a server
- Note that resource packs are different and must be installed on each separate machine, but only chanage the looks of things, so all are compatible

NOTE: If using GeyserMC to allow bedrock players to join server, some datapacks may not work properly for them (ex. graves)
---

NOTE: Use MCASelector to trim the world. Can also be useful when updating the world