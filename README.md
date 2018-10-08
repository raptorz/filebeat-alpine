## This project is forked from [filebeat-alpine](https://github.com/easonlau02/filebeat-alpine) and added version 6.4.1

* only 38M(6.4.1)
* customizable configuration
* built image: [raptor/filebeat](https://hub.docker.com/r/raptor/filebeat/)

## Basic usage

1. default config

The log files place in the following path：

```
PATH/[app_name]/logs/*.log
```

and mount volume：

```
volumes:
  - PATH:/home/user/ 
```

2. customize config：

mount the config file path by volume：

```
volumes:
  - /path_to_filebeat_yml:/etc/filebeat
```

The customized `filebeat.yml` is placed in `path_to_filebeat_yml`.

Caution: `filebeat.yml` must be owned by `root.root` and attribute is `rw-r--r--`.

## 本项目源于 [filebeat-alpine](https://github.com/easonlau02/filebeat-alpine) ，增加了6.4.1版本。

* 仅38M(6.4.1)
* 可修改配置
* 已发布到dockerhub：[raptor/filebeat](https://hub.docker.com/r/raptor/filebeat/)

## 基本用法

1. 默认配置：

日志文件放在如下路径：

```
PATH/[app_name]/logs/*.log
```

将路径作如下映射：

```
volumes:
  - PATH:/home/user/ 
```

2. 自定义配置：

自定义配置文件作如下映射：

```
volumes:
  - /path_to_filebeat_yml:/etc/filebeat
```

其中`path_to_filebeat_yml`是存放自定义的`filebeat.yml`的路径。

注意：自定义的`filebeat.yml`必须是属于`root.root`用户，并且属性为`rw-r--r--`。

## Why to use [filebeat-alpine](https://github.com/easonlau02/filebeat-alpine)
> filebeat with alpine, more tiny, more lighter, only 16M disk cost.

## Supported tags and respective `Dockerfile` links
-	[`5.3.1` (*Dockerfile*)](https://github.com/easonlau02/filebeat-alpine/blob/master/5.3.1/Dockerfile)
-	[`5.6.3` (*Dockerfile*)](https://github.com/easonlau02/filebeat-alpine/blob/master/5.6.3/Dockerfile)
-	[`6.1.1` (*Dockerfile*)](https://github.com/easonlau02/filebeat-alpine/blob/master/6.1.1/Dockerfile)

### Certainly, you have better to clone this git to your local for convenience.
```
git clone https://github.com/easonlau02/filebeat-alpine.git
```
### Something to know when using [eason02/filebeat-alpine](https://hub.docker.com/r/eason02/filebeat-alpine/)
1. Make sure your application log path need to follow below or link to below path.
```
PATH/application/logs/*.log
```

2. And change [docker-compose file](https://github.com/easonlau02/filebeat-alpine/blob/master/docker-compose.yml)
```
volumes:
  - PATH:/home/user/ 
```

Will auto-scan your log folder by this path: `PATH/`*/`logs`/`*.log`

3. Run via docker-compose
```
docker-compose up -d
```

4. docker ps | grep filebeat-alpine
```
CONTAINER ID        IMAGE                           COMMAND                  CREATED             STATUS              PORTS               NAMES
8b7a1d8a35c0        eason02/filebeat-alpine:5.3.1   "filebeat -e filebeat"   18 seconds ago      Up 17 seconds                           filebeat-alpine-5.3.1
```

## 为什么使用 [filebeat-alpine](https://github.com/easonlau02/filebeat-alpine)
> 结合微服务和容器化的思想，将无关的、无用的资源去掉，封装成一个单一，纯净的image镜像，使用当前最轻量级的OS-alpine来封装filebeat，更轻量级，大小只有16M左右，方便快速启动

### 当然，建议你将本git folder clone到你的本地方便后面启动service
```
git clone https://github.com/easonlau02/filebeat-alpine.git
```
### 使用[eason02/filebeat-alpine](https://hub.docker.com/r/eason02/filebeat-alpine/)，一些你需要配置的properties
1. 确保你的日志文件在如下的路径格式中，其中PATH需要做docker-compose配置的，application这一层可以有很多的app name，每个app folder下面有一个叫做logs的folder，然后下面才是具体的*.log文件
```
PATH/application/logs/*.log
```

2. 用上面的PATH来修改 [docker-compose file](https://github.com/easonlau02/filebeat-alpine/blob/master/docker-compose.yml)
```
volumes:
  - PATH:/home/user/ 
```

filebeat会通过如下的路径自动扫描日志: `PATH/`*/`logs`/`*.log`

3. 使用docker-compose启动
```
docker-compose up -d
```

4. docker ps | grep filebeat-alpine
```
CONTAINER ID        IMAGE                           COMMAND                  CREATED             STATUS              PORTS               NAMES
8b7a1d8a35c0        eason02/filebeat-alpine:5.3.1   "filebeat -e filebeat"   18 seconds ago      Up 17 seconds                           filebeat-alpine-5.3.1
```
