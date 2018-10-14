# Use the latest stable Ubuntu version (currently 16.04)
FROM ubuntu:16.04

# Make sure the image is updated, install some prerequisites,
# Download the latest version of Clang (official binary) for Ubuntu
# Extract the archive and add Clang to the PATH
RUN apt-get update && apt install -y 

RUN apt-get install apt-utils -y
RUN apt-get install make -y
RUN apt-get install clang-5.0 -y
RUN ln -s /usr/bin/clang++-5.0 /usr/bin/clang++
RUN ln -s /usr/bin/clang-5.0 /usr/bin/clang 
RUN apt-get install curl -y
RUN apt-get install bzip2 -y

RUN mkdir cmake && curl -SL "https://cmake.org/files/v3.12/cmake-3.12.3-Linux-x86_64.tar.gz" | tar --strip-components=1 -xz -C cmake
RUN export PATH=/cmake/bin:${PATH}

RUN curl -SL https://dl.bintray.com/boostorg/release/1.66.0/source/boost_1_66_0.tar.bz2 --output boost_1_66_0.tar.bz2
RUN tar jxf boost_1_66_0.tar.bz2

RUN cd boost_1_66_0 \
	&& ./bootstrap.sh  --with-toolset=clang \
	&& ./b2 link=static threading=multi --layout=tagged --with-test

RUN mkdir future_build
WORKDIR future_build

# Start from a Bash prompt
CMD [ "/bin/bash" ]
