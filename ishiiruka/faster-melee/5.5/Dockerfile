FROM ddfabbro/dolphin-emu:dependencies

ENV COMMITHASH fc3a235

RUN apt-get update && apt-get install -y \
	build-essential \
	ca-certificates \
	&& cd /usr/src/ \
	&& git clone https://github.com/FasterMelee/Ishiiruka.git \
	&& cd Ishiiruka \
	&& git checkout $COMMITHASH \
	&& mkdir build && cd build \
	&& cmake .. \
	&& make -j ${THREADS:-`cat /proc/cpuinfo | grep processor | wc -l`} \
	&& make install \
	&& cd / \
	&& rm -rf /usr/src/Ishiiruka/ /var/lib/apt/lists/*

ENTRYPOINT [ "/usr/local/bin/dolphin-emu" ]
