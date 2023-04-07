# chatGPT-Proxy-DockerCompose
Deploying ChatGPT using docker-compose and accessing it through a local proxy. For NAS or Web server.

快速部署使用Clash代理访问ChatGPT, 适用于NAS或Web服务器.

## 0. 确保你的环境(NAS,Web Server)已经安装了docker和docker-compose.

## 1. clash 代理配置

复制并替换你自己的Clash代理配置文件到 'clash/config.yaml' 中.

### 1.1 确保关键参数无误
```
# HTTP 代理端口
port: 7890

# SOCKS5 代理端口
socks-port: 7891

# 允许局域网的连接（可用来共享代理）
allow-lan: true

# 规则模式：Rule（规则） / Global（全局代理）/ Direct（全局直连）
mode: Rule

# 设置日志输出级别 (默认级别：info，级别越高日志输出量越大，越倾向于调试)
# 四个级别：silent / info / warning / error / debug
log-level: info

# DashboardUi的登录密码  如果想设置密码，可以取消注释 secret 并修改 TypeYourPasswordForDashboardUi 为你的密码
#secret: TypeYourPasswordForDashboardUi

# Clash 的 RESTful API
external-controller: 0.0.0.0:9090
```

## 2. docker-compose 配置

### 2.1 open-api 配置

修改 'docker-compose.yml' 中的 'OPENAI_API_KEY' 参数为你自己的open-api-key.

### 3. 启动
在项目根目录下执行 `docker-compose up -d`
* 3003端口为Clash 网页管理端
* 3002端口为ChatGPT 网页端