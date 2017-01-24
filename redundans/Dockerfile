FROM ubuntu:16.04

MAINTAINER lpryszcz <l.p.pryszcz+docker@gmail.com>

# install packages
RUN apt update && apt install -y perl python python-pip git make g++ zlib1g-dev && pip install matplotlib

# redundans in /root/srt
RUN mkdir -p /root/src && cd /root/src && \
git clone --recursive https://github.com/lpryszcz/redundans.git && cd redundans && \
(cd bin/bwa && make clean && make) && (cd bin/last && make clean && make) && (cd bin/snap && make clean && make)

# clean-up
RUN apt purge -y git make g++ zlib1g-dev python-pip && apt autoremove -y && apt autoclean -y && rm -rf /var/lib/apt/lists/*

# test & rm
RUN cd /root/src/redundans && ./redundans.py -v -i test/*.fq.gz -f test/contigs.fa -o test/run1 && \
find . -name .git | xargs rm -r test/run1