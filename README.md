# Docker builds

## alpine-bash
Trying to build minimal image for [Redundans](https://github.com/lpryszcz/redundans).
But cannot build even biopython / numpy. 

## redundans
Image for [Redundans](https://github.com/lpryszcz/redundans).

```bash
cd redundans
docker build -t lpryszcz/redundans:v0.111b .

# alias
docker tag -f lpryszcz/redundans:v0.111b lpryszcz/redundans:latest

# push
git push lpryszcz/redundans:latest

```
