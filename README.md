# docker plex

This is a Dockerfile to set up (https://plex.tv/ "Plex Media Server") - (https://plex.tv/)

Build from docker file

```
git clone git@github.com:captnbp/docker-plex.git
cd docker-plex
docker build -t plex .
```

You can also obtain it via:

```
docker pull captnbp/plex
```

---
Instructions to run:

```
docker run -d -h *your_host_name* -v /*your_config_location*:/config -v /*your_videos_location*:/media -p 32400:32400  plex
```
or for auto detection add --net="host". Though be aware this more insecure but should be fine on your personal servers.

```
docker run -d --net="host" -h *your_host_name* -v /*your_config_location*:/config -v /*your_videos_location*:/media -p 32400:32400  plex
```

The first time it runs, it will initialize the config directory and terminate.

You will need to modify the auto-generated config file to allow connections from your local IP range. This can be done by modifying the file:

*your_config_location*/Library/Application Support/Plex Media Server/Preferences.xml

and adding ```allowedNetworks="192.168.1.0/255.255.255.0" ``` as a parameter in the <Preferences ...> section. (Or what ever your local range is)

Start the docker instance again and it will stay as a daemon and listen on port 32400.

Browse to: ```http://*ipaddress*:32400/web``` to run through the setup wizard.

