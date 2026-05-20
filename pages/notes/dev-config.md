# idea 开发环境配置

# git 配置代理
```
git config --global http.proxy http://127.0.0.1:10809
```



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

- [基于 Vue3 + Vite + TypeScript + Element-Plus 从0到1搭建后台管理系统](https://blog.csdn.net/u013737132/article/details/130191394)

- [ESLint+Prettier+Stylelint+EditorConfig 约束和统一前端代码规范](https://blog.csdn.net/u013737132/article/details/130190788)
- [Husky + Lint-staged + Commitlint + Commitizen + cz-git 配置 Git 提交规范](https://blog.csdn.net/u013737132/article/details/130191363)
## 学习 使用  git 提交规范
https://blog.csdn.net/u013737132/article/details/130191363



wsl 启动 docker 
```
docker run -d -p 6379:6379 --name redis  -v /mnt/d/docker/redis/data:/data   redis:latest redis-server --bind 0.0.0.0 --port 6379

```

wsl 挂在
```
sudo mount -t drvfs C: ~/windows
```


vite 集成 tailwindcss 4.1
```
npm install tailwindcss @tailwindcss/vite


// vite.config.ts
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'
export default defineConfig({
  plugins: [
    tailwindcss(),
  ],
})



@import "tailwindcss";

// done will

```