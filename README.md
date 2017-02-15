# basalt Docker images

This way you can easily try [basalt](https://github.com/basalt/basalt) without a local installation or build (and in a way cross compile for Linux) on OSX or Windows.

At the moment you can find base images for [Ubuntu 14.04](https://hub.docker.com/r/basaltbuild/ubuntu1404_base/) and [Debian 8 (Jessie)](https://hub.docker.com/r/basaltbuild/debian8_base/). Those two include everything you neet to get started with basalt packaging. If you need e.g. Python to build your package, you can take a Look at the [Ubuntu 14.04 Python image](https://hub.docker.com/r/basaltbuild/ubuntu1404_python/).

## Pulling the images from Docker Hub

```
docker pull basaltbuild/base
docker pull basaltbuild/python
```


## Building the images

1. `cd base; docker build -t basaltbuild/debian8_base .`
2. `cd ../python; docker build -t basaltbuild/debian8_python .`

Now `docker images` should list two more images: `basaltbuild/debian8_base` and `basaltbuild/debian8_python`

If you need any other development environments, just take a look at e.g. the [Debian 8 (Jessie) Python Dockerfile](https://github.com/basalt/docker_images/blob/master/debian8/python/Dockerfile) for inspiration and send me a pull request afterwards.

## Using the basalt Docker images

`docker run --rm -i -t -v $PWD:/src basaltbuild/debian8_python invoke build --config configs/production.yaml`

In this example we are using the Debian 8 (Jessie) Python image and `invoke build` is execute in the `src` directory of the Docker container. `src` is your mounted `PWD`, the place your `tasks.py` would be located. This way the results of the compilation won't vanish with the container. The argument `--rm` destorys the container immediately after execution, so we won't accumulate a whole pile of dead contianers.

That's it. Have fun!
