FROM ubuntu:22.04

# install all software but not gcc arm none eabi (it's too heavy)
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
 && apt-get clean && rm -rf /var/lib/apt/lists/*

# install jlink from source


# ATTENTION!!! Download tar from official site, put it in the same folder with Dockerfile and write its name in first string
COPY JLink_Linux_V794g_x86_64.tgz \
     JLink_Linux.tgz 

RUN  mkdir -p /SEGGER/JLink_Linux && \
     cd /SEGGER && tar xf /JLink_Linux.tgz -C JLink_Linux --strip-components 1 && \
     chmod a-w /SEGGER/JLink_Linux && \
     ls -l /SEGGER/JLink_Linux && \
     rm /JLink_Linux.tgz 

ADD Devices \
     /SEGGER/JLink_Linux/Devices 

ADD JLinkDevices.xml \
     /SEGGER/JLink_Linux/JLinkDevices.xml 

WORKDIR /

# CMD make all

# /SEGGER/JLink_Linux/JLinkExe -CommanderScript jlinkscript.jlink 
# /bin/bash -c "/SEGGER/JLink_Linux/JLinkExe -CommanderScript jlinkscript.jlink"