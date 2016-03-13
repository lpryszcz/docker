FROM ubuntu

MAINTAINER lpryszcz <l.p.pryszcz@gmail.com>

# install packages && clean-up 
RUN apt-get update && apt-get install -y wget perl python-biopython python-numpy bwa #last-align mummer
RUN rm -rf /var/lib/apt/lists/*

# LAST & GapCloser in /bin
RUN cd /bin && wget -q https://raw.githubusercontent.com/lpryszcz/bin/master/last{al,db} && chmod +x last* && wget -q http://downloads.sourceforge.net/project/soapdenovo2/GapCloser/bin/r6/GapCloser-bin-v1.12-r6.tgz && tar xpfz GapCloser-bin-v1.12-r6.tgz GapCloser && chmod +x GapCloser

# SSPACE && redundans in /root/srt
RUN mkdir -p /root/src && cd /root/src && \
wget -q http://www.baseclear.com/base/download/41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && tar xpfz 41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && ln -s SSPACE-STANDARD-3.0_linux-x86_64 SSPACE && wget -O- -q http://cpansearch.perl.org/src/GBARR/perl5.005_03/lib/getopts.pl > SSPACE/dotlib/getopts.pl && \
wget -q -O redundans.tgz https://github.com/lpryszcz/redundans/archive/master.tar.gz && tar xpfz redundans.tgz && mv redundans-master redundans && ln -s /root/src/redundans /redundans && rm *gz
