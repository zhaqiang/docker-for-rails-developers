# Deploy to Production

## Pushing Image to Docker Registry

[Docker Hub](https://hub.docker.com/)

Image naming convention: `[<registry hostname>[:port]/]<username>/<image name>[:<tag>]`

1. Build production image: `docker build -f Dockerfile.prod -t zhaqiang/docker-demo_web:prod .`
2. `docker login`
