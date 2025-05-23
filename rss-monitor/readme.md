### 构件镜像
```bash
docker build -t ecouus/rss-monitor:latest .
```
### 登陆dockerhub
```bash
docker login
```
### 推送镜像到 Docker Hub
```bash
docker push ecouus/rss-monitor:latest
```

### 验证推送成功
浏览器打开：
```
https://hub.docker.com/r/ecouus/rss-monitor
```

---

### 部署：
```bash
docker pull ecouus/rss-monitor:latest

docker run -d \
  --name rss-monitor \
  -v $PWD:/app \
  ecouus/rss-monitor:latest
```
