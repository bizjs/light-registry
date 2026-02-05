# light-registry

`Light Registry` is a minimal Docker Registry stack combining Docker Distribution,
a pluggable auth-service, and docker-registry-ui — without the complexity of Harbor.

## 快速开始

### 1. 启动服务

```bash
# 构建并启动所有服务
docker-compose up -d

# 查看日志
docker-compose logs -f

# 查看特定服务的日志
docker-compose logs -f web-ui
docker-compose logs -f registry
```

### 2. 访问 Web UI

打开浏览器访问：http://localhost:3000

### 3. 推送镜像到 Registry

```bash
# 标记镜像
docker tag your-image:tag localhost:3000/your-image:tag

# 推送镜像（通过 UI 的代理）
docker push localhost:3000/your-image:tag

# 或者直接推送到 registry（如果需要）
docker tag your-image:tag localhost:5000/your-image:tag
docker push localhost:5000/your-image:tag
```

### 4. 拉取镜像

```bash
# 从 UI 代理拉取
docker pull localhost:3000/your-image:tag

# 或者直接从 registry 拉取
docker pull localhost:5000/your-image:tag
```

## 管理命令

### 停止服务

```bash
docker-compose down
```

### 停止并删除数据

```bash
docker-compose down -v
```

### 重新构建 UI

```bash
docker-compose build web-ui
docker-compose up -d web-ui
```

### 查看服务状态

```bash
docker-compose ps
```
