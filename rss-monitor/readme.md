封装自 [原项目](https://github.com/dajie111/nodeseek-userscript/tree/main)
- 新增 Telegram 交互支持，部署即用。
**2025.05.27 更新：**
- 调整抓取间隔至 30–40 秒，降低对 NodeSeek 首页的访问频率
- 优化访问逻辑：仅首次启动或遭遇 Cloudflare 拦截时访问首页，常规循环直接抓取帖子列表
### 部署
- 克隆基础配置并拉取镜像
```bash
git clone https://github.com/ecouus/nodeseekscript.git && \
cd nodeseekscript/rss-monitor && \
docker pull ecouus/rss-monitor:latest
```
- 运行容器并挂载当前目录
```
docker run -d \
  --name rss-monitor \
  -v $PWD:/app \
  --log-opt max-size=10m \
  --log-opt max-file=3 \
  ecouus/rss-monitor:latest
```
运行后修改config.json文件，替换默认的`bot_token`和`chat_id`
```bash
nano config.json && docker restart rss-monitor
```
### 其他
- 查看日志
```bash
docker logs rss-monitor
```
- 容器显示模式
```bash
docker exec -it rss-monitor bash && python rss_monitor.py --daemon
```

### Telegram 指令

| 指令         | 功能      |
| ---------- | ------- |
| `/add 关键词` | 添加关键词   |
| `/del 关键词` | 删除关键词   |
| `/list`    | 查看关键词列表 |
| `/help`    | 帮助菜单    |

---
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
