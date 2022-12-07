# About

**Open Forge Containers** is a project that I started due to the need for a self-host Minecraft Forge server that will allow me to play VRCraft 1.18.2 with few mods with my flatmate.

Due to the fact that other images containing Minecraft Forge does not satisfy my needs, I decided to start this small project.

Don't forget to visit [GitHub](https://github.com/michalwitek1232/open-forge-containers)

# Available tags

- `1.18.2` - Minecraft Forge for 1.18.2 version of the game with Forge version: `40.1.51`
- `1.18.2-vrcraft` -  Minecraft Forge for 1.18.2 version of the game with Forge version: `40.1.51` and VRCraft mod installed
- `experimental` - Minecraft Forge for user-specified version, requires some knowledge about Forge, Java versions and other stuff

# Usage


```
docker run -p 25565:25565 --restart=on-failure michalwitek1232/open-forge-containers:1.18.2
```
This will store the workspace in `/minecraft/forge/server`.
All Forge Server's data will be stored in there - including mods, worlds and configuration.
You will probably want to make that an explicit volume, so you can manage it and attach to another container for upgrades :

```
docker run -p 25565:25565 --restart=on-failure -v server_home:/minecraft/forge/server michalwitek1232/open-forge-containers:1.18.2
```
This will automatically create a **server_home** [docker volume](https://docs.docker.com/storage/volumes/) on the host machine.
Docker volumes retain their content even when the container is stopped, started, or deleted.
