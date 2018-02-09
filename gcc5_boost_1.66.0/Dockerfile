# Use the latest stable Ubuntu version (currently 16.04)
FROM ubuntu:16.04

# Make sure the image is updated, install some prerequisites,
# Download the latest version of Clang (official binary) for Ubuntu
# Extract the archive and add Clang to the PATH
RUN apt update && apt install -y 

RUN apt-get install gcc-5 -y
RUN apt-get install g++-5 -y
RUN ln -s /usr/bin/g++-5 /usr/bin/g++ 
RUN apt-get install cmake -y
RUN apt-get install curl -y
RUN apt-get install bzip2 -y

RUN curl -SL https://dl.bintray.com/boostorg/release/1.66.0/source/boost_1_66_0.tar.bz2 --output boost_1_66_0.tar.bz2
RUN tar jxf boost_1_66_0.tar.bz2
RUN cd boost_1_66_0 \
			&& ./bootstrap.sh \
			&& ./b2 link=static threading=multi --layout=tagged --with-test

RUN mkdir future_build
WORKDIR future_build

# Start from a Bash prompt
CMD [ "/bin/bash" ]
