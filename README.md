# basalt Docker images

This way you can easily try [basalt](https://github.com/basalt/basalt), use basalt without local installation or build (and in a way cross compile for Linux) on OSX or Windows.

There is a [base image](https://hub.docker.com/r/basaltbuild/base/) with just the things you need to get started with basalt, a [python image](https://hub.docker.com/r/basaltbuild/python/) with some stuff you might probably need for python projects and an image named [dajool](https://hub.docker.com/r/basaltbuild/dajool/) which uses a slightly different folder structure, that fits the needs of [dajool](http://dajool.com).

## Pulling the images from Docker Hub

```
docker pull basaltbuild/base
docker pull basaltbuild/python
```


## Building the images

1. `cd base; docker build -t basaltbuild/base .`
2. `cd ../python; docker build -t basaltbuild/python .`

Now `docker images` should list two more images: `basaltbuild/base` and `basaltbuild/python`

If you need any other development environments, just take a look at the [Python Dockerfile](https://github.com/basalt/docker_images/blob/master/python/Dockerfile) for inspiration and send me a pull request afterwards. We are still using `ubuntu:14.04.4` in our base image, since everything at dajool is still running 14.04. But this can easily be changed.

## Using the basalt Docker images

`docker run --rm -i -t -v $PWD:/src basalt/python invoke build --config configs/production.yaml`

In this example we are using the python image and `invoke build` is execute in the `src` directory of the Docker container. `src` is your mounted `PWD`, the place your `tasks.py` would be located. This way the results of the compilation won't vanish with the container. The argument `--rm` destorys the container immediately after execution, so we won't accumulate a whole pile of dead contianers.

That's it. Have fun!
