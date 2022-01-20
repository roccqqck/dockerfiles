FROM rockylinux:8
# forked from Hiroki Takeyama "https://github.com/takeyamajp/docker-centos-sshd"  

# sshd
RUN dnf -y install openssh-server; \
#    dnf -y install epel-release; \
#    dnf upgrade -y ; \
    sed -i 's/^\(UsePAM yes\)/# \1/' /etc/ssh/sshd_config; \
    ssh-keygen -q -t rsa -b 2048 -f /etc/ssh/ssh_host_rsa_key -N '' ; \
    ssh-keygen -q -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N '' ; \
    ssh-keygen -t dsa -f /etc/ssh/ssh_host_ed25519_key  -N ''; \
    echo 'root:root' | chpasswd ; \

# clean
    dnf clean all; \
    rm -rf /tmp/* /var/tmp/* \

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D", "-e"]
