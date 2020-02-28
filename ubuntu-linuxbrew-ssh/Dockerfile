# python miniconda3 and openssh for vscode pycharm ssh interpreter
# forked from  Aleksandar Diklic "https://github.com/rastasheep"
# forked from https://github.com/ContinuumIO

FROM ubuntu:18.04

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /root/miniconda3/bin:$PATH

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

EXPOSE 22 6006 8888
CMD    [ "/usr/sbin/sshd", "-D"]
# CMD [ "/bin/bash" ]
