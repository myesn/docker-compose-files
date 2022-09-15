# PostgreSQL Standalone Instance

本页介绍了如何部署 `PostgreSQL Standalone` 实例。

## 步骤

### 删除 .gitkeep

删除 `postgres-data\.gitkeep` 文件，保留目录。

### 设置文件夹权限

使用以下命令设置 `postgres-data` 目录的权限：
```bash
sudo chown -R 999:999 postgres-data
```

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

# 其他

## 其他服务依赖此服务

当 `app` 服务依赖于 `postgres` 服务时可以这样写：

```yaml
services:
  app:
    depends_on:
      postgres:
        condition: service_healthy
```

如果不依赖，可以将 `postgres` 服务中的 `healthcheck` 配置删除。