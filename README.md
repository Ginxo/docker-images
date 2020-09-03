# Docker images (just that)
this is a bunch of docker images, not related between each other by anything, they are just docker images, if you try to find any sense here, stop it! This is just a container of possible future containers (man!! what a joke I already made!!)

# How to use them
browse to any folder from here and run `docker build . -t whatevertagyouwatntoprovide` once they are built they should behave like any other docker image with its docker image things...
Once the image is created you run something like
`docker run -it --ulimit nofile=262144:262144 --entrypoint /bin/bash IMAGE_ID`