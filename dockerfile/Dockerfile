FROM ubuntu:xenial

MAINTAINER "Carlos H Brandt <carloshenriquebrandt at gmail>"

ENV DEBIAN_FRONTEND=noninteractive

# Docker ubuntu:xenial should have main/universe/multiverse repos already enabled.
#RUN echo 'deb http://archive.ubuntu.com/ubuntu xenial main universe multiverse' >> /etc/apt/sources.list

RUN apt-get update                                                                      &&\
    apt-get install -y --no-install-recommends equivs subversion binutils g++ git-core  &&\
    apt-get clean

RUN svn checkout svn://svn.code.sf.net/p/slam6d/code/trunk slam6d-code  &&\
    cd slam6d-code                                                      &&\
    equivs-build doc/equivs/control.ubuntu.xenial                       &&\
    dpkg -i 3dtk-build-deps_1.0_all.deb                                 ;\
    apt-get -f install -y --no-install-recommends                       &&\
    apt-get clean                                                       &&\
    make && make clean                                                  &&\
    echo "PATH=${PWD}/bin:\$PATH" >> /etc/profile                       &&\
    echo "PATH=${PWD}/bin:\$PATH" >> /etc/bash.bashrc

ARG WORKDIR='/work'

RUN git clone -b stable https://github.com/chbrandt/docker_entrypoint.git && \
    ln -sf docker_entrypoint/entrypoint.sh /.

ENTRYPOINT ["/entrypoint.sh"]

