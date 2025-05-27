# idea 开发环境配置


# 安装 wsl
- [wsl](https://docs.microsoft.com/zh-cn/windows/wsl/install) wsl
```

```

# 安装 docker
```
# 安装 docker desktop
- [docker desktop](https://www.docker.com/products/docker-desktop)

# 编程工具
- [阿里云 maven 仓库](https://developer.aliyun.com/mvn/guide) 阿里云 maven 仓库
- [配置 docker 镜像加速器](https://www.runoob.com/docker/docker-mirror.html) 配置 docker 镜像加速器
```
{
    "registry-mirrors": [
        "https://docker.1ms.run"
    ]
}
```

## mysql 8.0  客户端链接不上 
```
方法一：修改 DBeaver 连接设置
在 DBeaver 中打开你的 MySQL 连接配置
转到 "驱动属性" 或 "连接属性" 标签页
添加或修改以下属性：
allowPublicKeyRetrieval = true
useSSL = false (如果不需要 SSL)
```
