To map a network drive:
- Open file explorer and right click on My Computer
- Hit map network drive
- Change drive letter to what you want
- For folder, enter `\\<server name>\<shared folder>`  (ex. `\\Netherton_Nas\docker`)


To enable SSH on NAS, go to Control Panel>Terminal & SNMP>Terminal then Enable SSH Service and change port to 2299 (somewhat arbitrary number, just needs to be changed from default)
Use putty to SSH into the NAS with the port we previously specified:
- enter NAS username
- enter NAS password (won't see anything when typing password; can right click to paste)


linuxserver.io has lots of guides and docker containers for use

Run `id` to find PUID and PGID (use these numbers when needed for docker compose)

You will usually need to run all commands with "sudo" before the command so it has permissions (ex. sudo docker compose up -d)

To run the docker-compose.yaml file:
`docker compose up -d`

To bring down #docker services:
`docker compose down`

To update a single container:
`docker compose pull linuxserver/<image_name>`
`docker compose up -d <container_name>`

To update all containers at once:
`docker compose pull`
`docker compose up -d`

To prune old images from system:
`docker image prune`


For setting up Dynamic DNS
- Go to Control Panel>Connectivity>External Access>DDNS then Add
- For service provider, use Synology
- Set desired hostname (ex. jjnether.synology.me)
- Test Connection
- Check Get a certificate... (you can change which certificate each service uses in Control Panel>Connectivity>Security>Certificate>Settings
- Enable Heartbeat, then hit OK

For setting up a Reverse Proxy:
- Go to Control Panel>System>Login Portal>Advanced>Reverse Proxy then hit create
- Set a name
- Make source HTTPS and provide hostname (ex. jjnether.synology.me)
- Leave source port as default (ex. 443)
- Enable HSTS
- For destination, protocol should most likely be HTTPS
- Set hostname as the local IP for the destination portal (ex. 10.0.0.227)
- Set port for the destination portal (ex. 5055 - for overseerr)


To view current containers: docker ps -a

To remove a container: `docker rm <container>`

To exec into container: `docker exec -it <container name> /bin/bash`
- type exit to leave
- you can also exec in using portainer
	- will need to enable websocket support for portainer (in reverse proxy, under custom header, hit create and leave default values, then save)
		- Audiobookshelf also needs websocket support
	- when connecting to console, may need to change command from /bin/bash to /bin/sh
	
To make a new directory: `mkdir <directory name>`   or   `mkdir <path/directory name>` (ex. `mkdir config/assets`)

To get full directory path: `pwd`

You can use docker compose run instead of docker compose up and tack the arguments on the end. For example: `docker compose run dperson/samba <arg1> <arg2> <arg3>`

If you don't have permissions for a folder in Ubuntu, run `sudo chown -R jjnether:jjnether <folderpath>`
- Alternatively, might be easier to just run `sudo chown 1000 <file>` where 1000 is the UID

Local drives will be in the /mnt directory, but look here for accessing mapped drives: https://www.youtube.com/watch?v=dZEAQwXzTsA or https://atlassc.net/2021/08/10/mount-synology-with-cifs-utils-on-ubuntu
 - for NFS: https://www.youtube.com/watch?v=3ClCsJHS8lE

sudo service plexmediaserver start
sudo service plexmediaserver stop
sudo service plexmediaserver restart
sudo systemctl status plexmediaserver

IF PLEX CAN'T SEE YOUR MEDIA (PERMISSIONS ISSUE): https://askubuntu.com/questions/150909/plex-wont-enter-my-home-directory-or-other-partitions

For a task manager view, use the command `top`
To see a graph of gpu utilization, use the command `nvtop`

For executing minecraft server commands: `sudo docker exec -i <container_name> rcon-cli`

For hardlinking files:
`ln <sourcefile> <destinationfile>`

For hardlinking all files from one folder to another:
`cp -lR <sourcefolder> <destinationfolder>`
- This will place the source folder in the destination folder
Directories:
- Torrents: `/media/jjnether/PLEX_2/data/torrents`
- Media 1: `/media/jjnether/PLEX/data/media`
- Media 2: `/media/jjnether/PLEX_2/data/media`

To update plex server, download proper .deb file, then run it using "dpkg -i package_name.deb"

To update #docker containers, run `docker compose pull` followed by `docker compose up -d`

In Ubuntu, to see what apt software is ready to update, run `apt list --upgradable`
- to update, run `apt upgrade`

Also
- `apt-get update`
- `apt-get upgrade`

To prune unused #docker images, run `docker image prune`

To run plex media scanner commands, start with "sudo -u plex -s /usr/lib/plexmediaserver/Plex\ Media\ Scanner"
- this will run the command as the plex user
- to activate a manual scan (for credits), tack on "--analyze --manual --server-action credits --section [insert section ID]"
- to find section ID, go to `http://[PMS_IP_Address]:32400/library/sections?X-Plex-Token=[YourTokenGoesHere]` , and the `key=` number at the end of each library is the section id for that library

To run PMM:
First exec into container, then run: `python kometa.py --run`

To login with adminer:
- For server, use the name of the database container (mariadb) (not container_name, but the actual container name in the compose file)
- Then use root username and defined password in docker-compose

To run a .sh script:
- Give execute permission to your script: `chmod +x /path/to/yourscript.sh`
- And run your script: `/path/to/yourscript.sh`

If you get "Unauthorized" when logging into qbittorrent, change HostHeaderValidation to false in qbittorrent.conf

For Themerr update/install, first delete Themerr install:
`sudo rm -r sudo cp -r Themerr-plex.bundle /var/lib/plexmediaserver/Library/Application\ Support/Plex\ Media\ Server/Plug-ins/Themerr-plex.bundle`
Then install new Themerr from top level:
`sudo cp -r Themerr-plex.bundle /var/lib/plexmediaserver/Library/Application\ Support/Plex\ Media\ Server/Plug-ins`

To add line comments in VS: CTRL + K + C
- to remove: CTRL + K + U

To update vuetorrent:
- Navigate to `/home/jjnether/docker/qbit/config/theme`
- Run `git pull`

To download a file from github to the local working directory:
run wget `<url>`

To run plex theme uploader, run `bash /home/jjnether/docker/theme-music-manager-for-plex-1.0/plex-themer/uploader.command`



- make sure you have proper merging between sections using keywords, and keywords are bolded and capitalized
	- every section in a block of dialogue should be routed somewhere, or should indicate end dialogue
- no use of "default" in imp notes, you have to specify the condition
- make sure objectives use the correct format
- Be sure that the PC always has an option (to decline a quest for instance), and make sure you consider if/how the PC would talk to the quest giver to possibly accept the quest