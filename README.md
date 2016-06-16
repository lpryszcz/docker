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
docker push lpryszcz/redundans:v0.12b && docker push lpryszcz/redundans:latest

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
