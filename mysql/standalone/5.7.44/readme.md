# MySQL 5.7.44 Standalone Instance

本文介绍了如何部署 `MySQL 5.7.44 Standalone` 实例。

## 步骤

### 设置 root 账号密码和数据库

打开 `docker-compose.yml` 文件，找到如下配置，将必填参数 `${root_password}` 替换为自己想要的，其它的可选参数根据自己的情况删减：

```yaml
    environment:
      - MYSQL_ROOT_PASSWORD=${root_password} # [required] root 超级用户账户的密码
      - MYSQL_DATABASE=${database}           # [optional] 容器启动时创建的数据库的名称。如果提供了 MYSQL_USER、MYSQL_PASSWORD，则 MYSQL_USER 将被授予对此数据库的超级用户访问权限
      - MYSQL_USER=${user}                   # [optional] 创建新用户，此用户将被授予变量 MYSQL_DATABASE 数据库的超级用户权限
      - MYSQL_PASSWORD=${user_password}      # [optional] 创建新用户的密码
```

### 配置初始化脚本

如果想在变量 `MYSQL_DATABASE` 数据库创建后执行一些架构或数据初始化脚本，你可以将他们放入 `./docker-entrypoint-initdb.d` 目录中，支持的脚本类型有 `.sh`, `.sql`, `.sql.gz` 三种。文件将按字母顺序执行。SQL 文件将默认导入 `MYSQL_DATABASE` 变量指定的数据库。

在 `docker-compose.yml` 文件中默认配置了一个放置初始化脚本的目录 `./docker-entrypoint-initdb.d`：

```yaml
    volumes:
      - ./docker-entrypoint-initdb.d:/docker-entrypoint-initdb.d
```

### 上传部署包

将部署包（`mysql\standalone\5.7.44`）上传到服务器中任意目录。

### 权限配置

暂无，因为我现在用的 Windows 环境，对权限无感。未来使用 Linux 时再补充这部分的文档说明。

### 启动服务

执行以下命令启动 `MySQL 5.7.44 Standalone` 实例：

```bash
docker-compose up -d
```

# 参考

- https://hub.docker.com/_/mysql