FROM centos:centos8
# forked from Hiroki Takeyama "https://github.com/takeyamajp/docker-centos-sshd"  

# sshd
RUN dnf check-update ; \
    dnf install epel-release openssh-server -y ; \
    dnf upgrade -y ; \
    sed -i 's/^\(UsePAM yes\)/# \1/' /etc/ssh/sshd_config; \
    ssh-keygen -q -t rsa -b 2048 -f /etc/ssh/ssh_host_rsa_key -N '' ; \
    ssh-keygen -q -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N '' ; \
    ssh-keygen -t dsa -f /etc/ssh/ssh_host_ed25519_key  -N ''; \
    echo 'root:root' | chpasswd ; \
   

# linuxbrew 
#    dnf groupinstall 'Development Tools' -y ; \
    dnf install git curl file -y ; \
    dnf install gcc make perl -y ; \

    git clone https://github.com/Homebrew/brew /root/.linuxbrew/Homebrew ; \
    mkdir /root/.linuxbrew/bin ; \
    ln -s ../Homebrew/bin/brew /root/.linuxbrew/bin ; \
    echo "eval $(~/.linuxbrew/bin/brew shellenv)" >> /root/.bash_profile ; \
    /bin/bash -c "source /root/.bash_profile" ; \
    /root/.linuxbrew/bin/brew install hello ; \
    /root/.linuxbrew/bin/brew uninstall hello ; \
    /root/.linuxbrew/bin/brew cleanup ; \   
 
# clean
    dnf clean all; \
    rm -rf /tmp/* /var/tmp/* ; \
    rm -rf /root/.cache \

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D", "-e"]
