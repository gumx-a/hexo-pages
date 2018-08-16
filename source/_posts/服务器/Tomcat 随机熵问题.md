---
title: Tomcat 随机熵问题
categories:
  - 服务器
date: 2018-02-24 14:32:18
tags:
  - Tomcat
---

Tomcat 7/8都使用org.apache.catalina.util.SessionIdGeneratorBase.createSecureRandom类产生安全随机类SecureRandom的实例作为会话ID，比较耗时。是基于SHA-1算法实现且保密性较强的伪随机数生成器。非常适合那些需要非常高质量随机性的场景，比如一次性的支付或生成密钥的场景。对于生成高质量的加密密钥或者是需要长期保护的场景，一定要这么做。

随机数产生器会收集来自设备驱动器和其它源的环境噪声数据，并放入熵池中。产生器会评估熵池中的噪声数据的数量。当熵池为空时，这个噪声数据的收集是比较花时间的。这就意味着，Tomcat在生产环境中使用熵池时，会被阻塞较长的时间。

有两种解决办法：

1）配置tomcat参数 可以通过配置JRE使用非阻塞的Entropy Source。

在catalina.sh中加入这么一行：-Djava.security.egd=file:/dev/./urandom 即可。

加入后再启动Tomcat，整个启动耗时下降到Server startup in 2912 ms。

2）在JVM环境中解—一劳永逸

打开$JAVA_PATH/jre/lib/security/java.security这个文件，找到下面的内容：

securerandom.source=file:/dev/urandom 大概在70行 ，替换成

securerandom.source=file:/dev/./urandom