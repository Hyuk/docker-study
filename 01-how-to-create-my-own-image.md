# How to create my own image?

```docker
FROM Ubuntu

RUN apt-get update
RUN apt-get install python

RUN pip install flask
RUN pip install flask-mysql

COPY . /opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```

```bash
$ docker build Dockerfile -t mmumshad/my-custom-app
$ docker push mmumshad/my-custom-app
```

### prevent ubuntu image stop
```docker
FROM Ubuntu

CMD sleep 5
```

```bash
$ docker build -t ubuntu-sleeper

$ docker run ubuntu-sleeper
```

```bash
$ docker run ubuntu-sleeper sleep 10
```

```docker
FROM Ubuntu

ENTRYPOINT ["sleep"]
```

```bash
$ docker run ubuntu-sleeper 10
```

```docker
FROM Ubuntu

ENTRYPOINT ["sleep"]

CMD ["5"]
```

* Command at Startup: sleep 5
```bash
$ docker run ubuntu-sleeper
```

* Command at Startup: sleep 10
```bash
$ docker run ubuntu-sleeper 10
```

* Command at Startup: sleep2.0 10
```bash
$ docker run --entrypoint sleep2.0 ubuntu-sleeper 10
```

