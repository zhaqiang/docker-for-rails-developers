# Docker Commands

## docker run

```
docker run ruby:2.6 ruby -e "puts :hello"
```

`docker run [OPTIONS] IMAGE [COMMAND] [ARG...]`: Run a command in a new container.

man: `docker help run`

### Rails commands

```
docker-compose run --rm web bin/rails db:create
docker-compose exec web bin/rails g scaffold User first_name last_name
docker-compose exec web bin/rails db:migrate
```

## docker ps

```
docker ps -a
```

列出所有 containers，包括停止了的。

## docker rm

```
docker rm [OPTIONS] CONTAINER-ID [CONTAINER-ID...]
```

删除 containers。

一次性执行并删除容器，运行时加上 `--rm` 参数：

```
docker run --rm ruby:2.6 ruby -e "puts :hello"
```

## 交互式容器

```
docker run -i -t --rm -v ${PWD}:/usr/src/app ruby:2.6 bash
```

- `-i`: keep STDIN open
- `-t`: allocate a pseudo-TTY (set up a terminal emulator)
- `-v ${PWD}:/usr/src/app`: mount current dir inside the container at `/usr/src/app`

创建 Rails app：

```
cd /usr/src/app
gem install rails
rails new docker-demo --skip-test --skip-bundle
```

## docker build

```
docker build [OPTIONS] PATH | URL | -
```

Build an image from a Dockerfile.

## docker images

List images.

## docker run rails

```
docker run -p 3000:3000 CONTAINER-ID bin/rails s -b 0.0.0.0
```

## docker tag

```
docker tag CONTAINER-ID NAME[:TAG]
```

## docker-compose up

```
docker-compose up -d
```

## docker-compose ps

## docker-compose [stop|start|restart] SERVICE-NAME

## docker-compose run

```
run [options] [-v VOLUME...] [-p PORT...] [-e KEY=VAL...] [-l KEY=VALUE...] SERVICE [COMMAND] [ARGS...]
```

Run a one-off command on a service.

Example: `docker-compose run --rm redis redis-cli -h redis`

## docker-compose up

```
docker-compose up -d SERVICE-NAME
```

## docker-compose logs -f SERVICE-NAME

## docker-compose exec SERVICE-NAME COMMAND

## docker-compose down

## docker-compose prune

## docker system prune

Free up all resources.

## docker network ls

## docker-compose rm

```
docker-compose rm [options] [SERVICE...]
```

Removes stopped service containers.
