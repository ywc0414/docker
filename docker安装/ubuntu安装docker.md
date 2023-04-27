###### 卸载旧版本

```java
apt-get remove docker docker-engine docker.io containerd runc
```

###### 更新安装依赖

```java
apt-get update
```

###### 安装依赖包

```java
apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
software-properties-common
```

###### 安装秘钥

```java
curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
```

###### 设置docker源（阿里云）

```java
add-apt-repository \
   "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

###### 更新安装依赖

```java
apt-get update
```

###### 查看仓库中所有docker版本

```java
apt-cache madison docker-ce
```

###### 安装docker

```java
apt install docker-ce docker-ce-cli containerd.io
```

> 也可以安装指定版本
>
> apt install docker-ce<version> docker-ce-cli<version> containerd.io
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