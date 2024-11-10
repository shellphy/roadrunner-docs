# 什么是 RoadRunner？

RoadRunner 是一个高性能的 PHP 应用服务器和进程管理器，通过插件化的设计实现了高度的可扩展性。它使用 Go 语言开发，通过以 worker 形式运行您的应用程序，其中每个 worker 代表一个独立的进程，确保了运行时的隔离性和独立性。

RoadRunner 被设计为 PHP 应用程序的中央处理器，帮助开发者轻松创建更快、响应更快和更稳健的应用程序。

![image](https://user-images.githubusercontent.com/773481/235296092-2f82643b-7822-4649-952a-0529efa3af88.png)

## 工作原理

RoadRunner 高效地管理一组 PHP 进程（称为 workers），并将来自各种插件的传入请求路由到这些 workers。这种通信是通过 [goridge](https://github.com/roadrunner-server/goridge) 协议完成的，使您的 PHP 应用程序能够处理请求并将响应发送回客户端。

![架构图](https://github.com/roadrunner-server/docs/assets/8040338/e96ebcbf-3d7e-46be-b4ec-534df898a14e)

以下插件被设计用于运行 workers 并处理特定类型的请求：

- [**HTTP**](../http/http.md) - 处理来自客户端的 HTTP 请求并转发给 PHP 应用程序。
- [**Jobs**](../queues/overview-queues.md) - 处理从队列代理接收的队列任务，并将其发送到消费者 PHP 应用程序进行处理。
- [**Centrifuge**](../plugins/centrifuge.md) - 管理来自 Centrifugo WebSocket 服务器客户端的事件并转发到 PHP 应用程序。它支持双向通信，实现服务器和客户端之间高效无缝的交互。
- [**gRPC**](../plugins/grpc.md) - 处理来自客户端的 gRPC 请求并传递给 PHP 应用程序。
- [**TCP**](../plugins/tcp.md) - 处理来自客户端的 TCP 请求并路由到相应的 PHP 应用程序。
- [**Temporal**](../workflow/temporal.md) - 管理工作流和活动，实现各种任务和流程的高效处理。

通过使用这些插件，RoadRunner 确保您的 PHP 应用程序能够有效处理各种请求和通信协议，提供最佳的性能和灵活性。

## (g)RPC 接口

RoadRunner 还提供了一个定制的 gRPC 接口，用于应用程序和服务器之间的通信，这在增强两个组件之间的交互方面发挥着重要作用。当使用支持 RPC 通信的各种插件时，这个接口特别有用，例如：

- [**KV**](../kv/overview-kv.md) - 缓存服务，允许高效存储和检索缓存数据。
- [**Locks**](../plugins/locks.md) - 提供便捷的方式来管理分布式锁，确保跨多个进程或系统的资源访问协调。
- [**Service**](../plugins/service.md) - 动态服务器进程监督器，支持直接从应用程序无缝管理服务器进程。
- [**Jobs**](../queues/overview-queues.md) - 提供从应用程序内部动态管理队列管道的能力，简化任务和作业的执行。
- [**Logger**](../lab/logger.md) - 促进应用程序日志转发到 RoadRunner 日志器，确保集中和高效的日志管理。
- [**Metrics**](../lab/metrics.md) - 允许将应用程序指标提交到 Prometheus，支持全面的应用程序性能监控和分析。

## PHP Worker

RoadRunner 在传入请求之间保持 PHP workers 的活动状态。这意味着您可以完全消除启动加载时间（如框架初始化），显著加快重量级应用程序的运行速度。

![基础图表](https://user-images.githubusercontent.com/796136/65348057-00df2e00-dbe9-11e9-9173-f0bd4269c101.png)

由于 worker 驻留在内存中，所有打开的资源在请求之间持续存在，可用于后续交互。利用内置的 [goridge](https://github.com/roadrunner-server/goridge)，您可以将复杂计算卸载到应用服务器。例如，您可以调度后台 PHP 任务，甚至开发自己的 [自定义 RoadRunner 插件](../customization/plugin.md)，使用 Go 处理复杂任务，这提供了更好的效率和性能。通过利用 PHP 和 Go 的优势，您可以为应用程序创建更强大和高性能的解决方案。

值得提到 PHP workers 的以下特性：

- **隔离性：** 每个 worker 进程独立运行，防止与其他 worker 进程相互干扰，提高稳定性。
- **可扩展性：** 共享无状态架构通过简单地添加更多 worker 进程，使应用程序更容易扩展。
- **容错性：** 单个 worker 的故障不会影响其他 workers 的运行，确保服务不中断。
- **简化开发：** 通过维护 workers 的隔离性，共享无状态架构减少了管理共享资源的复杂性，简化了开发过程。

## 下一步

1. [PHP Workers](../php/worker.md) - 了解如何配置和运行 PHP workers。
2. [PHP Workers — RPC 到 RoadRunner](../php/rpc.md) - 了解如何使用 RPC 与 PHP 应用程序通信。
3. [编写自定义插件](../customization/plugin.md) - 了解如何创建自定义插件。