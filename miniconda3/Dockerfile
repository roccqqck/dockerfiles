# python miniconda3 and jupyter
# forked from https://github.com/ContinuumIO

FROM ubuntu:bionic-20190912.1

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /root/conda/bin:$PATH

### apt setting  #######################################

RUN apt-get update --fix-missing && \
    apt-get install -y --no-install-recommends \
                tmux vim wget git \
                ca-certificates bzip2 curl && \

### miniconda ##########################################


    wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-4.7.10-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /root/conda && \
#    ln -s /root/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
#    echo ". /root/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
#    echo "conda activate base" >> ~/.bashrc && \
    /root/conda/bin/conda update --all -y && \
    /root/conda/bin/conda init && \
    /bin/bash -c "source /root/.bashrc" && \

## change python version #####
#   /root/conda/bin/conda install python=3.6 -y  && \

#    /root/conda/bin/pip --no-cache-dir install --upgrade jupyter && \
    /root/conda/bin/conda clean -afy && \
    rm ~/miniconda.sh && \
#    rm -rf /root/conda/pkgs && \

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
