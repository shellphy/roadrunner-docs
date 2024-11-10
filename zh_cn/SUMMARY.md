# 目录

## 😃 基础概念

* [什么是 RoadRunner?](intro/about.md)
* [特性](README.md)
* [快速开始](intro/quick-start.md)
* [安装](intro/install.md)
* [配置](intro/config.md)
* [贡献指南](intro/contributing.md)
* [升级与兼容性](intro/compatibility.md)

## 👷 PHP Worker 进程

* [Worker 进程](php/worker.md)
* [Worker 进程池](php/pool.md)
* [开发者模式](php/developer.md)
* [代码覆盖率](php/codecoverage.md)
* [调试](php/debugging.md)
* [环境配置](php/environment.md)
* [动态扩缩容](php/scaling.md)
* [RPC 远程过程调用](php/rpc.md)

## 🚀 定制化开发

* [构建包含自定义插件的 RR](customization/build.md)
* [与 Golang 应用集成](customization/embedding.md)
* [编写中间件](customization/middleware.md)
* [编写任务驱动器](customization/jobs-driver.md)
* [编写插件](customization/plugin.md)
* [事件总线](customization/events-bus.md)

## 🔌 插件系统

* [插件介绍](plugins/intro.md)
* [Centrifuge (WebSocket)](plugins/centrifuge.md)
* [系统服务 (Systemd)](plugins/service.md)
* [配置](plugins/config.md)
* [服务器](plugins/server.md)
* [锁机制](plugins/locks.md)
* [gRPC](plugins/grpc.md)
* [TCP](plugins/tcp.md)

## 🌐 社区插件

* [社区插件介绍](community-plugins/intro.md)
* [断路器](community-plugins/circuit-breaker.md)
* [远程文件发送](community-plugins/sendremotefile.md)
* [RFC 7234 缓存](community-plugins/cache.md)

## 📡 应用服务器

* [生产环境使用指南](app-server/production.md)
* [RoadRunner 与 NGINX 配合使用](app-server/nginx-with-rr.md)
* [在 AWS Lambda 中使用 RR](app-server/aws-lambda.md)
* [Docker 镜像](app-server/docker.md)
* [命令行工具](app-server/cli.md)
* [Systemd 服务](app-server/systemd.md)

## 🔐 键值存储

* [键值存储介绍](kv/overview-kv.md)
* [Memcached](kv/memcached.md)
* [内存存储](kv/memory.md)
* [BoltDB](kv/boltdb.md)
* [Redis](kv/redis.md)

## 📦 队列和任务

* [任务系统介绍](queues/overview-queues.md)
* [Google Pub/Sub](queues/google-pub-sub.md)
* [Beanstalk](queues/beanstalk.md)
* [内存队列](queues/memory.md)
* [RabbitMQ](queues/amqp.md)
* [BoltDB](queues/boltdb.md)
* [Kafka](queues/kafka.md)
* [NATS](queues/nats.md)
* [SQS](queues/sqs.md)

## 🕸️ HTTP

* [HTTP 服务介绍](http/http.md)
* [请求头和跨域](http/headers.md)
* [代理 IP 解析](http/proxy.md)
* [静态文件服务](http/static.md)
* [X-Sendfile](http/sendfile.md)
* [流式传输](http/resp-streaming.md)
* [gzip 压缩](http/gzip.md)

## 📈 日志和可观测性

* [OpenTelemetry](lab/otel.md)
* [健康检查](lab/health.md)
* [访问日志](lab/accesslogs.md)
* [应用日志](lab/applogger.md)
* [指标监控](lab/metrics.md)
* [Grafana](lab/dashboards/dashboards.md)
* [日志系统](lab/logger.md)

## 🔀 工作流引擎

* [Temporal.io](workflow/temporal.md)
* [Worker 进程](workflow/worker.md)

## 🧩 框架集成

* [从 RRv1 迁移到 RRv2](integration/migration.md)
* [Spiral 框架](integration/spiral.md)
* [Yii](integration/yii.md)
* [Symfony](integration/symfony.md)
* [Laravel](integration/laravel.md)
* [ChubbyPHP](integration/chubbyphp.md)

## 🧪 实验性功能

* [实验性功能列表](experimental/experimental.md)

## 🚨 错误代码

* [CRC 校验失败](known-issues/stdout-crc.md)
* [分配超时](known-issues/allocate-timeout.md)

## 📚 版本发布

* [v2024.2.1](releases/v2024-2-1.md)
* [v2024.2.0](releases/v2024-2-0.md)
* [v2024.1.5](releases/v2024-1-5.md)