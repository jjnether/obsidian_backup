I just wanted to share what I've gotten to work for me as I've recently been working to get a private server up and finally got it to the state that I wanted. Note that I use the Epic Games version on Windows (cause you can't argue with free), but this should all work with the Steam version as well. Also note that I'm only sharing what worked for me. Some steps may be unnecessary, and this may not work for everyone.

**First of all, these extensive guides are good references to look over if you have questions:**

[User-made guide](https://steamcommunity.com/sharedfiles/filedetails/?id=1110775580)

[Official wiki guide](https://wiki.killingfloor2.com/index.php?title=Dedicated_Server_(Killing_Floor_2))

&#x200B;

**Server Install:**

I installed my server in a separate folder than my game install using SteamCMD (see [official wiki guide](https://wiki.killingfloor2.com/index.php?title=Dedicated_Server_(Killing_Floor_2)#Downloading_SteamCMD:)), but if you're using the EGS version, you can also just run the included `KF2Server.bat` in your install folder, and it should setup the server no problem (if you use this method, you'll have to manually install web admin; see section below). Also make sure you forward the ports listed on the [official guide](https://wiki.killingfloor2.com/index.php?title=Dedicated_Server_(Killing_Floor_2)#Downloading_SteamCMD:) (NTP port not necessary except for weekly outbreak feature). Note that if you don't want to or can't port forward, you and your friends can use an application as a workaround (see **Setup without Port Forwarding** section below).

**Server Configuration:**

There's a bunch of different ways to configure your server. Just read the guides on how to do most of those things. I highly recommend using darkdks' [KF2 Server Tool](https://github.com/darkdks/KF2ServerTool) for running and managing your server. It just makes it easy to configure many different settings and manage your server.

**Web Admin:**

Web Admin is basically a nice feature that I recommend you use. It runs off the server, and when you login to it, you can easily manage your server (KF2 Server Tool has a tab built-in for web admin). Check the [official guide](https://wiki.killingfloor2.com/index.php?title=Dedicated_Server_(Killing_Floor_2)#Downloading_SteamCMD:) to connect to web admin without the KF2 Server Tool. If you installed the server through `KF2Server.bat` in your EGS install, unfortunately you won't have the proper files to run web admin. To install it, you'll have to install the server with SteamCMD (see official guide), once it's finished, copy the `...\kf2server\KFGame\Web` folder and its contents into your server.

**Hosting Custom Maps:**

Here's the part that I think causes the most headaches with people and their server setups. First of all, in order for others to play a custom map on your server,  they need to have a way to download the map. There are a couple common methods of doing this, but the [website](https://www.skillzservers.com/kf2-redirect/) many used to use for this doesn't work anymore, and the other method is implementing Steam Workshop. Using Steam Workshop may work for Steam owners of the game, but I have had no success in getting this method to work (see method in the [user-made guide](https://steamcommunity.com/sharedfiles/filedetails/?id=1110775580)). So I will explain how I was able to get it to work.

1. Download any maps you want (if you want to download a map from the steam workshop but don't own the game on steam, see the section near the bottom).
2. Download and unpack [nginx](http://nginx.org/en/download.html) (we'll use this tool for hosting custom maps locally while allowing others connecting to the server to download the maps to their cache).
3. In the nginx install folder (the directory containing `nginx.exe`), create a new folder called `kf2` and place all your .kfm custom maps inside.
4. Inside the `conf` folder, open `nginx.conf` and replace all the lines with the following:

&#x200B;

    #user  nobody;
    worker_processes  1;
     
    #error_log  logs/error.log;
    #error_log  logs/error.log  notice;
    #error_log  logs/error.log  info;
     
    #pid        logs/nginx.pid;
     
    events {
        worker_connections  1024;
    }
     
    http {
        server {
        listen 80 default_server;
        server_name localhost
     
        access_log <nginx_install_folder>logs/access.log;
        error_log  <nginx_install_folder>logs/error.log;
     
        root <nginx_install_folder>;
        index index.php;
     
        location /kf2 {
        autoindex on;
        }
      }
    }

Be sure you replace `<nginx_install_folder>` with your actual nginx install file path, and make sure that path ends with a forward slash ( `/` ).

1. (sorry, reddit editing made bulleted numbers restart) On your router, forward port 80.
2. Run `nginx.exe` and type into your browser [`http://localhost/kf2`](http://localhost/kf2). If it is running properly, you should see a list of your .kfm map files (note that you'll only see nginx running as a background process in task manager).
3. Copy all your custom map files into your server maps folder (`...\kf2server\KFGame\BrewedPC\Maps`). I placed each file in it's own folder with the same name as the file itself, but I've seen that this may not be necessary.
4. Navigate to `...\kf2server\KFGame\Config` and open `PCServer-KFEngine.ini`.
5. Under `[IpDrv.TcpNetDriver]`, ensure the line `DownloadManagers=IpDrv.HTTPDownload` exists and delete any other lines beginning with `DownloadManagers=...`.
6. Under `[IpDrv.HTTPDownload]`, there should only be the line `RedirectToURL=http://<external_IPv4>/kf2/`, where `<external_IPv4>` is replaced with the number you find [here](https://www.yougetsignal.com/what-is-my-ip-address/). Note that with this setting, map downloading won't work for PC's on the local network of the server. A workaround is to temporarily change `<external_IPv4>` to your local IPv4 address (follow [this](https://www.whatismybrowser.com/detect/what-is-my-local-ip-address) to find it) and connect and download all the custom maps to your local PC(s). Then change `<external_IPv4>` back.
7. In the same directory, open `PCServer-KFGame.ini`
8. Follow the steps in the section **Custom Map Data Store & Map Cycle** in the [user-made guide](https://steamcommunity.com/sharedfiles/filedetails/?id=1110775580) also linked above. Note that all map names and entries are case sensitive.

**Running the Game and Server:**

Launch an instance of nginx, then start the server with the .bat file or with the KF2 Server Tool. To connect to the server (for anybody), open the game, then hit tilde (`~`) and type in `open <external_IPv4>:7777` where `<external_IPv4>` is the number that was defined in the previous section. If you're on the same network as the server, you can type `open <internal_IPv4>` where `<internal_IPv4>` is the local IPv4 address of the server (follow [this](https://www.whatismybrowser.com/detect/what-is-my-local-ip-address) to find it). If connecting on the same PC as the server, you can just type `open 127.0.0.1`.

**Setup without Port Forwarding**

If you can't or don't want to port forward, you and your friends can install and use a program to virtually place you on the same network. Some examples of these are [Hamachi](https://www.vpn.net/), [Radmin VPN](https://www.radmin-vpn.com/), and [Zero Tier](https://www.zerotier.com/) (my personal preference). There are many guides online where you can look up how to set these up, but essentially you and whoever you're playing with just need to connect to each other through the application. When connecting to the server, others must now use your new IPv4 given by the application you choose as the `<external_IPv4>` from the above section. Note that anyone outside your network will not be able to download custom maps you're hosting because you must forward port 80 for the method I described.

**Downloading a Mod from the Steam Workshop (Manually):**

If you own the game on steam, you can just subscribe to the mod on the workshop and after it downloads, find the mod in the proper directory. However, if you use the EGS version, here are steps to download a mod manually:

1. Download SteamCMD from [Valve's official site.](https://developer.valvesoftware.com/wiki/SteamCMD#Downloading_SteamCMD)
2. Find the AppID for the program. Look at the link while browsing the [app on Steam](https://steamcommunity.com/app/294100) (this example of RimWorld has the AppID of 294100)
3. Find the ModID in the link while browsing the [mod](https://steamcommunity.com/sharedfiles/filedetails/?id=735106432) (in this example, the ModID is 735106432)
4. Run SteamCMD and wait for it to download the command line version of steam, then use the commands: `login anonymousworkshop_download_item <AppID > <ModID>` Using the example above would look like: `steam>login anonymoussteam>workshop_download_item 294100 735106432`
5. You should now find the mod in: `...\steamCMD\steamapps\workshop\content\<AppID>\<ModID>` or for the above example it would be: `...\steamCMD\steamapps\workshop\content\294100\735106432`

&#x200B;

I know this was long, but I tried to be as detailed as possible for the noobs out there. Please feel free to ask any questions, and I'll answer as best as I can. I hope this helped at least someone trying to do this server setup!