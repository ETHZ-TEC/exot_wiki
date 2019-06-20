To encapsulate the required tools for building C and C++ based projects, the library provides a [Docker](https://docs.docker.com)-based container. It's based on the latest Ubuntu LTS, and supports cross-compiling for x86_64, aarch64, and 32-bit arm architectures with soft and hard floating-point implementations.

> *Note:* At the moment the images have to be built locally. Pulling directly from git should be quite straightforward, but would require some minor manual changes to the host script.

The script running on the host and the entrypoint script running inside the container were inspired by [sdt/docker-raspberry-pi-cross-compiler](https://github.com/sdt/docker-raspberry-pi-cross-compiler). The main idea is to have a script which passes all commands and arguments to the container, which runs them with the host's UID, GID, username and group. Thanks to that, there are no permission/access issues on the host's side. The [host script](src/host-script.sh) mounts the host's current working directory inside the container.

Additionally, a number of CMake toolchains are available inside the container for further convenience. These are available for targets **x86_64**, **aarch64**, **arm**, and **armhf**, in **basic** (dynamic linkage), **static** (static linkage), and **rpath** (dynamic linkage with current directory set as runtime load path) configurations. These are available in the container at `/tool/{basic,static,rpath}/{x86_64,aarch64,arm,armhf}.cmake`.

## How to build?

Firstly, to build and use the images the docker engine is required. Follow the [guides](https://docs.docker.com/install/) available on Docker's documentation website.[^1] For convenience, one can use the Docker's installation script from https://get.docker.com. Additional [post-installation steps](https://docs.docker.com/install/linux/linux-postinstall/) might be useful on Linux, for example to allow executing Docker commands without root privileges. make sure that docker is running before proceeding with installation.

To build the container images, clone the repository and navigate to the folder in which this README is contained, and use `make`. The contained [Makefile](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/tools/docker/Makefile) defines the following rules:

- __*base*: build the base image__,
- __*scripted*: build the extended image, depends on *base*__,
- *host-script*: create a the script to run commands in the *scripted* container, depends on *host-script-config*,
- *host-script-config*: create a config file for the script above,
- *echo-script*: echo the script to stdout,
- *clean*: clean the script and config files,
- *delete-images*: delete docker images created using the script.

The following variables, defined in the Makefile, can be used to customise the configuration:

- `NAMESPACE`: the namespace with which the images will be tagged, default: *tooling*;
- `IMAGE_BASE`: the name of the base image, default: *base*;
- `IMAGE_SCRIPTED`: the name of the image with extended user-scripting support, default: *dock*;
- `IMAGE_TAG`: the tag which will be used during the build, default: *latest*.

During build time, the *base* image will report the installed versions of the contained tools. When building the *scripted* some further information will be displayed.

## How to use?

After building the image using the *scripted* rule, a special script will be created. For the sake of convenience, the script can be copied somewhere in the user's PATH.

Assuming that the created script was called *dock*, one can, for example, build a CMake project by running on the host machine:

```sh
dock cmake -DCMAKE_TOOLCHAIN_FILE=/tool/static/x86_64.cmake -DCMAKE_BUILD_TYPE=Debug -B build/linux-amd64 -H.
dock cmake --build build/linux-amd64 --target <target>
```

To output the version info of the installed compilers and tools, run:

```sh
dock /setup/print-env.sh
```

To get a shell inside the container, one can run:

```sh
dock /usr/bin/env bash
```

To bypass the entrypoint script in the *scripted* or to get a shell in the *base* container, on create a docker container manually (assumes images *tooling/base* and *tooling/dock*):

```sh
docker run --interactive --tty --rm tooling/base /bin/bash
# or
docker run --interactive --tty --rm --entrypoint /bin/bash tooling/base
# or
docker run --interactive --tty --rm --entrypoint /bin/bash tooling/dock
```

---

[^1]: Guidelines for Ubuntu 18.04 are also available at https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04.
