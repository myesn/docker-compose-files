# RabbitMQ Standalone Instance

本页介绍了如何部署 `RabbitMQ Standalone Instance`。

## 步骤

### 修改 rabbitmq.conf

打开 `rabbitmq.conf` 文件，找到如下配置，将 `${username}`、`${password}` 替换为自己想要的账号和密码：

```
default_user = ${username}
default_pass = ${password}
```

### 上传部署包

将部署包（`rabbitmq\standalone`）上传到服务器中任意目录。

### 启动服务

执行以下命令启动 `RabbitMQ Standalone` 实例：

```bash
docker-compose up -d
```