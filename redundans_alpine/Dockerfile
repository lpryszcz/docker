FROM alpine

MAINTAINER lpryszcz <l.p.pryszcz@gmail.com>

RUN apk add --update --no-cache bash wget python sqlite #perl py-pip 

# add testing and edge repo
RUN echo -e "http://nl.alpinelinux.org/alpine/edge/main\nhttp://nl.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories
RUN apk add --update --no-cache py-pysqlite # py-numpy
# biopython missing

# blat & GapCloser in /bin
#RUN cd /sbin && wget --no-check-certificate -q https://raw.githubusercontent.com/lpryszcz/bin/master/blat && chmod +x blat &&  wget -q http://downloads.sourceforge.net/project/soapdenovo2/GapCloser/bin/r6/GapCloser-bin-v1.12-r6.tgz && tar xpfz GapCloser-bin-v1.12-r6.tgz GapCloser && chmod +x GapCloser

# SSPACE && redundans in /root/srt
#RUN mkdir -p /root/src && cd /root/src && wget -q http://www.baseclear.com/base/download/41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && tar xpfz 41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && ln -s SSPACE-STANDARD-3.0_linux-x86_64 SSPACE && wget -O- -q http://cpansearch.perl.org/src/GBARR/perl5.005_03/lib/getopts.pl > SSPACE/dotlib/getopts.pl && wget --no-check-certificate -q -O redundans.tgz https://github.com/lpryszcz/redundans/archive/master.tar.gz && tar xpfz redundans.tgz && mv redundans-master redundans && ln -s /root/src/redundans /redundans && rm *gz
