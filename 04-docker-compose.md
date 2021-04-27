# Docker Compose

```bash
$ docker run mmumshad/simple-webapp
$ docker run mongodb
$ docker run redis:alpine
$ docker run ansible
```

* docker-compose.yml
```yml
services:
  web:
    image: "mmumshad/simpole-webapp"
  database:
    image: "mongodb"
  messaging:
    image: "redis:alpine"
  orchestration:
    image: "ansible"
```

```bash
$ docker-compose up
```

```bash
$ docker run -d --name=redis redis
$ docker run -d --name=db postgres:9.4
$ docker run -d --name=vote -p 5000:80 --link redis:redis voting-app
$ docker run -d --name=result -p 5001:80 --link db:db result-app
$ docker run -d --name=worker --link db:db --link redis:redis worker
```

* docker-compose.yml
```yml
services:
  redis:
    image: redis
  db:
    image: postgres:9.4
  vote:
    image: voting-app
    ports:
      - 5000:80
    links:
      - redis
  result:
    image: result-app
    ports:
      - 5001:80
    links:
      - db
  worker:
    image: worker
    links:
      - redis
      - db
```

```bash
$ docker-compose up
```

* docker-compose.yml
```yml
services:
  redis:
    image: redis
  db:
    image: postgres:9.4
  vote:
    image: ./vote
    ports:
      - 5000:80
    links:
      - redis
  result:
    image: ./result
    ports:
      - 5001:80
    links:
      - db
  worker:
    image: ./worker
    links:
      - redis
      - db
```

* docker-compose.yml
```yml
redis:
  image: redis
db:
  image: postgres: 9.4
vote:
  image: voting-app
  ports:
    - 5000:80
  links:
    - redis
```

* docker-compose.yml
```yml
version: 2
services:
  redis:
    image: redis
  db:
    image: postgres:9.4
  vote:
    image: voting-app
    ports:
      - 5000:80
    depends_on:
      - redis
```

* docker-compose.yml
```yml
version: 3
services:
  redis:
    image: redis
  db:
    image: postgres:9.4
  vote:
    image: voting-app
    ports:
      - 5000:80
```

* docker-compose.ytml
```yml
version: 2
services:
  redis:
    image: redis
    networks:
      - back-end
  db:
    image: postgres:9.4
    networks:
      - back-end
  vote:
    image: voting-app
    networks:
      - front-end
      - back-end
  result:
    image: result
    networks:
      - front-end
      - back-end
networks:
  front-end:
  back-end:
```