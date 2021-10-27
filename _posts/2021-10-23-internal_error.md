---
layout: post
title: "[IntelliJ]java.util.concurrent.CompletionException: java.net.BindException: Address already in use"
author: "Misun"
categories: [TIL]
comments: true
---

작업을 하려고 인텔리제이를 켰는데 아래와 같은 오류가 발생했다. 당황... 아마 어제 포트를 8080에서 8088로 바꼈던게 문제가 되었던 듯 하다.<br>

### 오류 전문

<details>
<summary>더보기</summary>
<div markdown="1">

```
Internal error. Please refer to [https://jb.gg/ide/critical-startup-errors](https://jb.gg/ide/critical-startup-errors)

java.util.concurrent.CompletionException: java.net.BindException: Address already in use: bind
at java.base/java.util.concurrent.CompletableFuture.encodeThrowable(CompletableFuture.java:314)
at java.base/java.util.concurrent.CompletableFuture.completeThrowable(CompletableFuture.java:319)
at java.base/java.util.concurrent.CompletableFuture$AsyncSupply.run(CompletableFuture.java:1702)
at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
at java.base/java.util.concurrent.Executors$PrivilegedThreadFactory$1$1.run(Executors.java:668)
at java.base/java.util.concurrent.Executors$PrivilegedThreadFactory$1$1.run(Executors.java:665)
at java.base/java.security.AccessController.doPrivileged(Native Method)
at java.base/java.util.concurrent.Executors$PrivilegedThreadFactory$1.run(Executors.java:665)
at java.base/java.lang.Thread.run(Thread.java:829)
Caused by: java.net.BindException: Address already in use: bind
at java.base/sun.nio.ch.Net.bind0(Native Method)
at java.base/sun.nio.ch.Net.bind(Net.java:455)
at java.base/sun.nio.ch.Net.bind(Net.java:447)
at java.base/sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:227)
at io.netty.channel.socket.nio.NioServerSocketChannel.doBind(NioServerSocketChannel.java:134)
at io.netty.channel.AbstractChannel$AbstractUnsafe.bind(AbstractChannel.java:550)
at io.netty.channel.DefaultChannelPipeline$HeadContext.bind(DefaultChannelPipeline.java:1334)
at io.netty.channel.AbstractChannelHandlerContext.invokeBind(AbstractChannelHandlerContext.java:506)
at io.netty.channel.AbstractChannelHandlerContext.bind(AbstractChannelHandlerContext.java:491)
at io.netty.channel.DefaultChannelPipeline.bind(DefaultChannelPipeline.java:973)
at io.netty.channel.AbstractChannel.bind(AbstractChannel.java:248)
at io.netty.bootstrap.AbstractBootstrap$2.run(AbstractBootstrap.java:356)
at io.netty.util.concurrent.AbstractEventExecutor.safeExecute(AbstractEventExecutor.java:164)
at io.netty.util.concurrent.SingleThreadEventExecutor.runAllTasks(SingleThreadEventExecutor.java:472)
at io.netty.channel.nio.NioEventLoop.run(NioEventLoop.java:500)
at io.netty.util.concurrent.SingleThreadEventExecutor$4.run(SingleThreadEventExecutor.java:989)
at io.netty.util.internal.ThreadExecutorMap$2.run(ThreadExecutorMap.java:74)
```

</div>
</details>

### 해결방법

- Windows PowerShell을 관리자 권한으로 실행

- netsh winsock reset 를 입력

- 컴퓨터를 재부팅

<br>
이렇게 하면 인텔리제이가 제대로 작동하는 것을 볼 수 있다. 검색을 했을 때 대부분이 dism.exe /Online /Disable-Feature:Microsoft-Hyper-V 명령어를 이용하라고 했는데 Windows10 Home에서는 Hyper-V를 사용할 수 없어서 도움이 되지 않았다. Hyper-V를 사용하지 않아도 간단히 해결돼서 다행이다.

#### 출처

<https://idongmai.wo.tc/entry/JetBrains%E7%A4%BE-%EC%A0%9C%ED%92%88%EA%B5%B0%EC%9D%98-%ED%8F%AC%ED%8A%B8-%EB%B0%94%EC%9D%B8%EB%94%A9-%EB%AC%B8%EC%A0%9C-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95>
