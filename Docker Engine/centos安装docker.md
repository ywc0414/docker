###### 卸载旧版本的docker

```java
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

###### 安装yum-uitls工具

```java
yum install -y yum-utils
```

###### 设置docker的yum源（阿里云）

```java
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

###### 查看仓库中所有docker版本

```java
yum list docker-ce --showduplicates | sort -r
```

###### 安装docker

```java
yum install docker-ce docker-ce-cli containerd.io
```

> 也可以安装指定版本
>
> yum install docker-ce<version> docker-ce-cli<version> containerd.io
>

###### 配置镜像加速及修改默认存储路径

docker的默认存储路径：/var/lib/docker

创建daemon.json：vim /etc/docker/daemon.json

```java
{ 
    "registry-mirrors": ["https://23evy2ba.mirror.aliyuncs.com"], # 阿里云的镜像加速地址
    "data-root": "/home/docker" # 设置docker的默认存储路径     
}
```

> 重新加载配置并启动docker
>
> systemctl daemon-reload
>
> systemctl start docker
>
> systemctl enable docker

###### docker的常用命令

>设置docker开机自启动：docker 
>
>进入容器内：docker exec -it id/name bash
>
>查看容器所有信息：docker inspect id/name 
>
>查看容器进程：docker top id/name
>
>查看容器端口：docker port id/name 
>
>查看容器IP：docker exec -it id/name ip addr
>
>查看容器资源使用情况：docker stats
>
>查看容器网路情况：docker network ls