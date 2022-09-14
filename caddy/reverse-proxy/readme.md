# Caddy Reverse Proxy

本页介绍了如何部署 `Caddy` 反向代理实例。

## 步骤

### 域名

必须拥有一个自己注册的域名，或者 `localhost`，否则无法使用 `Caddy`。

### DNS 指向

* Requires domain's public A/AAAA DNS records pointed at your machine.

* 要求域名的公共 A 或 AAAA DNS 记录指向服务器。

### 修改配置

打开 `Caddyfile`，修改以下内容：
1. 将 `myesn.io` 替换为自己注册的域名
2. 将 `localhost:3001` 替换为实际应用地址+端口

```
myesn.io

reverse_proxy localhost:3001
```

### 上传部署包

将部署包（`caddy`）上传到服务器中任意目录。

### 启动服务

执行以下命令启动 `Caddy` 实例：

```bash
docker-compose up -d
```