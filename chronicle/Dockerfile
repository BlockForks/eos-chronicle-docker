FROM ubuntu:latest

RUN apt update
RUN apt install -y wget gnupg2 software-properties-common
RUN wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | apt-key add -
RUN apt-add-repository 'deb https://apt.kitware.com/ubuntu/ bionic main'
RUN add-apt-repository ppa:ubuntu-toolchain-r/test 
RUN apt install -y git g++-8 cmake libssl-dev libgmp-dev zlib1g-dev
RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 800 --slave /usr/bin/g++ g++ /usr/bin/g++-8
RUN wget https://dl.bintray.com/boostorg/release/1.67.0/source/boost_1_67_0.tar.gz
RUN tar -xvzf boost_1_67_0.tar.gz
RUN cd boost_1_67_0 && ./bootstrap.sh && ./b2 install
# use " sudo ./b2 install -j N" for N CPU cores for faster compiling (may require more RAM)
RUN git clone https://github.com/EOSChronicleProject/eos-chronicle.git && \ 
    cd eos-chronicle && git submodule update --init --recursive && \
    mkdir build && cd build && cmake .. && make -j 10 && \
    mv chronicle-receiver /opt/
RUN mkdir /data
RUN rm -rf ~/eos-chronicle

COPY entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/entrypoint.sh
WORKDIR /opt/data
ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

