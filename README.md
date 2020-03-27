Summary
=======

EAPeak is a tool designed to information gathering EAP networks prior to an attack with a tool like EAPHammer. It will capture EAP requests from clients connecting into a network and gather usernames(PEAP/LEAP) and certificate information passively, allowing an attacker to replicate this network more closely, or to use the information to further probe the enabled radius options for a network.

My Spin
=======

I had some build issues with the tool so I've put it inside a Docker container and added some start up options to make life easier. Now just pull, build, run with the appropriate options and go.

Build Instructions
=======

git clone https://github.com/SecurityJon/epeak_docker.git
cd eapeak_docker
sudo docker build -t securityjon_eapeak:1.0 .


Running the Tool
=======
First we will force the host to kill off any access to the wifi interfaces
`sudo airmon-ng check kill`
To run the tool against a specific SSID, use the below
`sudo docker run -it --net="host" --privileged -e WIFIINTERFACE=<Name In Here> -e SSID="<Name In Here>" securityjon_eapeak:1.0`
To run the tool against all SSIDs it can see, use the below
`sudo docker run -it --net="host" --privileged -e WIFIINTERFACE=<Name In Here> securityjon_eapeak:1.0`
To get inside the Docker container and run the tool with more options. The tool is contained within /eapeak
`sudo docker run -it --net="host" --privileged --entrypoint /bin/bash -e securityjon_eapeak:1.0`







