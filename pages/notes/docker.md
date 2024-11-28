# Docker 安装
# docker
- [IT Tools - Handy online tools for developers](http://192.168.16.128:8010/)
- [Memos](http://192.168.16.128:8011/)
- [Jellyfin](http://192.168.16.128:8012/web/)
- [Excalidraw | Hand-drawn look & feel • Collaborative • Secure](http://192.168.16.128:8013/)
- [Hello 算法](https://www.hello-algo.com/)
- [DockerDesktop使用指南_笔记大全_设计学院](https://www.python100.com/html/99002.html)
- [Overview of Docker Desktop | Docker Documentation](https://docs.docker.com/desktop/)
- [docker 命令](https://docs.docker.com/engine/reference/commandline/rmi/)
- [Docker: Accelerated Container Application Development](https://www.docker.com/)

## 卸载旧版本
``` shell
sudo yum remove docker \
    docker-client \
    docker-client-latest \
    docker-common \
    docker-latest \
    docker-latest-logrotate \
    docker-logrotate \
    docker-engine \
    docker-selinux
sudo rm -rf /var/lib/docker
sudo rm -rf /etc/docker
# sudo rm -rf /etc/yum.repos.d/*        

sudo yum install docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
                
```
## yum 安装
```shell
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
sudo yum-config-manager \
    --add-repo
    http://mirrors.aliyun.com/repo/Centos-7.repo
sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
# sudo yum install docker-ce docker-ce-cli containerd.io
# sudo systemctl start docker
# sudo docker run hello-world
```

## Docker 镜像加速器 
也可以加载国内其他镜像源，部分国内镜像源地址如下：
- [阿里云](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)
- [DaoCloud](https://www.daocloud.io/mirror#accelerator-doc)
- [网易云](https://hub-mirror.c.163.com)
- [腾讯云](https://cloud.tencent.com/document/product/457/9107)
- [七牛云](https://kcrm.ksserver.cn:8443/#/image-repo)
- [中科大](https://mirrors.ustc.edu.cn/help/dockerhub.html)
- [阿里云](https://www.aliyun.com/product/acr?source=5176.11533457&userCode=8lx5zmtu)
部分镜像源已经下线，无法使用，请使用其他镜像源。

```shell
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://register.liberx.info"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

- [register search](https://register.liberx.info/)


## 运行 mysql
```shell
docker run -d -p 3306:3306 --name mysql -v /data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 mysql
```

docker run --name=mysql -it  \
-p 3306:3306  \
-e MYSQL_ROOT_PASSWORD=123456  \
-e MYSQL_ROOT_HOST=%  \
-v /data/mysql:/var/lib/mysql  \
-d 56a8c14e1404

## 运行 redis
下一步就是使用run命令创建并启动镜像，但在启动镜像之前，我们需要去官网下载redis的配置文件redis.conf文件。注意不同版本的redis配置文件内容不一样
- [redis-conf](https://redis.io/docs/latest/operate/oss_and_stack/management/config/) redis config 配置文件
```shell
docker run -d -p 6379:6379 --name redis -v /data/redis/redis.conf:/usr/local/etc/redis/redis.conf -v /data/redis/data:/data redis:latest redis-server /usr/local/etc/redis/redis.conf
```













## 其他

Docker 是一个开源的应用容器引擎，它允许开发者打包他们的应用以及依赖包到一个可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。容器是完全使用沙箱机制，相互之间不会有任何接口。

启动 Docker 服务通常取决于你使用的操作系统。以下是一些常见操作系统上启动 Docker 服务的方法：

### 对于 Linux 系统：

大多数现代的 Linux 发行版使用 `systemd` 来管理系统服务。你可以使用以下命令来启动 Docker 服务：

```bash
sudo systemctl start docker
```

如果你想让 Docker 在系统启动时自动启动，可以使用以下命令来启用它：

```bash
sudo systemctl enable docker
```

### 对于 Windows 系统：

在 Windows 上，Docker 通常作为一个后台服务运行。如果你使用的是 Docker Desktop for Windows，你可以通过 Docker Desktop 的图形界面来启动 Docker 服务。通常，当你打开 Docker Desktop 应用程序时，它会自动启动 Docker 服务。

如果你需要从命令行启动 Docker 服务，可以使用 PowerShell 作为管理员，并运行：

```powershell
Start-Service docker
```

### 对于 macOS 系统：

在 macOS 上，Docker 也作为一个后台服务运行，通常通过 Docker Desktop for Mac 来管理。打开 Docker Desktop 应用程序时，Docker 服务会自动启动。

如果你需要从命令行启动 Docker 服务，可以使用以下命令：

```bash
brew services start docker
```

或者，如果你使用的是 Docker Desktop 的早期版本，你可能需要使用以下命令：

```bash
open /Applications/Docker.app
```

这将打开 Docker Desktop 应用程序，Docker 服务将随之启动。

请注意，如果你的 Docker 服务没有按预期启动，可能需要检查 Docker 的日志以确定问题所在。在 Linux 上，你可以使用以下命令查看 Docker 的日志：

```bash
sudo journalctl -u docker.service
```

或者，如果你使用的是较旧的系统，可能需要查看 `/var/log/docker.log` 文件。

如果你遇到任何问题，可以提供更多的信息，以便我能提供更具体的帮助。


以下是一些基本的 Docker 命令来启动容器：

1. **启动一个新的容器**：
   ```bash
   docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
   ```
   例如，启动一个基于 `nginx` 镜像的容器：
   ```bash
   docker run --name some-nginx -d nginx
   ```
   这里 `--name some-nginx` 给容器指定一个名称，`-d` 表示在后台运行。

2. **启动一个已经存在的容器**：
   如果容器已经创建但未运行，可以使用以下命令启动：
   ```bash
   docker start [OPTIONS] CONTAINER [CONTAINER...]
   ```
   例如，启动名为 `some-nginx` 的容器：
   ```bash
   docker start some-nginx
   ```

3. **列出正在运行的容器**：
   ```bash
   docker ps
   ```
   这将显示所有正在运行的容器。

4. **列出所有容器**（包括未运行的）：
   ```bash
   docker ps -a
   ```

5. **查看容器日志**：
   要查看容器的日志，可以使用：
   ```bash
   docker logs [OPTIONS] CONTAINER
   ```
   例如：
   ```bash
   docker logs some-nginx
   ```

6. **进入正在运行的容器**：
   如果你需要进入容器内部，可以使用：
   ```bash
   docker exec -it CONTAINER COMMAND
   ```
   例如，进入 `some-nginx` 容器并使用 bash：
   ```bash
   docker exec -it some-nginx bash
   ```

7. **停止容器**：
   要停止一个正在运行的容器，可以使用：
   ```bash
   docker stop CONTAINER
   ```

请根据你的具体需求选择合适的命令。如果你需要更详细的帮助或有特定的 Docker 镜像和配置需求，可以提供更多的信息。
