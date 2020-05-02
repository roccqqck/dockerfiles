# linuxbrew ssh
# forked from  Aleksandar Diklic "https://github.com/rastasheep"

FROM ubuntu:18.04

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /home/linuxbrew/.linuxbrew/bin:$PATH

### ssh setting  #######################################

RUN apt-get update --fix-missing && \
    apt-get install -y --no-install-recommends \
                openssh-server \
                vim wget \
                ca-certificates bzip2 software-properties-common \
                build-essential curl file git locales && \
    locale-gen en_US.UTF-8 && \
    apt-get upgrade -y && \
    mkdir /var/run/sshd && \

    echo 'root:root' |chpasswd && \

    sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config && \

    mkdir /root/.ssh && \


### linuxbrew ##########################################

    git clone https://github.com/Homebrew/brew /home/linuxbrew/.linuxbrew/Homebrew ; \
    mkdir /home/linuxbrew/.linuxbrew/bin ; \
    ln -s /home/linuxbrew/.linuxbrew/Homebrew/bin/brew /home/linuxbrew/.linuxbrew/bin ; \
    echo "eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" >> /root/.bashrc ; \
    /bin/bash -c "source /root/.bashrc" ; \
    /home/linuxbrew/.linuxbrew/bin/brew install patchelf ; \
    /home/linuxbrew/.linuxbrew/bin/brew uninstall patchelf ; \
    /home/linuxbrew/.linuxbrew/bin/brew cleanup ; \

### clean #########################################

    apt-get autoclean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/* \
           /tmp/* \
           /var/tmp/* && \
    rm -rf /root/.cache

EXPOSE 22 6006 8888
CMD    [ "/usr/sbin/sshd", "-D"]
# CMD [ "/bin/bash" ]
