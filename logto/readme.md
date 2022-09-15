# Logto

本页介绍了如何部署 `Logto` 实例。

## 步骤

### 生成 https 证书

#### 自己有域名

如果有已注册的域名可以使用 `caddy` 进行反向代理（本仓库已存在该示例），然后再参考[此文档](https://docs.logto.io/zh-cn/docs/references/core/configuration#%E4%BD%BF%E7%94%A8-https-%E4%BB%A3%E7%90%86)进行配置。

然后删除 `docker-compose.yml` 文件中的以下配置：
```yaml
      - HTTPS_CERT_PATH=/https/cert/myesn.io.pem
      - HTTPS_KEY_PATH=/https/cert/myesn.io-key.pem
```

接着替换 `docker-compose.yml` 文件中的以下配置为自己的域名：
```yaml
      - ENDPOINT=https://myesn.io
```

#### 自己没有域名 

如果没有已注册的域名，可以使用 [mkcert](https://github.com/FiloSottile/mkcert) 在本地自行生成任意域名的 https 证书，然后将证书拷贝到 `https\cert` 目录中。

然后修改 `docker-compose.yml` 文件中以下配置的证书和密钥路径：
```yaml
      - HTTPS_CERT_PATH=/https/cert/myesn.io.pem
      - HTTPS_KEY_PATH=/https/cert/myesn.io-key.pem
```

接着替换 `docker-compose.yml` 文件中的以下配置为 https 证书中的域名：
```yaml
      - ENDPOINT=https://myesn.io
```

### 上传部署包

将部署包（`logto`）上传到服务器中任意目录。

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