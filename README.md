# docker-transmission-openvpn-PIA-replacement-files
this is a simple replacement script to enable the use of the next-gen servers on PIA with the docker image docker-transmission-openvpn found here https://github.com/haugene/docker-transmission-openvpn

credit to https://github.com/haugene and https://github.com/fm407 whos code i mergerd together and edited for my purposes, this is just a v1 which i need to tidy up.

the follow steps should get you working until we get an office update.


1.	Download the new next-gen profile pack from here https://www.privateinternetaccess.com/pages/download#
2.	Extract the files to your machine that runs docker
3.	Edit the config files, replacing the line auth-user-path and change it to 
auth-user-path /config/openvpn-credentials.txt 
this way it picks up the vpn creds already passed into the docker container.
4.	Change your docker-compose.yml file and overwrite the files in the docker container with the files you just unpacked an example would be 
- /home/user/config/pia-nextgen:/etc/openvpn/pia:ro
this will overwrite the folder in docker with your files as read only
5.	Download the modded updatePort.sh from https://github.com/mizzi0n/docker-transmission-openvpn-PIA-replacement-files/blob/main/updatePort.sh 
6.	Map that in your docker-compose.yml, again an example is adding the line
- /home/user/config/updatePort.sh:/etc/transmission/updatePort.sh:ro
7.	That should get it up and running as well as keep your port request alive every 15 minutes.
