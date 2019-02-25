# docker-3dtk

There is an image in DockerHub at `chbrandt/3dtk`.

## Run
Example from a Linux host, with access to container's Xorg:
```bash
$ docker run --rm -it -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix:0 chbrandt/3dtk
```

### Test 3DTK
```bash
$ cp -v -R /slam6d-code/dat .
# ...
$ slam6D dat
# ...
$ show dat
```

## Build
If you want to build on your own:
```bash
$ cd docker-3dtk/dockerfile
$ docker build -t 3dtk_container .
```

/.\
