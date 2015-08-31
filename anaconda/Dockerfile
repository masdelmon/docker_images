# Reference:
# https://github.com/ContinuumIO/docker-images/blob/master/anaconda/Dockerfile
# https://github.com/jupyter/docker-stacks/tree/master/minimal-notebook
# https://github.com/ipython/docker-notebook/tree/master/notebook

FROM ubuntu
MAINTAINER Colin Fang <colinfang@live.com>

ENV downloads /downloads
RUN mkdir $downloads

RUN apt-get update && apt-get install -y \
	wget
	
ENV anaconda_url https://repo.continuum.io/archive/Anaconda-2.3.0-Linux-x86_64.sh
ENV anaconda_path /opt/anaconda

RUN wget -nv -O $downloads/anaconda.sh $anaconda_url && \
    /bin/bash $downloads/anaconda.sh -b -p $anaconda_path
	
ENV PATH $anaconda_path/bin:$PATH

RUN conda update -y conda

RUN rm $downloads/anaconda.sh
# Remove cached package tarballs.
RUN conda clean -yt

# For ipython notebook
EXPOSE 8888

RUN conda info -a
RUN ipython -c "print 'Hello World'"