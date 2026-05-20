# WSL2 Notes

安装 wsl --install -d Ubuntu

运行
wsl.exe -d Ubuntu

停止
wsl -t Ubuntu

| wsl -l -v             | 查看所有发行版及状态 |
| --------------------- | ---------- |
| wsl -t Ubuntu         | 停止Ubuntu实例 |
| wsl --shutdown        | 停止所有WSL实例  |
| wsl -d Ubuntu -u root | 以root用户启动  |

## wsl 用户及密码

172.28.135.207 2222
user:  zhuxiaoxi
passwd: 123456

## Docker 
```
# 启动 mysql
docker run -d -p 3306:3306 --name mysql -v d:/docker/data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 mysql

# 启动 redis
docker run -d -p 6379:6379 --name redis -v D:/docker/redis/redis.conf:/usr/local/etc/redis/redis.conf -v D:/docker/redis/data:/data redis:latest redis-server /usr/local/etc/redis/redis.conf


# 启动 ollama
docker run -d -v D:/docker/ollama-data:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:0.10.0-rc1-rocm

##  pull model 
docker exec ollama ollama pull llama2
crtl + d // to exit
docker exec -d ollama ollama run llama2


## deepseek:8b```
docker exec ollama ollama pull deepseek-r1:8b
docker exec ollama ollama run deepseek-r1:8b



```

### 管理命令

| 功能      | 命令                                                                 |
| ------- | ------------------------------------------------------------------ |
| 启动容器    | docker start ollama                                                |
| 停止容器    | docker stop ollama                                                 |
| 进入容器终端  | docker exec -it ollama bash                                        |
| 查看已下载模型 | docker exec ollama ollama list                                     |
| 删除模型    | docker exec ollama ollama rm llama2                                |
| 更新容器    | docker pull ollama/ollama:0.10.0-rc1-rocm && docker restart ollama |


1. **基础操作**
    
    - `ollama run <模型名>`：启动并交互指定模型（如 `ollama run llama3`）
    - `ollama pull <模型名>`：下载模型（如 `ollama pull gemma:7b`）
    - `ollama push <模型名>`：上传模型到仓库
    - `ollama list`：显示本地已下载的所有模型
    - `ollama delete <模型名>`：删除指定模型
2. **模型管理**
    
    - `ollama create <自定义模型名> -f <Modelfile路径>`：基于 Modelfile 创建自定义模型
    - `ollama show <模型名>`：查看模型详细信息（配置、参数等）
    - `ollama cp <源模型> <目标模型>`：复制模型（可用于创建副本或重命名）
3. **服务控制**
    
    - `ollama serve`：启动 Ollama 服务（通常会自动后台运行）
    - `ollama stop`：停止 Ollama 服务
4. **其他功能**
    
    - `ollama help`：查看命令帮助
    - `ollama version`：显示当前 Ollama 版本
- Usage:
  ollama [flags]
  ollama [command]

Available Commands:
  serve       Start ollama
  create      Create a model
  show        Show information for a model
  run         Run a model
  stop        Stop a running model
  pull        Pull a model from a registry
  push        Push a model to a registry
  list        List models
  ps          List running models
  cp          Copy a model
  rm          Remove a model
  help        Help about any command

Flags:
  -h, --help      help for ollama
  -v, --version   Show version information

Use "ollama [command] --help" for more information about a command.

```
### 💬 与模型交互

#### 方式 1: 命令行交互

bash

docker exec -it ollama ollama run llama2
>>> /help  # 查看帮助
>>> 为什么天空是蓝色的？

#### 方式 2: REST API 调用

bash

curl http://localhost:11434/api/generate -d '{
  "model": "llama2",
  "prompt": "解释量子计算的基本概念",
  "stream": false
}' | jq .response

#### 方式 3: Python 集成

python

import ollama

response = ollama.generate(
    model='llama2',
    prompt='用简单语言解释人工智能'
)
print(response['response'])
```




##### 
ip addr show eth0 | grep inet | awk '{print $2;}' | sed 's/\/.*$//'

config
bind 0.0.0.0  # 允许所有地址访问
docker restart redis
