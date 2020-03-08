# Deploy to Production

## Pushing Image to Docker Registry

[Docker Hub](https://hub.docker.com/)

Image naming convention: `[<registry hostname>[:port]/]<username>/<image name>[:<tag>]`

1. Build production image: `docker build -f Dockerfile.prod -t zhaqiang/docker-demo_web:prod .`
2. `docker login`

## Docker Swarm

To turn a VPS into a swarn: `docker swarm init --advertise-addr <IP address of instance>`

## docker-machine

```
$ docker-machine create --driver <cloud-service-provider> --access-token <token> <manager-machine-name>
$ docker-machine ssh <machine-name>
root@machine-name:~# docker swarm init --advertise-addr <internet-address>
root@machine-name:~# exit
$ docker-machine create --driver <cloud-service-provider> --access-token <token> <worker-machine-name>
$ docker-machine ssh <worker-machine-name> "docker swarm join --token $SWARM_TOKEN $MANAGER_INTERNAL_IP:2337"
$ eval $(docker-machine env <manager-machine-name>)
$ docker stack deploy -c docker-stack.yml docker-demo_web
```

## Scaling the App

```
docker service scale docker-demo_web=3
```
