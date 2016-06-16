FROM alpine

MAINTAINER lpryszcz <l.p.pryszcz@gmail.com>

RUN apk add --update --no-cache bash bash-doc bash-completion wget python perl tar gzip make gcc g++ musl-dev zlib-dev

# GapCloser, last & bwa in /bin 
RUN cd /sbin && wget -q http://downloads.sourceforge.net/project/soapdenovo2/GapCloser/bin/r6/GapCloser-bin-v1.12-r6.tgz && tar xpfz GapCloser-bin-v1.12-r6.tgz GapCloser && chmod +x GapCloser && \
wget http://last.cbrc.jp/last/index.cgi/archive/tip.tar.gz && ln -s last-bb03593936dc last && cd last && make && make install && /
wget http://downloads.sourceforge.net/project/bio-bwa/bwa-0.7.15.tar.bz2 && tar xpfjv bwa-0.7.15.tar.bz2 && ln -s bwa-0.7.15 bwa && cd bwa && make && make install

# still unable to build bwa: need to add `#include <stdint.h>` to kthread.c
# it probably won't work due to replacement of standard glibc by musl-libc https://wiki.alpinelinux.org/wiki/How_to_get_regular_stuff_working#Compiling_:_a_few_notes_and_a_reminder

# SSPACE && redundans in /root/srt
RUN mkdir -p /root/src && cd /root/src && \
cd /root/src && wget -q http://www.baseclear.com/base/download/41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && tar xpfz 41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && ln -s SSPACE-STANDARD-3.0_linux-x86_64 SSPACE && wget -O- -q http://cpansearch.perl.org/src/GBARR/perl5.005_03/lib/getopts.pl > SSPACE/dotlib/getopts.pl && \
wget --no-check-certificate -q -O redundans.tgz https://github.com/lpryszcz/redundans/archive/master.tar.gz && tar xpfz redundans.tgz && mv redundans-master redundans && ln -s /root/src/redundans /redundans && rm *gz

