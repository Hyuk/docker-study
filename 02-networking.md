# Networking

* Bridge
* none
* host

### Bridge
```bash
$ docker run Ubuntu
```

### none
```bash
$ docker run Ubuntu --network=none
```

### host
```bash
$ docker run Ubuntu --network=host
```

### Inspect Network
```bash
$ docker inspect blissful_hopper
```

### Embeded DNS
```
mysql.connect(mysql)
```