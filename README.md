Docker images for [Dolphin Emulator](https://wiki.dolphin-emu.org/index.php?title=Main_Page), [Ishiiruka](https://github.com/Tinob/Ishiiruka) and [FasterMelee](https://github.com/FasterMelee/Ishiiruka).

# Instructions

Start a container from image:
`docker run [flags] ddfabbro/dolphin-emu:[version]`

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
-v /path/to/isos:/root
```
