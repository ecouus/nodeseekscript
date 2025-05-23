[原项目地址](https://github.com/dajie111/nodeseek-userscript/tree/main)  
对原版进行了完善，并封装为Docker，便于部署。  
新增机器人指令交互模式
### 部署
```bash
git clone https://github.com/ecouus/nodeseekscript.git && cd nodeseekscript/rss-monitor && docker pull ecouus/rss-monitor:latest

docker run -d \
  --name rss-monitor \
  -v $PWD:/app \
  ecouus/rss-monitor:latest
```
运行后修改config.json文件，替换默认的`bot_token`和`chat_id`
```bash
nano config.json
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
