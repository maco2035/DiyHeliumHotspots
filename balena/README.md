# Helium DIY hotspot using balena.io with RAK2245 or RAK2287 concentrators

This document explains how to deploy a Helium DIY hostpot with balena on the family of RAK concentrators 2245 and 2287 on Raspberry Pi 3 or 4 (using balenaOS 64 bits).

## Getting started

### Hardware

* Raspberry Pi 3 or 4
* SD card for the Raspberry Pi

#### LoRa Concentrators

* [RAK 2287 Concentrator](https://store.rakwireless.com/products/rak2287-lpwan-gateway-concentrator-module)
* [RAK 2287 Pi Hat](https://store.rakwireless.com/products/rak2287-pi-hat)

or

* [RAK 2245 pi hat](https://store.rakwireless.com/products/rak2245-pi-hat)

### Software

* A balenaCloud account ([sign up here](https://dashboard.balena-cloud.com/))
* [balenaEtcher](https://balena.io/etcher)

Once all of this is ready, you are able to deploy the Helium DIY Hotspot following instructions below.


## Before deploying

At balena with all the community developers we are working to provide a simple way to deploy independently of the concentrator or the LoRaWAN region.

On this document you will find some of the projects available with balena to quickly work with your DIY Helium Hotspot.

DISCLAIMER: It's important to introduce your LoRaWAN region on the dockerfile template files for the lora packet forwarder. So, it's strongly recommended to clone the following repositories if you need to change the region.



## DIY Helium Hotspot repositories

Feel free to introduce your versions here.

### PastaGringo

This is a repository that works on RAK 2245. It is configured for the EU region.

* https://github.com/PastaGringo/balenaos-helium-gtw 

[![](https://www.balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/PastaGringo/balenaos-helium-gtw)

This is a repository that works on RAK 2287 (based on sx1302). It is configured for the US region.

* https://github.com/PastaGringo/balenaos-helium-gtw-sx1302

[![](https://www.balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/PastaGringo/balenaos-helium-gtw-sx1302)


### just4give

This is a repository that works on RAK 2245 repository. It contains a webserver that enables you to access the _swarmkey_ easily. It is configured for the US region.

* https://github.com/just4give/helium-dyi-hotspot-balena-pi4

[![](https://www.balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/just4give/helium-dyi-hotspot-balena-pi4)


### bottxnife

This is a repository for RAK2287 with the wifi-connect project. That means that it's easy to define another WiFi credentials on the hotspot with your mobile phone, in case you move the hotspot. It is configured for the US region.

* https://github.com/bottxrnife/helium-2287-w

[![](https://www.balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/bottxrnife/helium-2287-w)


This is a repository that mixes Pastagringo and just4give website idea on RAK 2287 configured for the US region.

* https://github.com/bottxrnife/heilum-2287

[![](https://www.balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/bottxrnife/heilum-2287)

This is a repository for RAK2245 configured for the US region.

* https://github.com/bottxrnife/helium-2245

[![](https://www.balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/bottxrnife/helium-2245)


## Check the Hotspot on balenaCloud

Once your will click the ```Deploy with balena``` button, follow instructions. First click Create a balena Application, then add a Device and flash an SD card with that OS image dowloaded from balenaCloud. Enjoy the magic 🌟Over-The-Air🌟!

Once the Raspberry Pi will boot up with the flashed SD card the DIY Helium Hotspot containers will be deployed into the device and it will start running. You will be able to check all the logs from the balenaCloud logs.

If you need to configure the miner, get into the miner container and interact via SSH on the balenaCloud dashboard.

## ToDo

We are currently working on a Hotspot version with these containers:

* wifi-connect
* Helium LoRa packet forwarder
* watcher

THe WiFi-Connect container will help Hotpsot owners that change the WiFi SSID or move the hotpsot to change easily the WiFi credentials.

The Helium LoRa packet forwarder is the Helium standard packet forwarder.

The watcher should deploy and auto-update the ```miner``` container. To do it we need several features:
- the watcher should create a ```Docker container``` download the miner container and run it. 
- Create a ```crontab``` that everyday would check for a newer miner version, and it case that there would be a newer miner version, update it (removing the previous container and running the new one with the latest version). 
- On the other hand the watcher should be able to visualize all the logs from the miner logs. 
- Finally it's important that the watcher enable the users to download/upload easily the ```swarm_key``` from the miner.


