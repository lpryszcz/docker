FROM alpine

MAINTAINER lpryszcz <l.p.pryszcz@gmail.com>

RUN apk add --update --no-cache python perl bash wget build-base zlib-dev

# bwa, GapCloser & last in /bin 
RUN mkdir -p /root/src && cd /root/src && wget http://downloads.sourceforge.net/project/bio-bwa/bwa-0.7.15.tar.bz2 && tar xpfj bwa-0.7.15.tar.bz2 && ln -s bwa-0.7.15 bwa && cd bwa && \
cp kthread.c kthread.c.org && echo "#include <stdint.h>" > kthread.c && cat kthread.c.org >> kthread.c && \
sed -ibak 's/u_int32_t/uint32_t/g' `grep -l u_int32_t *.c *.h` && make && cp bwa /bin/ && \
cd /root/src && wget http://liquidtelecom.dl.sourceforge.net/project/soapdenovo2/GapCloser/src/r6/GapCloser-src-v1.12-r6.tgz && tar xpfz GapCloser-src-v1.12-r6.tgz && ln -s v1.12-r6/ GapCloser && cd GapCloser && make && cp bin/GapCloser /bin/ && \
cd /root/src && wget http://last.cbrc.jp/last-744.zip && unzip last-744.zip && ln -s last-744 last && cd last && make && make install && \
cd /root/src && rm -r last* bwa* GapCloser* v* 

# SSPACE && redundans in /root/srt
RUN cd /root/src && wget -q http://www.baseclear.com/base/download/41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && tar xpfz 41SSPACE-STANDARD-3.0_linux-x86_64.tar.gz && ln -s SSPACE-STANDARD-3.0_linux-x86_64 SSPACE && wget -O- -q http://cpansearch.perl.org/src/GBARR/perl5.005_03/lib/getopts.pl > SSPACE/dotlib/getopts.pl && \
wget --no-check-certificate -q -O redundans.tgz https://github.com/lpryszcz/redundans/archive/master.tar.gz && tar xpfz redundans.tgz && mv redundans-master redundans && ln -s /root/src/redundans /redundans && rm *gz

RUN apk del wget build-base zlib-dev 
RUN apk add libstdc++
