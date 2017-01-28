# Live CV Docker files

The 2 images are used to test the standalone version of livecv (launcher based) and the minimal 
version for compatibility issues.

### Building the docker images:

Building livecv launcher test image: 

```
cd livecv-launcher-test
sudo docker build -t livecv/launcher-test .
```

Building livecv test image:

```
cd livecv
sudo docker build -t livecv/test .
```

### Running an image:

```
docker run -t -i -p 5900 -v /<local_livecv_path>:/<remove_livecv_path> livecv/launcher-test
```

### Connecting to an image:

The image uses vnc to display live cv. Use a vnc viewer like vinagre to view the images display port.
The display port is available in docker's container list:

```
docker ps
```
