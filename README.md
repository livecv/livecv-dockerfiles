# Live CV Docker files

### Building a docker image:

Building livecv launcher test imge

```
sudo docker build -t livecv/launcher-test .
```

### Running image:

```
docker run -t -i -p 5900 -v /path/to/livecv:/livecv livecv
```

### Connecting to an image:

The image uses vnc to display live cv. Use a vnc viewer like vinagre to view the images display port.
The display port is available in docker's container list:

```
docker ps
```
