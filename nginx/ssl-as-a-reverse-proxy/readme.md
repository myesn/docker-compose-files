# SSL as a Reverse Proxy

本页介绍了如何部署 `nginx ssl` 实例。

## 步骤

### 生成 https 证书

准备证书文件和证书密钥文件，本地测试可以用 [mkcert](https://github.com/FiloSottile/mkcert) 工具生成。

然后把证书放入 `ssl/certs` 目录中，证书密钥文件放入 `ssl/private` 目录中。

### 修改 nginx.conf

打开 `conf/nginx.conf` 文件找到如下配置，进行相应的修改（反向代理的服务器地址）：
```nginx.conf
    upstream web-api {
        server hi:9195;
    }
    
    ...
```

### 修改 docker-compose.yml

打开 `docker-compose.yml` 找到如下配置，修改左侧的证书文件名称和证书密钥文件名称：
```yaml
      - ./ssl/certs/myesn.io.pem:/etc/ssl/certs/site.pem
      - ./ssl/private/myesn.io-key.pem:/etc/ssl/private/site-key.pem
```

### 上传部署包

将部署包（`ningx\ssl-as-a-reverse-proxy`）上传到服务器中任意目录。

### 权限配置

进入 `logto` 目录，执行以下命令为启动脚本赋予可执行权限：

```bash
sudo chmod +x up.sh
```

### 启动服务

最后执行以下命令启动 `Logto` 实例：

```bash
./up.sh
```

打开浏览器，访问你的域名比如 `https://myesn.io` 就可以了。

## 其他

### bind() to 0.0.0.0:443 failed (10013: An attempt was made to access a socket in a way forbidden by its access permissions

其他程序占用了 `443` 端口，我是在 `windows` 发现此问题的，通过 `netstat -aon|findstr "443"` 找到具体的 PID，然后到任务管理器结束它。