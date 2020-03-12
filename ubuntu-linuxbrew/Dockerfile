# linuxbrew
# forked from  Aleksandar Diklic "https://github.com/rastasheep"

FROM ubuntu:18.04

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /root/.linuxbrew/bin:$PATH

### apt setting  #######################################

RUN apt-get update --fix-missing && \
    apt-get install -y --no-install-recommends \
                vim wget \
                ca-certificates bzip2 software-properties-common \
                build-essential curl file git locales && \
    locale-gen en_US.UTF-8 && \
    apt-get upgrade -y && \

### linuxbrew ##########################################

    git clone https://github.com/Homebrew/brew /root/.linuxbrew/Homebrew && \
    mkdir /root/.linuxbrew/bin && \
    ln -s ../Homebrew/bin/brew /root/.linuxbrew/bin && \
    echo "eval $(~/.linuxbrew/bin/brew shellenv)" >> /root/.bashrc &&\
    /bin/bash -c "source /root/.bashrc" && \
    /root/.linuxbrew/bin/brew install hello && \
    /root/.linuxbrew/bin/brew uninstall hello && \
    /root/.linuxbrew/bin/brew cleanup && \

### clean #########################################

    apt-get autoclean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/* \
           /tmp/* \
           /var/tmp/* && \
    rm -rf /root/.cache

EXPOSE 6006 8888
# CMD    [ "/usr/sbin/sshd", "-D"]
CMD [ "/bin/bash" ]
