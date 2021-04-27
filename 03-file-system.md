# File system

/var/lib/docker
  /aufs
  /containers
  /image
  /volumes

### Layered architecture
```docker
FROM Ubuntu

RUN apt-get update && apt-get -y install python

RUN pip install flask flask-mysql

COPY . /opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```

```bash
$ docker build Dockerfile -t mmumshad/my-custom-app
```

```docker
FROM Ubuntu

RUN apt-get update && apt-get -y install python

RUN pip install flask flask-mysql

COPY app2.py /opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app2.py flask run
```

```bash
$ docker build Dockerfile2 -t mmumshad/my-custom-app-2
```

### volumes
```bash
$ docker volume create data_volume
```

/var/lib/docker
  /volumes
    /data_volumes

```bash
$ docker run -v data_volume:/var/lib/mysql mysql
$ docker run -v data_volume2:/var/lib/mysql mysql
$ docker run -v /data/mysql:/var/lib/mysql mysql
$ docker run --mount type=bind,source=/data/mysql,target=/var/lib/mysql mysql
```

### Storage Drivers
* AUFS
* ZFS
* BTRFS
* Device Mapper
* Overlay
* Overlay2