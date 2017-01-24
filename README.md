# Docker builds

## redundans_alpine
Trying to build minimal image for [Redundans](https://github.com/lpryszcz/redundans).
But cannot build biopython. 

```bash
# build latests
cd redundans_alpine
docker build --pull --no-cache --force-rm -t lpryszcz/redundans:v0.12b_alpine .

# alias
#docker tag -f lpryszcz/redundans:v0.12b_alpine lpryszcz/redundans:latest

# test
docker run -it -w /root/src/redundans lpryszcz/redundans:v0.12b_alpine ./redundans.py -v -i test/{600,5000}_{1,2}.fq.gz -f test/contigs.fa -o test/run1

# push
docker push lpryszcz/redundans:v0.12b_alpine #&& docker push lpryszcz/redundans:latest

```


## redundans
Ubuntu-based (~150Mb) image for [Redundans](https://github.com/lpryszcz/redundans).

```bash
# build latest
cd redundans
docker build --pull --no-cache --force-rm -t lpryszcz/redundans:v0.13a .

# alias
docker tag -f lpryszcz/redundans:v0.13a lpryszcz/redundans:latest

# test (already in build)
# docker run -it -w /root/src/redundans lpryszcz/redundans ./redundans.py -v -i test/{600,5000}_{1,2}.fq.gz -f test/contigs.fa -o test/run1

# push
docker push lpryszcz/redundans:v0.13a && docker push lpryszcz/redundans:latest

# microbadger update - maintained through webhooks https://hub.docker.com/r/lpryszcz/redundans/~/settings/webhooks/
#curl --data "info=update" https://hooks.microbadger.com/images/lpryszcz/redundans/X0g8hB_GwLqt2094hbnYfwDOYks=

```
