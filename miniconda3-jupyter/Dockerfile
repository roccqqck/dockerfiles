# python miniconda3 and jupyter
# forked from https://github.com/ContinuumIO

FROM ubuntu:bionic-20191010

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /root/miniconda3/bin:$PATH

### apt setting  #######################################

RUN apt-get update --fix-missing && \
    apt-get install -y --no-install-recommends \
                tmux vim wget git \
                ca-certificates bzip2 curl && \
    apt-get upgrade -y && \

### miniconda ##########################################


    wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-4.7.12-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /root/miniconda3 && \
#    ln -s /root/miniconda3/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
#    echo ". /root/miniconda3/etc/profile.d/conda.sh" >> ~/.bashrc && \
#    echo "conda activate base" >> ~/.bashrc && \
    /root/miniconda3/bin/conda update --all -y && \
    /root/miniconda3/bin/conda init && \
    /bin/bash -c "source /root/.bashrc" && \

## change python version #####
#    /root/miniconda3/bin/conda install python=3.6 -y  && \

#    /root/miniconda3/bin/pip --no-cache-dir install --upgrade jupyter && \
    /root/miniconda3/bin/conda install jupyterlab -y && \
    /root/miniconda3/bin/conda clean -afy && \
    rm ~/miniconda.sh && \
#    rm -rf /root/miniconda3/pkgs && \

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
