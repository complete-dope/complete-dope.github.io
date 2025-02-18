---
layout: post
title: Learning Docker
date : 2024-09-07
---

## Docker Commands end to end 

* **docker run** - Run a container from an image
* **docker start** - Start a container that has been stopped
* **docker stop** - Stop a running container
* **docker kill** - Kill a running container
* **docker rm** - Remove a container    


### Docker in interactive mode

Here this `-i` is the interactive mode but this looks like shit !! 
```
docker run -i image_name /bin/bash
```

So we need to attach the -t ( tty ) to it to look good and usable
```
docker run -it image_name /bin/bash 
```


### Docker in detached mode

```bash
docker run -d image_name
```

## 







