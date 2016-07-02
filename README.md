# basalt Docker images

This way you can easily try [basalt](https://github.com/basalt/basalt), use basalt without local installation or build (and in a way cross compile for Linux) on OSX or Windows.

The images are not yet published on Docker hub, therefore you need to clone the repo. At the moment there is a base image with just the things you need to get started with basalt, a python image with some stuff we need for our python projects and an image named dajool which uses a slightly different folder structure, that fit the needs of [dajool](http://dajool.com).

## Building the images

1. `cd base; docker build -t basalt/base .`
2. `cd ../python; docker build -t basalt/python .`

Now `docker images` should list two more images: `basalt/base` and `basalt/python`

If you need any other development environments, just take a look at the [Python Dockerfile](https://github.com/basalt/docker_images/blob/master/python/Dockerfile) for inspiration and send me a pull request afterwards. We are still using `ubuntu:14.04.4` in our base image, since everything at dajool is still running 14.04. But this can easily be changed.

## Using the basalt Docker images

`docker run --rm -i -t -v ~/my_repos/my_sources:/src basalt/python make build`

In this example we are using the python image and `make build` is execute in the `src` directory of the Docker container. `src` is your mounted local folder `my_sources`. This way the results of the compilation won't vanish with the container. The argument `--rm` destorys the container immediately after execution, so we won't accumulate a whole pile of dead contianers.

That's it. Have fun!
