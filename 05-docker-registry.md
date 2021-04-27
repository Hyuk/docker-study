# Docker Registry

```bash
$ docker run -d -p 5000:5000 --name registry registry:2
```

```bash
$ docker image tag my-image localhost:5000/my-image
```

```bash
$ docker push localhost: 5000/my-image
```

```bash
$ docker pull localhost:5000/my-image
```

```bash
$ docker pull 192.168.56.100:5000/my-image
```