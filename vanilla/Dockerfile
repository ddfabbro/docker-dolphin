FROM ubuntu:18.04

RUN apt-get update &&  apt-get install -y --no-install-recommends \
	software-properties-common \


RUN apt-add-repository ppa:dolphin-emu/ppa \
    && apt update && apt install -y --no-install-recommends \
        dolphin-emu \
    && rm -rf /var/lib/apt/lists/*

ENTRYPOINT [ "/usr/games/dolphin-emu" ]