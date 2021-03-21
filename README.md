# Description

Plain django init project.

# Instructions

```bash
$ docker-compose -f devops/docker/docker-compose.yaml build --build-arg USER=1000 --build-arg GROUP=1000
$ docker-compose -f devops/docker/docker-compose.yaml up
$ docker-compose -f devops/docker/docker-compose.yaml down
```

Visit app at [localhost:8000](http://localhost:8000)