Dockerfiles for building [Dolphin Emulator](https://wiki.dolphin-emu.org/index.php?title=Main_Page), [Ishiiruka](https://github.com/Tinob/Ishiiruka) and [Faster Melee](https://github.com/FasterMelee/Ishiiruka).

# Instructions

Start a container from image:
`docker run [flags] --name [container] ddfabbro/dolphin-emu:[tag]`

You should use `docker run` once to start a container. If you exit the container you can restart it using:
`docker start [container]`

# [flags]

- **X11 support**: 
```
-e DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix \
--device /dev/dri
```
- **Audio support ([source](https://github.com/jessfraz/dockerfiles/issues/85#issuecomment-299431931)):** 
```
--device /dev/snd \
-e PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native \
-v ${XDG_RUNTIME_DIR}/pulse/native:${XDG_RUNTIME_DIR}/pulse/native \
--group-add $(getent group audio | cut -d: -f3)
```
- **Controller support:**
 ```
 --device /dev/input
 ```
- **Mount local game directory:** 
```
-v /path/to/isos:/path/to/anywhere/in/container
```
Your dolphin configuration files will also be stored in this directory

# [container]

Choose a name for the container (e.g. `'Faster Melee 5.9'`)

# [tag]

Pick one of the available [tags](https://hub.docker.com/r/ddfabbro/dolphin-emu/tags/)
