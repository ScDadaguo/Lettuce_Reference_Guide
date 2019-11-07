![lettuce green text@2x](https://lettuce.io/core/release/reference/images/lettuce-green-text@2x.png)

> 事出有因：
>
> 为啥我会想去读这本官方文档，因为查找了一些博文，发现网上的资源并不是非常多，少而杂，那正好我时间，我就自己去啃吧！冲就完事了！



# 1. 总览

这是一个基于 Lettuce 官网的参考导读文档，它介绍了如何使用 Lettuce ，以及 Lettuce  的概念、语义和语法。

您可以从头到尾按序导读，也可以直接跳到您感兴趣的章节进行导读。

本节会对 Redis 进行基础的介绍，文档剩余的章节是假设您已经对 Redis 有稍许了解的基础上进行对 Lettuce 特性的讲解。

## 1.1 了解 Redis

NoSQL 在数据库领域掀起了一场浪潮，它是一个广阔的领域，具有非常多的解决方案，术语和模式（更糟的是同一术语有多个意思），尽管原理是相通的，但是至关重要的是，用户要一定程度上熟悉 Reids。去深入了解Redis 最好的方法还是去阅读它们的官方文档。



想深入了解redis，可以访问 [redis.io](redis.io)，下面列出一些其他十分有用的资源：

- [交互式教程-try.redis.i](http://try.redis.io/)
- [command references](http://redis.io/commands) 介绍redis命令以及一些学习导读，参考文档和教程

## 1.2 Project Reactor

[Reactor](https://projectreactor.io/) 是一个基于[Reactive Streams Specification](https://github.com/reactive-streams/reactive-streams-jvm)运行在 JVM 上的应用于构建高效的非阻塞应用程序的一个 reactive 库。基于reactor构建的应用程序具有非常高的吞吐量，并以非常低的内存占用量运行。这个特性使得它非常适合使用微服务架构来构建高效的事件驱动程序。

Reactor 实现了  [Flux<>T](https://projectreactor.io/docs/core/release/api/reactor/core/publisher/Flux.html) and [Mono<T>](https://projectreactor.io/docs/core/release/api/reactor/core/publisher/Mono.html) 两者都支持 non-blocking back-pressure ，这样就可以在具有明确定义的内存使用情况的线程之间交换数据，同时就避免了一些不必要的缓冲和阻塞。



## 1.3 Redis 的非阻塞 API

Lettuce 是一个基于 [netty](http://netty.io/) 和 Reactor 的一个可扩展同时线程安全的 Redis 客户端。Lettuce提供了同步，异步和反应式API来与Redis进行交互。



## 1.4 环境需求

- Lettuce 4.x and 5.x 需要 JDK8 及以上更高版本
- Redis 需要2.6 及以上更高版本



## 1.5 其它你可能需要的资源

学习一个新的开源框架肯定不是一番风顺的，在这个部分，我们试着提供一个较为简单的导读指南来帮助读者来学习 Lettuce。如果您遇到一些困扰或者您想要得到一些建议，我们提供一下链接给你，或许能够帮助到您！

