FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update

RUN apt-get install -y gcc make perl ccache curl python3 aria2 git libssl-dev libncurses5 bison g++-multilib gperf libxml2-utils zlib1g-dev:i386 zip liblz4-tool bc flex openjdk-11-jdk

RUN mkdir -p /root/.bin && \
    curl https://storage.googleapis.com/git-repo-downloads/repo > /root/.bin/repo && \
    chmod a+rx /root/.bin/repo

ENV PATH="/root/.bin:${PATH}"

RUN git config --global user.email "user@email.com"
RUN git config --global user.name "user"

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /workspace

RUN repo init -u https://android.googlesource.com/platform/manifest -b android-10.0.0_r1 &&\
    repo sync


CMD ["/bin/bash"]
