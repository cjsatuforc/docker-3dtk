# docker-3dtk

## Run

Example from a Linux host, with Xorg:
```bash
$ docker run --rm -it -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix:0 chbrandt/3dtk
```

## Test 3DTK
```bash
$ cp -v -R /slam6d-code/dat .
# ...
$ slam6D dat
# ...
$ show dat
```

