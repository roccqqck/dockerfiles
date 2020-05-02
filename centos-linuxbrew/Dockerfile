FROM centos:8
# forked from Hiroki Takeyama "https://github.com/takeyamajp/docker-centos-sshd"  

# sshd
RUN dnf check-update ; \
    dnf install epel-release -y ; \
    dnf upgrade -y ; \

# linuxbrew 
#    dnf groupinstall 'Development Tools' -y ; \
    dnf install git curl file -y ; \
    dnf install gcc make perl -y ; \

    git clone https://github.com/Homebrew/brew /home/linuxbrew/.linuxbrew/Homebrew ; \
    mkdir /home/linuxbrew/.linuxbrew/bin ; \
    ln -s /home/linuxbrew/.linuxbrew/Homebrew/bin/brew /home/linuxbrew/.linuxbrew/bin ; \
    echo "eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" >> /root/.bash_profile ; \
    /bin/bash -c "source /root/.bash_profile" ; \
    /home/linuxbrew/.linuxbrew/bin/brew install patchelf ; \
    /home/linuxbrew/.linuxbrew/bin/brew uninstall patchelf ; \
    /home/linuxbrew/.linuxbrew/bin/brew cleanup ; \   
 
# clean
    dnf clean all; \
    rm -rf /tmp/* /var/tmp/* ; \
    rm -rf /root/.cache \

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D", "-e"]
