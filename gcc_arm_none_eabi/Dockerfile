FROM ubuntu:22.04

# install all software but not gcc arm none eabi (it's too heavy)
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    build-essential \
    make \
    ninja-build \
    cmake \
    doxygen \
    graphviz \
 && apt-get clean && rm -rf /var/lib/apt/lists/*

# install gcc arm none eabi from source

# ATTENTION!!! Download tar from official site, put it in the same folder with Dockerfile and write its name in first string
COPY gcc-arm-none-eabi-10.3-2021.10-x86_64-linux.tar.bz2 \
     gcc-arm-none-eabi.tar.bz2 

# unpack the archive to a neatly named target directory & remove the archive
RUN mkdir gcc-arm-none-eabi && tar xjfv gcc-arm-none-eabi.tar.bz2  -C gcc-arm-none-eabi --strip-components 1 && \
    rm gcc-arm-none-eabi.tar.bz2 
# add the tools to the path
ENV PATH="/gcc-arm-none-eabi/bin:${PATH}"

WORKDIR /work

# ENTRYPOINT [ "make" ]

CMD make all
