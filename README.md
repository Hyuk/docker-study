# Install Docker

### OS
Ubuntu Bionic

### Uninstall Old version
```bash
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

### Install Docker using convienent script on Linux Ubuntu Bionic
```bash
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
```

### Check Docker Version
```bash
$ sudo docker version
```

### Check if it is working
```bash
$ sudo docker run docker/whalesay cowsay Hello-World!
```

### Docker Command - run - start a container (foreground mode)
```bash
$ docker run nginx
```

### Docker Command - name - start a container with specific name(webapp)
```bash
$ docker run --name webapp nginx
```

### Docker Command - : - start a container with specific version
* if there is no tag, default value is the `latest`
```bash
$ docker run --name webapp nginx:1.14-alpine
```

### Docker Command - -i - start a container with standard input mode (interactive mode)
* without input mode, container doesn't accept users input
```bash
$ docker run -i kodekloud/simple-prompt-docker
```

### Docker Command - -it - start a container with standard input mode (interactive mode) + program questions
```bash
$ docker run -it kodekloud/simple-prompt-docker
```

### Docker command - ps - list containers
* currently working containers
```bash
$ docker ps
```
* currently working containers with stopped containers
```bash
$ docker ps -a
```

### Docker command - stop - stop a container
```bash
$ docker stop silly_sammet
```

### Docker command - rm - Remove a container
```bash
$ docker rm silly_sammet
```

### Docker command - images - List images
```bash
$ docker images
```

### Docker command - rmi - Remove images
```bash
$ docker rmi nginx
```
* if there are multiple image with different tag
```bash
$ docker rmi nginx:latest
```

### Docker command - pull - download an image
```bash
$ docker pull nginx
```

### Docker command with OS
* When starting a container with OS, it will stops right away.
```bash
$ docker run ubuntu
```
* In order to prevent OS stop right away
```bash
$ docker run ubuntu sleep 5
```

### Docker command - exec - execute a command
```bash
docker exec distracted_mcclintock cat /etc/hosts
```

### Docker command - d - detach mode (background mode)
```bash
docker run -d kodekloud/simple-webapp
```
`a043d...`

### Docker command - attach (foreground mode)
```bash
docker attach a043d
```

### Docker command - p - port
```bash
$ docker run kodekloud/webapp
```
`Running on http://0.0.0.0:5000`

```bash
$ docker run -p 80:5000 kodekloud/simple-webapp
```

```bash
$ docker run -p 83282:8080 kodekloud/simple-webapp:blue
```

### Docker command - inspect - Inspect Container
* you can check the environment variable.
```bash
$ docker inspect blissful_hopper
```

### Docker command - logs - Container Logs
```bash
$ docker logs blissful_hopper
```

### Environment Variables
* app.py
```python
import os
from flask import Flask

app = Flask(__name__)

color = os.environ.get('APP_COLOR')

@app.route("/")
def main():
  print(color)
  return render_template('hello.html', color = color)

if __name__ == "__main__":
  app.run(host="0.0.0.0", port="8080")
```
```bash
$ export APP_COLOR=blue; python app.py
```
```bash
$ docker run -e APP_COLOR=blue simple-webapp-color
```

### Start the tutorial
```bash
$ docker run -d -p 80:80 docker/getting-started
```



