# 简介

该仓库用于记录平时用到的一些服务的 `docker-compose.yml` 配置。

下面列举出的目录项都已在使用，并已验证过，但时间和精力有限，有空的时候再编写具体的文档内容。

## 目录

- MongoDB
    - [x] [MongoDB Standalone](mongodb/standalone/readme.md)
    - [ ] MongoDB Replica Set 副本集
- Node.js
- Java
- Nginx
  - [x] [Nginx SSL配置](nginx/ssl-as-a-reverse-proxy/readme.md)
- MySQL
    - Standalone
      - [x] [MySQL 5.7.44 Standalone](mysql/standalone/5.7.44/readme.md)
      - [x] [MySQL 8.0.28 Standalone](mysql/standalone/8.0.28/readme.md)
    - [ ] MySQL Master=Slave 双实例互为主从
- Redis
    - [ ] Redis Standalone
    - [ ] Redis Sentinel 哨兵模式
- RabbitMQ
    - [x] [RabbitMQ Standalone](rabbitmq/standalone/readme.md)
    - [ ] RabbitMQ Classic Queue Mirroring 经典镜像队列（镜像集群）
- PostgreSQL
    - [x] [PostgreSQL Standalone](postgre-sql/standalone/readme.md)
- Caddy
  - [x] [Caddy Reverse proxy 反向代理](caddy/reverse-proxy/readme.md)
- Logto
  - [x] [Logto(HTTPS) + PostgresSQL](logto/simple/readme.md)

## 单词说明

`Standalone`：单实例
