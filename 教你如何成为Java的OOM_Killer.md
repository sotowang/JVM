# 教你如何成为Java的OOM Killer

[教你如何成为Java的OOM Killer](https://mp.weixin.qq.com/s?__biz=MzI4NDY5Mjc1Mg==&mid=2247484071&idx=1&sn=84604a51fd18b91f73c46507c182540a&chksm=ebf6dad8dc8153cebb029372c0745a3c6570e527e1f95cee2fb9fb33c50d46c64f20722a3d96&scene=21#wechat_redirect)

我们都知道JVM的内存管理是自动化的，Java语言的程序指针也不需要开发人员手工释放，JVM的GC会自动的进行回收，但是，如果编程不当，JVM仍然会发生内存泄露，导致Java程序产生了OutOfMemoryError（OOM）错误。

产生OutOfMemoryError错误的原因包括：

```
java.lang.OutOfMemoryError: Java heap space

java.lang.OutOfMemoryError: PermGen space及其解决方法

java.lang.OutOfMemoryError: unable to create new native thread

java.lang.OutOfMemoryError：GC overhead limit exceeded
```


对于第1种异常，表示Java堆空间不够，当应用程序申请更多的内存，而Java堆内存已经无法满足应用程序对内存的需要，将抛出这种异常。

对于第2种异常，表示Java永久带（方法区）空间不够，永久带用于存放类的字节码和长常量池，类的字节码加载后存放在这个区域，这和存放对象实例的堆区是不同的，大多数JVM的实现都不会对永久带进行垃圾回收，因此，只要类加载的过多就会出现这个问题。一般的应用程序都不会产生这个错误，然而，对于Web服务器来讲，会产生有大量的JSP，JSP在运行时被动态的编译成Java Servlet类，然后加载到方法区，因此，太多的JSP的Web工程可能产生这个异常。

对于第3种异常，本质原因是创建了太多的线程，而能创建的线程数是有限制的，导致了这种异常的发生。

对于第4种异常，是在并行或者并发回收器在GC回收时间过长、超过98%的时间用来做GC并且回收了不到2%的堆内存，然后抛出这种异常进行提前预警，用来避免内存过小造成应用不能正常工作。

* 下面两个异常与OOM有关系，但是，又没有绝对关系。

```
java.lang.StackOverflowError …

java.net.SocketException: Too many open files
```

* 对于第1种异常，是JVM的线程由于递归或者方法调用层次太多，占满了线程堆栈而导致的，线程堆栈默认大小为1M。

* 对于第2种异常，是由于系统对文件句柄的使用是有限制的，而某个应用程序使用的文件句柄超过了这个限制，就会导致这个问题。

上面介绍了OOM相关的基础知识，接下来我们开始讲述笔者经历的一次OOM问题的定位和解决的过程。

## 产生问题的现象

在某一段时间内，我们发现不同的业务服务开始偶发的报OOM的异常，有的时候是白天发生，有的时候是晚上发生，有的时候是基础服务A发生，有的时候是上层服务B发生，有的时候是上层服务C发生，有的时候是下层服务D发生，丝毫看不到一点规律。

产生问题的异常如下：

```
Caused by: java.lang.OutOfMemoryError: unable to create new native thread at java.lang.Thread.start0(Native Method)
at java.lang.Thread.start(Thread.java:597)
at java.util.Timer.<init>(Timer.java:154)
```

## 解决问题的思路和过程

经过细心观察发现，产生问题虽然在不同的时间发生在不同的服务池，但是，晚上0点发生的时候概率较大，也有其他时间偶发，但是都在整点。

这个规律很重要，虽然不是一个时间，但是基本都在整点左右发生，并且晚上0点居多。从这个角度思考，整点或者0点系统是否有定时，与出问题的每个业务系统技术负责人核实，0点没有定时任务，其他时间的整点有定时任务，但是与发生问题的时间不吻合，这个思路行不通。

到现在为止，从现象的规律上我们已经没法继续分析下去了，那我们回顾一下错误本身：

>java.lang.OutOfMemoryError: unable to create new native thread

顾名思义，错误产生的原因就是应用不能创建线程了，但是，应用还需要创建线程。为什么程序不能创建线程呢？

有两个具体原因造成这个异常:

```
由于线程使用的资源过多，操作系统已经不能再提供给应用资源了。

操作系统设置了应用创建线程的最大数量，并且已经达到了最大允许数量。
```

上面第1条资源指的是内存，而第2条中，在Linux下线程使用轻量级进程实现的，因此线程的最大数量也是操作系统允许的进程的最大数量。

* 内存计算

操作系统中的最大可用内存除去操作系统本身使用的部分，剩下的都可以为某一个进程服务，在JVM进程中，内存又被分为堆、本地内存和栈等三大块，Java堆是JVM自动管理的内存，应用的对象的创建和销毁、类的装载等都发生在这里，本地内存是Java应用使用的一种特殊内存，JVM并不直接管理其生命周期，每个线程也会有一个栈，是用来存储线程工作过程中产生的方法局部变量、方法参数和返回值的，每个线程对应的栈的默认大小为1M。

Linux和JVM的内存管理示意图如下：

![](http://mmbiz.qpic.cn/mmbiz_jpg/odp4zTVAogo5XkPb5f7cibDtDbGb5HUqBhBLwQDAFPtTbjwhCXrTDaf7KQjCASp4XJ896CaP7wYPwUNCWYicEeUw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)















