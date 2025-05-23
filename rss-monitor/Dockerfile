FROM python:3.11-slim

ENV TZ=Asia/Shanghai

# 安装系统依赖（用于编译 lxml 等库）
RUN apt-get update && apt-get install -y \
    gcc libxml2-dev libxslt1-dev && \
    rm -rf /var/lib/apt/lists/*

# 设置工作目录
WORKDIR /app

# 复制依赖与代码文件
COPY requirements.txt ./
COPY rss_monitor.py ./
COPY config.json ./

# 安装 Python 依赖
RUN pip install --no-cache-dir -r requirements.txt

# 启动容器时默认进入 daemon 模式（自动抓取与推送）
CMD ["python", "rss_monitor.py", "--daemon"]
