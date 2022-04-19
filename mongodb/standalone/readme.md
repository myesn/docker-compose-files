# MongoDB Standalone Instance

本页介绍了如何部署 `MongoDB Standalone` 实例。

## 步骤

### 设置 root 账号密码

打开 `docker-compose.yml` 文件，找到如下配置，将 `${root_username}`、`${root_password}` 替换为自己想要的，该用户名和密码仅具有 `admin` 数据库的 `root`权限。

```yaml
    environment:
      - MONGO_INITDB_ROOT_USERNAME=${root_username}
      - MONGO_INITDB_ROOT_PASSWORD=${root_password}
```

### 上传部署包

将部署包（`mongodb\standalone`）上传到服务器中任意目录。

### 权限配置

在服务器上切换到 `docker-compose.yml` 文件所在目录，然后执行以下命令设置权限：

```bash
sudo chown -R 999:999 ./mongodb
```

### 启动服务

执行以下命令启动 `MongoDB Standalone` 实例：

```bash
docker-compose up -d
```
