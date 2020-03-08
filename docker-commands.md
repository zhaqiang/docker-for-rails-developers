# Docker Commands

## docker run

```
docker run ruby:2.6 ruby -e "puts :hello"
```

`docker run [OPTIONS] IMAGE [COMMAND] [ARG...]`: Run a command in a new container.

man: `docker help run`

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
