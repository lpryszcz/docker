FROM ubuntu:16.04

MAINTAINER lpryszcz <l.p.pryszcz+docker@gmail.com>

# install packages
RUN apt update && apt install -y wget perl python python-pip git make automake g++ zlib1g-dev && pip install matplotlib

# redundans in /root/srt # banches: master & de_novo
RUN mkdir -p /root/src && cd /root/src && \
git clone -b de_novo --recursive https://github.com/lpryszcz/redundans.git && cd redundans && bin/.compile.sh

# clean-up
RUN apt purge -y git make g++ zlib1g-dev python-pip && apt autoremove -y && apt autoclean -y && rm -rf /var/lib/apt/lists/*

# test & rm
RUN cd /root/src/redundans && ./redundans.py -v -i test/*_?.fq.gz -o test/run.denovo && find . -name .git | xargs rm -r test/run*