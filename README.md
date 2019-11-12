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



### 1.5.1 Support

- [Stackoverflow](https://stackoverflow.com/questions/tagged/lettuce) 在 Stackoverflow 上有一个 Lettuce 用户社区，很多用户都在这互相帮助分享交流。
- [Gitter](https://gitter.im/lettuce-io/Lobby) 上也有一个Lettuce社区。
- 谷歌 Lettuce 论坛： [lettuce-redis-client-users](https://groups.google.com/d/forum/lettuce-redis-client-users) or lettuce-redis-client-users@googlegroups.com.
- Github issues https://github.com/lettuce-io/lettuce-core/issues.



### 1.5.2 快速跳转

- 如果你想直接开始  [Getting Started](https://lettuce.io/core/release/reference/index.html#getting-started)  。
- 转到主从，Redis Sentinel和Redis Cluster 的高可用和分片特性讲解。传送门：[High-Availability and Sharding](https://lettuce.io/core/release/reference/index.html#ha-sharding) 
- 如果你想更深入的了解 Reactor 的核心功能：
  - 了解客户端如何配置，一些性能相关各种传输方式，传送门：[高级用法](https://lettuce.io/core/release/reference/index.html#advanced-usage)
  - 想知道如何把 Lettuce 集成到你的 spring 应用中可查看  [Integration and Extension](https://lettuce.io/core/release/reference/index.html#integration-extension)
  - You want to know more about **at-least-once** and **at-most-once**? Take a look into [Command execution reliability](https://lettuce.io/core/release/reference/index.html#command-execution-reliability).

# 2. New & Noteworthy





# 3. Getting Started

### 3.1. 1. Get it

#### Maven 用户:

把如下配置添加到 pom.xml 文件下：

```xml
<dependency>
    <groupId>io.lettuce</groupId>
    <artifactId>lettuce-core</artifactId>
    <version>5.2.1.RELEASE</version>
</dependency>
```



#### lvy 用户：

把如下配置添加到 ivy.xml 文件下：

```xml
<ivy-module>
  <dependencies>
    <dependency org="io.lettuce" name="lettuce-core" rev="5.2.1.RELEASE"/>
  </dependencies>
</ivy-module>
```

#### Gradle 用户：

把如下配置添加到 build.gradle 文件下：

```
dependencies {
  compile 'io.lettuce:lettuce-core:5.2.1.RELEASE'
}
```

#### Plain Java

去 https://github.com/lettuce-io/lettuce-core/releases 下载最新的二进制压缩包解压使用



### 3.2. 2. 开始 coding！

很简单吧！不用太多复杂的流程，我们就可以开始了，冲！

导入需要的类：

```java
import io.lettuce.core.*;
```

开始写代码：

```java
RedisClient redisClient = RedisClient.create("redis://password@localhost:6379/0");
StatefulRedisConnection<String, String> connection = redisClient.connect();
RedisCommands<String, String> syncCommands = connection.sync();

syncCommands.set("key", "Hello, Redis!");

connection.close();
redisClient.shutdown();
```

完成！

接下来看一些其他github上的事例吧：

- [Standalone Redis](https://github.com/lettuce-io/lettuce-core/blob/5.2.1.RELEASE/src/test/java/io/lettuce/examples/ConnectToRedis.java)
- [Standalone Redis with SSL](https://github.com/lettuce-io/lettuce-core/blob/5.2.1.RELEASE/src/test/java/io/lettuce/examples/ConnectToRedisSSL.java)
- [Redis Sentinel](https://github.com/lettuce-io/lettuce-core/blob/5.2.1.RELEASE/src/test/java/io/lettuce/examples/ConnectToRedisUsingRedisSentinel.java)
- [Redis Cluster](https://github.com/lettuce-io/lettuce-core/blob/5.2.1.RELEASE/src/test/java/io/lettuce/examples/ConnectToRedisCluster.java)
- [Connecting to a ElastiCache Master](https://github.com/lettuce-io/lettuce-core/blob/5.2.1.RELEASE/src/test/java/io/lettuce/examples/ConnectToElastiCacheMaster.java)
- [Connecting to ElastiCache with Master/Replica](https://github.com/lettuce-io/lettuce-core/blob/5.2.1.RELEASE/src/test/java/io/lettuce/examples/ConnectToMasterSlaveUsingElastiCacheCluster.java)
- [Connecting to Azure Redis Cluster](https://github.com/lettuce-io/lettuce-core/blob/5.2.1.RELEASE/src/test/java/io/lettuce/examples/ConnectToRedisClusterSSL.java)
- [Lettuce with Spring](https://github.com/lettuce-io/lettuce-core/blob/5.2.1.RELEASE/src/test/java/io/lettuce/examples/SpringExample.java)



## 4. 连接Redis

与Redis Standalone，Sentinel或Cluster的连接有详细的连接配置。连接的统一形式是通过 **RedisURI**，

在 **RedisURI** 中包含了数据库，密码，超时设置等，你可以通过以下方式来创建 **RedisURI**

1. Use an URI:

```
RedisURI.create("redis://localhost/");
```



2. Use the Builder

```
RedisURI.Builder.redis("localhost", 6379).auth("password").database(1).build();
```



3. 直接赋值

```
new RedisURI("localhost", 6379, 60, TimeUnit.SECONDS);
```



### 4.1. URI 语法

**Redis Standalone**

*redis* **://** [**:** *password*@] *host* [**:** *port*] [**/** *database*][**?** [*timeout=timeout*[*d|h|m|s|ms|us|ns*]] [&_database=database_]]



**Redis Standalone (SSL)**

*rediss* **://** [**:** *password*@] *host* [**:** *port*] [**/** *database*][**?** [*timeout=timeout*[*d|h|m|s|ms|us|ns*]] [&_database=database_]]



**Redis Standalone (Unix Domain Sockets)**

*redis-socket* **://** *path* [**?**[*timeout=timeout*[*d|h|m|s|ms|us|ns*]][&_database=database_]]



**Redis Sentinel**

*redis-sentinel* **://** [**:** *password*@] *host1*[**:** *port1*] [, *host2*[**:** *port2*]] [, *hostN*[**:** *portN*]] [**/** *database*][**?**[*timeout=timeout*[*d|h|m|s|ms|us|ns*]] [&_sentinelMasterId=sentinelMasterId_] [&_database=database_]]



**对应方式**

- `redis` ---Redis Standalone
- `rediss`--- Redis Standalone SSL
- `redis-socket` ---Redis Standalone Unix Domain Socket
- `redis-sentinel` ---Redis Sentine



**Timeout 单位对应** 

- `d` Days 天
- `h` Hours 时
- `m` Minutes 分
- `s` Seconds 秒
- `ms` Milliseconds 毫秒
- `us` Microseconds 微妙
- `ns` Nanoseconds 纳秒
- 

**Tip：相比在路径中写数据库，建议优先使用直接赋值的方式，**



### 4.2. 基本用法

**Example 1. Basic usage**

------

```java
RedisClient client = RedisClient.create("redis://localhost");                //1  

StatefulRedisConnection<String, String> connection = client.connect();       //2

RedisCommands<String, String> commands = connection.sync();                  //3          

String value = commands.get("foo");                                          //4         

...

connection.close();                                                          //5                

client.shutdown();                                                           //6
```

1. 提供一个 RedisUri 指向 localhost 默认端口为 6379 并创建一个 redis 客户端实例。
2. 用创建好的客户端实例建立连接。
3. 获取同步执行的命令API，并且 Lettuce 还支持 异步 和反应式的执行操作。
4. 发出一个 redis 命令，去获取 键为“foo” 的值。
5. 完成后关闭连接，这通常是发生在程序的最后。
6. 关闭客户端去释放线程和资源，这通常是发生在程序的最后。



------

每个 redis command 都是通过一种或多种名称和redis 命令名称相同的方法实现的。

Complex commands with multiple modifiers that change the result type include the CamelCased modifier as part of the command name, e.g. `zrangebyscore` and `zrangebyscoreWithScores`.



Redis 连接是长链接和线程安全的，如果连接断开，将重新连接，直到调用 `close()`  为止。重新连接成功后，将（重新）发送尚未超时的未决命令。



所有的连接都是使用的是设置的 reids 客户端的 timeout，在非阻塞命令在timeout时间之内未返还结果将抛出**RedisException**



超时默认设置为 60 秒，可以在redis 客户端中修改，当 timeout了 同步方法将抛出RedisCommandExecutionException，以防Redis响应错误，Redis响应错误时，异步连接的轻快下不会引发异常。



####  4.2.1. RedisURI

RedisURI 包含 host/port 并且可以携带 权限认证和数据的信息，连接成功后你会获得权限，然后选择数据库。

断开连接后依然可以恢复连接。

