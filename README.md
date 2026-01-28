# C++ "Hello, World!"

This directory contains a C++-based "Hello, World!" example running on Unikraft.

## Set Up

This requires Docker to work. If Docker is not installed, can do this on Ubuntu:
```bash
sudo apt-get update
sudo apt-get install -y docker.io
sudo usermod -aG docker $USER
newgrp docker
sudo systemctl enable --now docker
```

## Run and Use

Use `kraft` to run the image and start a Unikraft instance:

```bash
newgrp docker
docker ps # just to check if returns docker column names
kraft run
```

Once executed, you should see a "Bye, World!" message.

## Inspect and Close

To list information about the Unikraft instance, use:

```bash
kraft ps
```

```text
NAME            KERNEL                          ARGS         CREATED        STATUS   MEM  PORTS  PLAT
elastic_goblin  oci://unikraft.org/base:latest  /helloworld  9 seconds ago  running  64M         qemu/x86_64
```

The instance name is `elastic_goblin`.
To close the Unikraft instance, close the `kraft` process (e.g., via `Ctrl+c`) or run:

```bash
kraft rm elastic_goblin
```

Note that depending on how you modify this example your instance **may** need more memory to run.
To do so, use the `kraft run`'s `-M` flag, for example:

```bash
kraft run --rm --plat qemu --arch x86_64 -M 256M .
```

## `kraft` and `sudo`

Mixing invocations of `kraft` and `sudo` can lead to unexpected behavior.
Read more about how to start `kraft` without `sudo` at [https://unikraft.org/sudoless](https://unikraft.org/sudoless).

## Learn More

- [How to run unikernels locally](https://unikraft.org/docs/cli/running)
- [Building `Dockerfile` Images with `BuildKit`](https://unikraft.org/guides/building-dockerfile-images-with-buildkit)
