FROM       ubuntu:20.04
# forked from  Aleksandar Diklic "https://github.com/rastasheep"

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
                openssh-server && \
   
 
    mkdir /var/run/sshd && \

    echo 'root:root' |chpasswd && \

    sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config && \

    mkdir /root/.ssh && \

    apt-get autoclean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]
