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

没有直接设置老年代的参数，但是可以设置堆空间大小和新生代空间大小两个参数来间接控制。

>老年代空间大小=堆空间大小-年轻代大空间大小

从更高的一个维度再次来看JVM和系统调用之间的关系

![](https://mmbiz.qpic.cn/mmbiz_png/PgqYrEEtEnoUSbbnzEiafyyQWUibOfnE3G1sZG1aJZSakhFe5d6QeiciaO9ZIDfHrFS9UZx8RfWfkPk9UZLCVdcriaQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

方法区和对是所有线程共享的内存区域；而java栈、本地方法栈和程序员计数器是运行是线程私有的内存区域。

下面我们详细介绍每个区域的作用

## Java堆（Heap）

对于大多数应用来说，Java堆（Java Heap）是Java虚拟机所管理的内存中最大的一块。Java堆是被所有线程共享的一块内存区域，在虚拟机启动时创建。此内存区域的唯一目的就是存放对象实例，几乎所有的对象实例都在这里分配内存。

Java堆是垃圾收集器管理的主要区域，因此很多时候也被称做“GC堆”。如果从内存回收的角度看，由于现在收集器基本都是采用的分代收集算法，	
>所以Java堆中还可以细分为：新生代和老年代；	
>再细致一点的有Eden空间、From Survivor空间、To Survivor空间等。

根据Java虚拟机规范的规定，Java堆可以处于物理上不连续的内存空间中，只要逻辑上是连续的即可，就像我们的磁盘空间一样。在实现时，既可以实现成固定大小的，也可以是可扩展的，不过当前主流的虚拟机都是按照可扩展来实现的（通过-Xmx和-Xms控制）。

如果在堆中没有内存完成实例分配，并且堆也无法再扩展时，将会抛出OutOfMemoryError异常。

## 方法区（Method Area）
方法区（Method Area）与Java堆一样，是各个线程共享的内存区域，它用于存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。虽然Java虚拟机规范把方法区描述为堆的一个逻辑部分，但是它却有一个别名叫做Non-Heap（非堆），目的应该是与Java堆区分开来。

对于习惯在HotSpot虚拟机上开发和部署程序的开发者来说，很多人愿意把方法区称为“永久代”（Permanent Generation），本质上两者并不等价，仅仅是因为HotSpot虚拟机的设计团队选择把GC分代收集扩展至方法区，或者说使用永久代来实现方法区而已。

Java虚拟机规范对这个区域的限制非常宽松，除了和Java堆一样不需要连续的内存和可以选择固定大小或者可扩展外，还可以选择不实现垃圾收集。相对而言，垃圾收集行为在这个区域是比较少出现的，但并非数据进入了方法区就如永久代的名字一样“永久”存在了。这个区域的内存回收目标主要是针对常量池的回收和对类型的卸载，一般来说这个区域的回收“成绩”比较难以令人满意，尤其是类型的卸载，条件相当苛刻，但是这部分区域的回收确实是有必要的。

根据Java虚拟机规范的规定，当方法区无法满足内存分配需求时，将抛出OutOfMemoryError异常。

方法区有时被称为持久代（PermGen）。

![](http://mmbiz.qpic.cn/mmbiz_png/PgqYrEEtEnoL6lB6hGicsicgcT50EBbI0CicvmOXXLKcdAmJVia32ITn6gWezTRCuficFIgibcgDiaBUibjicaQyO7blCyQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

所有的对象在实例化后的整个运行周期内，都被存放在堆内存中。
>堆内存又被划分成不同的部分：伊甸区(Eden)，幸存者区域(Survivor Sapce)，老年代（Old Generation Space）。

方法的执行都是伴随着线程的。原始类型的本地变量以及引用都存放在线程栈中。而引用关联的对象比如String，都存在在堆中。为了更好的理解上面这段话，我们可以看一个例子：

```
import java.text.SimpleDateFormat;
import java.util.Date;
import org.apache.log4j.Logger;
public class HelloWorld {
    private static Logger LOGGER = Logger.getLogger(HelloWorld.class.getName());
 
    public void sayHello(String message) {
        SimpleDateFormat formatter = new SimpleDateFormat("dd.MM.YYYY");
        String today = formatter.format(new Date());
        LOGGER.info(today + ": " + message);
    }
}

```

这段程序的数据在内存中的存放如下：

![](http://mmbiz.qpic.cn/mmbiz_png/PgqYrEEtEnoL6lB6hGicsicgcT50EBbI0CMiazSMwukWpGox7ns74yo5Ke8iaPpD6bXgWnT2T87RFyEoDXAia06P34g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

通过JConsole工具可以查看运行中的Java程序（比如Eclipse）的一些信息：堆内存的分配，线程的数量以及加载的类的个数；

![](http://mmbiz.qpic.cn/mmbiz_png/PgqYrEEtEnoL6lB6hGicsicgcT50EBbI0Cdgw9jArfdDicTUlyicGNQsrE7abLJMlCzAKqDYwK9LfiaLug4UycK3jlQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

## 程序计数器（Program Counter Register）
>程序计数器（Program Counter Register）是一块较小的内存空间，它的作用可以看做是当前线程所执行的字节码的行号指示器。在虚拟机的概念模型里（仅是概念模型，各种虚拟机可能会通过一些更高效的方式去实现），字节码解释器工作时就是通过改变这个计数器的值来选取下一条需要执行的字节码指令，分支、循环、跳转、异常处理、线程恢复等基础功能都需要依赖这个计数器来完成。

由于Java虚拟机的多线程是通过线程轮流切换并分配处理器执行时间的方式来实现的，在任何一个确定的时刻，一个处理器（对于多核处理器来说是一个内核）只会执行一条线程中的指令。因此，为了线程切换后能恢复到正确的执行位置，每条线程都需要有一个独立的程序计数器，各条线程之间的计数器互不影响，独立存储，我们称这类内存区域为“线程私有”的内存。

如果线程正在执行的是一个Java方法，这个计数器记录的是正在执行的虚拟机字节码指令的地址；如果正在执行的是Natvie方法，这个计数器值则为空（Undefined）。

>此内存区域是唯一一个在Java虚拟机规范中没有规定任何OutOfMemoryError情况的区域。

## JVM栈（JVM Stacks）

与程序计数器一样，Java虚拟机栈（Java Virtual Machine Stacks）也是线程私有的，它的生命周期与线程相同。
>虚拟机栈描述的是Java方法执行的内存模型：每个方法被执行的时候都会同时创建一个栈帧（Stack Frame）用于存储局部变量表、操作栈、动态链接、方法出口等信息。每一个方法被调用直至执行完成的过程，就对应着一个栈帧在虚拟机栈中从入栈到出栈的过程。

局部变量表存放了编译期可知的各种基本数据类型（boolean、byte、char、short、int、float、long、double）、对象引用（reference类型，它不等同于对象本身，根据不同的虚拟机实现，它可能是一个指向对象起始地址的引用指针，也可能指向一个代表对象的句柄或者其他与此对象相关的位置）和returnAddress类型（指向了一条字节码指令的地址）。

其中64位长度的long和double类型的数据会占用2个局部变量空间（Slot），其余的数据类型只占用1个。局部变量表所需的内存空间在编译期间完成分配，当进入一个方法时，这个方法需要在帧中分配多大的局部变量空间是完全确定的，在方法运行期间不会改变局部变量表的大小。

在Java虚拟机规范中，对这个区域规定了两种异常状况：

```
如果线程请求的栈深度大于虚拟机所允许的深度，将抛出StackOverflowError异常；
如果虚拟机栈可以动态扩展（当前大部分的Java虚拟机都可动态扩展，只不过Java虚拟机规范中也允许固定长度的虚拟机栈），
当扩展时无法申请到足够的内存时会抛出OutOfMemoryError异常。
```

## 本地方法栈（Native Method Stacks）
本地方法栈（Native Method Stacks）与虚拟机栈所发挥的作用是非常相似的，其区别不过是虚拟机栈为虚拟机执行Java方法（也就是字节码）服务，而本地方法栈则是为虚拟机使用到的Native方法服务。虚拟机规范中对本地方法栈中的方法使用的语言、使用方式与数据结构并没有强制规定，因此具体的虚拟机可以自由实现它。甚至有的虚拟机（譬如Sun HotSpot虚拟机）直接就把本地方法栈和虚拟机栈合二为一。
>与虚拟机栈一样，本地方法栈区域也会抛出StackOverflowError和OutOfMemoryError异常。














