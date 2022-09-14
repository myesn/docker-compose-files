# PostgreSQL Standalone Instance

本页介绍了如何部署 `PostgreSQL Standalone` 实例。

## 步骤

### 设置账号密码

打开 `docker-compose.yml` 文件，找到如下配置，将 `POSTGRES_USER: postgres`、`POSTGRES_PASSWORD: p0stgr3s` 替换为自己想要的。

```yaml
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
```

[其他配置](https://github.com/docker-library/docs/blob/master/postgres/README.md)

### 上传部署包

将部署包（`postgre-sql\standalone`）上传到服务器中任意目录。

### 启动服务

执行以下命令启动 `PostgreSQL Standalone` 实例：

```bash
docker-compose up -d
```