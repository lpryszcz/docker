FROM ubuntu

MAINTAINER lpryszcz <l.p.pryszcz@gmail.com>

# install packages && clean-up 
RUN apt-get update && apt-get install -y build-essential wget perl python-biopython python-numpy bwa #last-align mummer
RUN rm -rf /var/lib/apt/lists/*

# GapCloser in /bin
RUN cd /bin && wget -q http://downloads.sourceforge.net/project/soapdenovo2/GapCloser/bin/r6/GapCloser-bin-v1.12-r6.tgz && tar xpfz GapCloser-bin-v1.12-r6.tgz GapCloser && chmod +x GapCloser

# LAST in /root/srt
RUN mkdir -p /root/src && cd /root/src && \
wget -q http://last.cbrc.jp/last/index.cgi/archive/tip.tar.gz && tar xpfz tip.tar.gz && ln -s last-*/ last && cd last && make
RUN ln -s /root/src/last/src/lastal /root/src/last/src/lastaldb /bin

# SSPACE && redundans in /root/srt
RUN cd /root/src && wget -q http://www.baseclear.com/base/download/41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && tar xpfz 41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && ln -s SSPACE-STANDARD-3.0_linux-x86_64 SSPACE && wget -O- -q http://cpansearch.perl.org/src/GBARR/perl5.005_03/lib/getopts.pl > SSPACE/dotlib/getopts.pl && \
wget -q -O redundans.tgz https://github.com/lpryszcz/redundans/archive/master.tar.gz && tar xpfz redundans.tgz && mv redundans-master redundans && ln -s /root/src/redundans /redundans && rm *gz
