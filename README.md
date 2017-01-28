# Live CV Docker files

### Building a docker image:

```
sudo docker build -t livecv/launcher-test .
```

### Running image:

```
docker run -t -i -p 5900 -v /<local_livecv_path>:/<remove_livecv_path> livecv
```

### Connecting to an image:

The image uses vnc to display live cv. Use a vnc viewer like vinagre to view the images display port.
The display port is available in docker's container list:

```
docker ps
```
