# Docker builds

## redundans_alpine
Trying to build minimal image for [Redundans](https://github.com/lpryszcz/redundans).
But cannot build biopython. 

```bash
cd redundans_alpine
docker build -t lpryszcz/redundans:alpine .

# 9M with bash & wget
# 45M with python, sqlite & 55Mb with py-pi
# 47M with py-sqlite
## 198Mb with numpy!

# 80Mb with redundans & 120 with perl


## abandon numpy 145M and biopython (not installeable): easy
## and SSPACE 11M (& perl 40M): more difficult
# ia32 32-bit libs needed by:
## BLAT & GapCloser

# biopython
## limits.h: No such file or directory
```


## redundans
Ubuntu-based (~150Mb) image for [Redundans](https://github.com/lpryszcz/redundans).

```bash
# build latest
cd redundans
docker build --pull --no-cache --force-rm -t lpryszcz/redundans:v0.12b .

# alias
docker tag -f lpryszcz/redundans:v0.12b lpryszcz/redundans:latest

# test
docker run -it -w /root/src/redundans lpryszcz/redundans ./redundans.py -v -i test/{600,5000}_{1,2}.fq.gz -f test/contigs.fa -o test/run1

# push
docker push lpryszcz/redundans:v0.12b && docker push lpryszcz/redundans:latest

```
