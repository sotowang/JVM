# 腾讯IEG（offer）
## 一面（全程问基础）：

```
1、介绍项目
2、String、StringBuffer、StringBuilder的区别，怎么理解String不变性
3、==和equals的区别，如果重写了equals()不重写hashCode()会发生什么
4、volatile怎么保证可见性，synchronized和lock的区别，synchronized的底层实现
5、sleep和wait的区别，sleep会不会释放锁，notify和notifyAll的区别
6、了不了解线程的局部变量，讲讲线程池参数
7、什么情况会发生死锁，死锁的处理方法
8、Cookie和Session的区别，怎么防止Cookie欺骗
9、从用户在浏览器输入域名，到浏览器显示出页面的过程
```

---

### [String、StringBuffer、StringBuilder的区别，怎么理解String不变性](https://www.cnblogs.com/xudong-bupt/p/3961159.html)

##### [String、StringBuffer、StringBuilder的区别，怎么理解String不变性 ](https://blog.csdn.net/chenliguan/article/details/51911906)
---
##### [==和equals的区别，如果重写了equals()不重写hashCode()会发生什么](https://blog.csdn.net/woailuo453786790/article/details/49779869)
##### [==和equals的区别，如果重写了equals()不重写hashCode()会发生什么](https://blog.csdn.net/javazejian/article/details/51348320)
##### [==和equals的区别，如果重写了equals()不重写hashCode()会发生什么](https://blog.csdn.net/neosmith/article/details/17068365)
##### [==和equals的区别，如果重写了equals()不重写hashCode()会发生什么](https://blog.csdn.net/u013679744/article/details/57074669)
---
##### [volatile怎么保证可见性](http://www.tianshouzhi.com/api/tutorials/mutithread/286)
##### [并发编程的锁机制：synchronized和lock](https://juejin.im/post/5a43ad786fb9a0450909cb5f)
##### [synchronized的底层实现](https://blog.csdn.net/javazejian/article/details/72828483)
##### [synchronized的底层实现](https://blog.csdn.net/chenssy/article/details/54883355)
---
##### [sleep和wait的区别，sleep会不会释放锁](https://www.zhihu.com/question/23328075)
![](https://pic2.zhimg.com/80/bb4f380c79779c9dc1aea6f0a6c10b6d_hd.jpg)
##### [notify和notifyAll的区别](https://www.zhihu.com/question/37601861)
---

##### [线程的局部变量t和成员变量](https://www.cnblogs.com/mengdd/archive/2013/02/16/2913659.html)
##### [线程池参数](https://liuzho.github.io/2017/04/17/%E7%BA%BF%E7%A8%8B%E6%B1%A0%EF%BC%8C%E8%BF%99%E4%B8%80%E7%AF%87%E6%88%96%E8%AE%B8%E5%B0%B1%E5%A4%9F%E4%BA%86/)
---
##### [什么情况会发生死锁，死锁的处理方法](https://blog.csdn.net/a1414345/article/details/70215628)
---
##### [Cookie和Session的区别](https://blog.csdn.net/baidu_31337243/article/details/48954445)
##### [怎么防止Cookie欺骗](https://blog.csdn.net/sollion/article/details/6769798)
---
##### [从用户在浏览器输入域名，到浏览器显示出页面的过程](https://blog.csdn.net/qq_24147051/article/details/81115806)
---



## 二面（全程怼项目，压力面）：

##### [1. 谈谈对UDF的理解，写UDF的目的，代码怎么写的](https://blog.csdn.net/WYpersist/article/details/80314352)
[UDFgithub](https://github.com/sotowang/udf)
```
Hive中有3种UDF：
	UDF：操作单个数据行，产生单个数据行；
	UDAF：操作多个数据行，产生一个数据行。
	UDTF：操作一个数据行，产生多个数据行一个表作为输出。
    
用户构建的UDF使用过程如下：
	第一步：继承UDF或者UDAF或者UDTF，实现特定的方法。
	第二步：将写好的类打包为jar。如hivefirst.jar.
	第三步：进入到Hive外壳环境中，利用add jar /home/hadoop/hivefirst.jar.注册该jar文件
	第四步：为该类起一个别名，create temporary function mylength as 'com.whut.StringLength';这里注意UDF只是为这个Hive会话临时定义的。
	第五步：在select中使用mylength();
```

```
1、看你写过UDF，谈谈对UDF的理解，写UDF的目的，代码怎么写的
2、改造hive表后怎么进行数据一致性校验的，有没有自动化流程
3、看你读过kafka源码，讲讲kafka broker的源码里面你最熟悉的类，以及这个类的主要方法，用的什么设计模式
4、项目里面从数据采集到最终的数据可视化，每个环节都有可能丢数据，怎么判断数据有没有丢，如果丢了如何定位到在哪一个环节丢的
5、项目里面为什么要用kafka stream做实时计算，而不是用spark或者flink，kafka sql和spark sql了解过吗
6、项目里面用到了时序数据库opentsdb，为什么要用这个，有没有跟其它的时序数据库对比过
7、平时逛不逛社区，有没有参与过开源项目
8、看你春招笔试的时候***作系统得了0分是怎么做到的
```

## 三面（接着怼项目）：

```
1、看你写了实时计算的程序，你怎么保证计算的结果肯定是对的
2、数据接入的时候，怎么往kafka topic里面发的，用的什么方式，起了几个线程，producer是线程安全的吗
3、kafka集群有几台机器，怎么确定你们项目需要用几台机器，有评估过吗，吞吐量测过吗
4、spark streaming是怎么跟kafka交互的，具体代码怎么写的，程序执行流程是怎样的，这个过程中怎么确保数据不丢
5、kafka监控是怎么做的，kafka中能彻底删除数据吗，怎么做的
```

## 面委会（全程聊天）：
* 平时是怎么学习的，爱看哪些博客，怎么看待加班，有没有成为leader的潜力

# 网易考拉（offer）
## 一面：

```
1、sql题：学生成绩表，把每科最高分前三名统计出来
2、算法题：二维数组中的查找
3、kafka如何保证高吞吐的，了不了解kafka零拷贝，具体怎么做的
4、sql有几种join，map join了解过没
5、hbase中row key该怎么设计
6、hdfs文件上传流程，hdfs的容错机制
7、怎么解决hive数据倾斜问题
```

## 二面（全程写写写）：

```
1、算法题：二维矩阵相乘
2、算法题：链表中环的入口
3、写一下mysql binlog的数据格式，怎么进行数据清洗的
4、写一个正则表达式进行手机号匹配
5、讲一下数据仓库层级的划分，每层的作用
```

# 美团新到店（offer）
* 去了北京美团公司里面试，一上午面完，第二天通知高分通过
## 一面（简单的聊了聊，10min）：

```
1、介绍项目，以及滴滴的实习经历
2、JVM内存的划分
3、垃圾收集算法
4、数据建模，星型模型和雪花模型
5、数仓层级的划分，怎么对接到mysql拿数据
```

## 二面：

```
1、sql题：写一条sql删除订单表中重复的记录
2、sql题：一张网页浏览信息表，
	有两列，一列是网页ip，一列是浏览网页的用户（比如a或者b、c、d直到z），
    求这些网页被a和b或者a和c或者b和c两两组合访问的次数
3、hive数据倾斜产生的原因，怎么解决
4、设计学生成绩管理系统，符合第三范式要求，并绘出UML图
5、算法题：斐波那契数列
6、spark程序的运行流程
7、spark streaming从kafka中读数据的两种方式
8、讲讲数据库索引，B树和B+树
9、Elasticsearch的索引，单field索引和多field的联合索引
10、linux查看某文件的大小，vim中怎么替换内容
11、海量数据的Count问题（单机），如果把大文件hash成不同的小文件，此时小文件装不下某个key对应的数据，该怎么办
12、智力题：8升水，有一个5L的杯子和3L的杯子，怎么得到4升水
```

## 三面：

```
1、osi七层模型，三次握手和四次挥手，为什么两次握手不行
2、kafka怎么保证高吞吐量，项目中有测过吞吐量吗，相比于其它MQ，为什么会选择kafka，kafka怎么保证exactly once语义
3、了解hbase吗，hbase为什么查询速度快
4、hive sql怎么转换成底层的MapReduce程序，以及shuffle的过程
5、算法题：被围绕的区域，leetcode第130题原题
6、智力题：一头母牛每年生一头小母牛，每头小母牛从第四年开始，每年也会生一头小母牛，写个公式求第n年会有多少头牛
```

# 小米（offer）
## 一面：

```
1、java和python的区别，对面向对象的理解，和面向过程相比有什么区别
2、java为什么不能多继承
3、讲一下java抽象类和接口
4、java中为什么要写非static方法
5、volatile和synchronized的区别
6、算法题：跳台阶问题
7、算法题：树的非递归后序遍历
8、设计题：一个停车场有一些大车位和小车位，大车只能停大车位，小车既能停大车位又能停小车位，实现这种场景下的调度系统
```

## 二面：

```
1、算法题：输入一个字符串，输出该字符串中字符的所有排列
```

# 贝壳（offer）
## 一面：

```
1、synchronized的底层实现
2、线程等待时位于哪个区域，具体讲一下
3、谈谈对kafka的理解，能讲多少讲多少
4、算法题：二分查找
5、快排的时间复杂度和空间复杂度，最优情况和最差情况分别是多少，是稳定排序吗，快排为什么快
```

## 二面：

```
1、介绍项目，项目中涉及到了一些算法，介绍一下
2、两道算法题：路径问题，leetcode上63题和64题原题
3、写正则表达式匹配电话号码
4、智力题：一张圆桌子，我和面试官轮流往桌子上放硬币（随便放），直到桌子放不下为止，最后一个放硬币的人赢，如果我先放，怎么保证我肯定赢
```

# 华为（录用排序）
## 一轮玄学面：
* 面试官是做安卓的，瞧不起大数据，觉得大数据很虚，我跟他bb了一堆。然后问我有没有女朋友，我说以前有，现在分了；问我什么时候谈的，什么时候分的，我说本科谈的，毕业分了；问我为什么要分，此处省略一万字......问我现在想没想过再谈，我说毕竟转专业过来的，想趁在校期间利用好短暂的时光提升自己的技术水平（其实因为找不到）；然后面试官说以后工作了就不好找咯，我说您说的有道理............

# 快手（待hr面）
## 一面：

```
1、jvm类加载机制，类加载器，双亲委派模型
2、java实现多线程的方式
3、spark怎么划分stage，宽窄依赖，各包括哪些***作
4、zookeeper怎么保证原子性，怎么实现分布式锁
5、写个快排，为什么要用三数取中法，好处是什么
```

---

### java实现多线程的方式

[java实现多线程的方式](https://blog.csdn.net/aboy123/article/details/38307539)

JAVA多线程实现方式主要有三种：

```
继承Thread类、实现Runnable接口、使用ExecutorService、Callable、Future实现有返回结果的多线程。
其中前两种方式线程执行完后都没有返回值，只有最后一种是带返回值的。
```

* 1、继承Thread类实现多线程


> 继承Thread类的方法尽管被我列为一种多线程实现方式，但Thread本质上也是实现了Runnable接口的一个实例，
> 它代表一个线程的实例，并且，启动线程的唯一方法就是通过Thread类的start()实例方法。start()方法是一个native方法，它将启动一个新线程，并执行run()方法。这种方式实现多线程很简单，通过自己的类直接extend Thread，并复写run()方法，就可以启动新线程并执行自己定义的run()方法。例如：

```
public class MyThread extends Thread {
　　public void run() {
　　 System.out.println("MyThread.run()");
　　}
}

```

在合适的地方启动线程如下：

```
MyThread myThread1 = new MyThread();
MyThread myThread2 = new MyThread();
myThread1.start();
myThread2.start();
```

* 2、实现Runnable接口方式实现多线程	


如果自己的类已经extends另一个类，就无法直接extends Thread，此时，必须实现一个Runnable接口，如下：

```
public class MyThread extends OtherClass implements Runnable {
　　public void run() {
　　 System.out.println("MyThread.run()");
　　}
}
```

为了启动MyThread，需要首先实例化一个Thread，并传入自己的MyThread实例：

```
MyThread myThread = new MyThread();
Thread thread = new Thread(myThread);
thread.start();
```

事实上，当传入一个Runnable target参数给Thread后，Thread的run()方法就会调用target.run()，参考JDK源代码：

```
public void run() {
　　if (target != null) {
　　 target.run();
　　}
}
```

* 3、使用ExecutorService、Callable、Future实现有返回结果的多线程	
ExecutorService、Callable、Future这个对象实际上都是属于Executor框架中的功能类。想要详细了解Executor框架的可以访问http://www.javaeye.com/topic/366591 ，这里面对该框架做了很详细的解释。返回结果的线程是在JDK1.5中引入的新特征，确实很实用，有了这种特征我就不需要再为了得到返回值而大费周折了，而且即便实现了也可能漏洞百出。
可返回值的任务必须实现Callable接口，类似的，无返回值的任务必须Runnable接口。执行Callable任务后，可以获取一个Future的对象，在该对象上调用get就可以获取到Callable任务返回的Object了，再结合线程池接口ExecutorService就可以实现传说中有返回结果的多线程了。下面提供了一个完整的有返回结果的多线程测试例子，在JDK1.5下验证过没问题可以直接使用。代码如下：

```
import java.util.concurrent.*;
import java.util.Date;
import java.util.List;
import java.util.ArrayList;
 
/**
* 有返回值的线程
*/
@SuppressWarnings("unchecked")
public class Test {
public static void main(String[] args) throws ExecutionException,
    InterruptedException {
   System.out.println("----程序开始运行----");
   Date date1 = new Date();
 
   int taskSize = 5;
   // 创建一个线程池
   ExecutorService pool = Executors.newFixedThreadPool(taskSize);
   // 创建多个有返回值的任务
   List<Future> list = new ArrayList<Future>();
   for (int i = 0; i < taskSize; i++) {
    Callable c = new MyCallable(i + " ");
    // 执行任务并获取Future对象
    Future f = pool.submit(c);
    // System.out.println(">>>" + f.get().toString());
    list.add(f);
   }
   // 关闭线程池
   pool.shutdown();
 
   // 获取所有并发任务的运行结果
   for (Future f : list) {
    // 从Future对象上获取任务的返回值，并输出到控制台
    System.out.println(">>>" + f.get().toString());
   }
 
   Date date2 = new Date();
   System.out.println("----程序结束运行----，程序运行时间【"
     + (date2.getTime() - date1.getTime()) + "毫秒】");
}
}
 
class MyCallable implements Callable<Object> {
private String taskNum;
 
MyCallable(String taskNum) {
   this.taskNum = taskNum;
}
 
public Object call() throws Exception {
   System.out.println(">>>" + taskNum + "任务启动");
   Date dateTmp1 = new Date();
   Thread.sleep(1000);
   Date dateTmp2 = new Date();
   long time = dateTmp2.getTime() - dateTmp1.getTime();
   System.out.println(">>>" + taskNum + "任务终止");
   return taskNum + "任务返回运行结果,当前任务时间【" + time + "毫秒】";
}
}

```

代码说明：
>上述代码中Executors类，提供了一系列工厂方法用于创先线程池，返回的线程池都实现了ExecutorService接口。	
public static ExecutorService newFixedThreadPool(int nThreads) 	
创建固定数目线程的线程池。	
public static ExecutorService newCachedThreadPool() 	
创建一个可缓存的线程池，调用execute 将重用以前构造的线程（如果线程可用）。如果现有线程没有可用的，则创建一个新线程并添加到池中。终止并从缓存中移除那些已有 60 秒钟未被使用的线程。	
public static ExecutorService newSingleThreadExecutor() 	
创建一个单线程化的Executor。	
public static ScheduledExecutorService newScheduledThreadPool(int corePoolSize) 	
创建一个支持定时及周期性的任务执行的线程池，多数情况下可用来替代Timer类。

ExecutoreService提供了submit()方法，传递一个Callable，或Runnable，返回Future。如果Executor后台线程池还没有完成Callable的计算，这调用返回Future对象的get()方法，会阻塞直到计算完成。


---
### Spark中的宽窄依赖和Stage的划分

[Spark中的宽窄依赖和Stage的划分](https://blog.csdn.net/LHWorldBlog/article/details/79300039)

#### 前述

RDD之间有一系列的依赖关系，依赖关系又分为窄依赖和宽依赖。

Spark中的Stage其实就是一组并行的任务，任务是一个个的task 。

#### 具体细节
* 窄依赖	
父RDD和子RDD partition之间的关系是一对一的。或者父RDD一个partition只对应一个子RDD的partition情况下的父RDD和子RDD partition关系是多对一的。不会有shuffle的产生。父RDD的一个分区去到子RDD的一个分区。

---
## 二面：

```
1、sql题：找出单科成绩高于该科平均成绩的同学名单（无论该学生有多少科，只要有一科满足即可）
2、sql题：找出单科成绩高于该科平均成绩的同学名单（该学生所有科都必须满足）
3、算法题：求数组中连续子数组的最大和
4、算法题：使用最小花费爬楼梯，leetcode746题原题
```

## 三面：

```
1、讲一下java IO
2、算法题：输入n个整数，找出其中最大的k个数
3、算法题：给一个整数数组和一个目标值，找出数组中和为目标值的两个数
```

--------------------------写的头疼，明天接着更-------------------------------------------
# 完美世界（offer）

# 京东广告部（四面完没了消息）

# 阿里菜鸟（三面完已回绝）
* 阿里的面试还是比较重视基础的，应该是bat里面问基础问的最多的

## 一面：

```
1、HashMap和HashTable的区别，HashMap怎么解决hash冲突，jdk1.8后对HashMap的改进
2、讲讲ConcurrentHashMap，ConcurrentHashMap怎么保证线程安全，HashTable怎么保证线程安全
3、HashSet的底层实现，是不是线程安全的
4、ArrayList和LinkedList的区别，是不是线程安全的
5、讲讲设计模式，最常用哪种设计模式，单例模式的实现方式
6、进程和线程，Java实现多线程的方式，什么是线程安全，怎么保证多线程线程安全
7、可重入锁的可重入性是什么意思，哪些是可重入锁
8、为什么要用线程池，线程池的好处
9、JVM垃圾处理方法，对象什么时候进入老年代，什么时候进行FullGC
10、Java堆溢出问题怎么处理，内存泄漏和内存溢出的区别
11、智力题：50个红球和50个黑球往两个桶里放，然后自己去抽，怎么样才能使抽到红球的概率最高
```

---
### Java堆溢出问题怎么处理，内存泄漏和内存溢出的区别
[Java堆溢出问题怎么处理，内存泄漏和内存溢出的区别](https://blog.csdn.net/sinat_35512245/article/details/54866068)

[Java内存泄漏与内存溢出详解](https://blog.csdn.net/sinat_35512245/article/details/54866068)

* 内存泄漏指你用malloc或new申请了一块内存，但是没有通过free或delete将内存释放，导致这块内存一直处于占用状态。

* 内存溢出指你申请了10个字节的空间，但是你在这个空间写入11或以上字节的数据，就是溢出。

内存泄露是指程序中间动态分配了内存，但在程序结束时没有释放这部分内存，从而造成那部分内存不可用的情况，重启计算机可以解决，但也有可能再次发生内存泄露，内存泄露和硬件没有关系，它是由软件设计缺陷引起的。

内存泄漏可以分为4类： 

* 1)常发性内存泄漏。
>发生内存泄漏的代码会被多次执行到，每次被执行的时候都会导致一块内存泄漏。

* 2)偶发性内存泄漏。
>发生内存泄漏的代码只有在某些特定环境或操作过程下才会发生。常发性和偶发性是相对的。对于特定的环境，偶发性的也许就变成了常发性的。所以测试环境和测试方法对检测内存泄漏至关重要。

* 3)一次性内存泄漏。
> 发生内存泄漏的代码只会被执行一次，或者由于算法上的缺陷，导致总会有一块仅且一块内存发生泄漏。比如，在类的构造函数中分配内存，在析构函数中却没有释放该内存，所以内存泄漏只会发生一次。

* 4)隐式内存泄漏。
>程序在运行过程中不停的分配内存，但是直到结束的时候才释放内存。严格的说这里并没有发生内存泄漏，因为最终程序释放了所有申请的内存。但是对于一个服务器程序，需要运行几天，几周甚至几个月，不及时释放内存也可能导致最终耗尽系统的所有内存。所以，我们称这类内存泄漏为隐式内存泄漏。

内存溢出即用户在对其数据缓冲区操作时，超过了其缓冲区的边界；尤其是对缓冲区写操作时，缓冲区的溢出很可能导致程序的异常。

* Java内存泄露与溢出的区别

```
内存溢出就是你要求分配的内存超出了系统能给你的，系统不能满足需求，于是产生溢出。

Java内存泄漏就是没有及时清理内存垃圾，导致系统无法再给你提供内存资源（内存资源耗尽）。
```

看到上面的解释，可能有些朋友还是不太理解吧。没问题，看以下例子:

* 1.Java内存泄露是说程序逻辑问题,造成申请的内存无法释放.这样的话无论多少内存,早晚都会被占用光的. 最简单的例子就是死循环了.由于程序判断错误导经常发生此事。

* 2.Java内存泄漏是指在堆上分配的内存没有被释放，从而失去对其控制。这样会造成程序能使用的内存越来越少，导致系统运行速度减慢，严重情况会使程序当掉。

* 3.关于内存溢出有点出入。比如说你申请了一个integer,但给它存了long才能存下的数，那就是内存溢出。

举个现实中的例子： 
>比如有一个桶，装满了水.你丢个苹果进去。桶的水正常。如果你放个大石头。水就出溢出，内存溢出也就是这个原理。 

区别：

* 内存溢出，提供的内存不够；
* Java内存泄漏，无法再提供内存资源。

### 相关问题


Q:Java中会存在内存泄漏吗？ 	
A:  	Java中也存在内存泄露。	当被分配的对象可达但已无用（未对作废数据内存单元的引用置null）即会引起。

Q: 如何避免内存泄露、溢出？ 	
A: 
* 1)尽早释放无用对象的引用。	
好的办法是使用临时变量的时候，让引用变量在退出活动域后自动设置为null，暗示垃圾收集器来收集该对象，防止发生内存泄露。

* 2)程序进行字符串处理时，尽量避免使用String，而应使用StringBuffer。

[String,StringBuffer与StringBuilder的区别??](https://blog.csdn.net/rmn190/article/details/1492013)

```
简要的说， String 类型和 StringBuffer 类型的主要性能区别其实在于 String 是不可变的对象, 因此在每次对 String 类型进行改变的时候其实都等同于生成了一个新的 String 对象，
然后将指针指向新的 String 对象，所以经常改变内容的字符串最好不要用 String ，因为每次生成对象都会对系统性能产生影响，特别当内存中无引用对象多了以后， JVM 的 GC 就会开始工作，那速度是一定会相当慢的。

 而如果是使用 StringBuffer 类则结果就不一样了，每次结果都会对 StringBuffer 对象本身进行操作，而不是生成新的对象，再改变对象引用。
 所以在一般情况下我们推荐使用 StringBuffer ，特别是字符串对象经常改变的情况下。
 而在某些特别情况下， String 对象的字符串拼接其实是被 JVM 解释成了 StringBuffer 对象的拼接，所以这些时候 String 对象的速度并不会比 StringBuffer 对象慢，
 而特别是以下的字符串对象生成中， String 效率是远要比 StringBuffer 快的：
 String S1 = “This is only a” + “ simple” + “ test”;
 StringBuffer Sb = new StringBuilder(“This is only a”).append(“ simple”).append(“ test”);
 
 你会很惊讶的发现，生成 String S1 对象的速度简直太快了，而这个时候 StringBuffer 居然速度上根本一点都不占优势。其实这是 JVM 的一个把戏，在 JVM 眼里，这个
 
String S1 = “This is only a” + “ simple” + “test”; 其实就是：
String S1 = “This is only a simple test”; 
所以当然不需要太多的时间了。但大家这里要注意的是，如果你的字符串是来自另外的 String 对象的话，速度就没那么快了，譬如：
String S2 = “This is only a”;
String S3 = “ simple”;
String S4 = “ test”;
String S1 = S2 +S3 + S4;

这时候 JVM 会规规矩矩的按照原来的方式去做
```

* 3) 尽量少用静态变量。因为静态变量是全局的，GC不会回收。

* 4)避免集中创建对象尤其是大对象，如果可以的话尽量使用流操作。

* 5)尽量运用对象池技术以提高系统性能。	
生命周期长的对象拥有生命周期短的对象时容易引发内存泄漏，例如大集合对象拥有大数据量的业务对象的时候，可以考虑分块进行处理，然后解决一块释放一块的策略。

* 6)不要在经常调用的方法中创建对象，尤其是忌讳在循环中创建对象。
可以适当的使用hashtable，vector创建一组对象容器，然后从容器中去取那些对象，而不用每次new之后又丢弃。

* 7) 优化配置。

---
### Java对象池技术

[Java对象池技术](https://www.jianshu.com/p/38c5bccf892f)

#### 为什么用对象池
在 java 中，对象的生命周期包括对象创建、对象使用，对象消失三个时间段，其中对象的使用是对象真正需要存活的时间，不好修改，该用的时候还得使用啊。对象的创建和消失就得好好控制下了。对象的创建是比较费时间的，也许感觉不到，好比一个赋值操作int i=1，也是需要耗时的，在比如构造一个对象，一个数组就更加消耗时间。再说对象的消除，在 java 里面使用 GC 来进行对象回收，其实也是需要对对象监控每一个运行状态，包括引用，赋值等。在 Full GC 的时候，会暂停其他操作，独占 CPU。所以，我们需要控制对象的创建数量，也不要轻易的让对象消失，让他的复用更加充分。

### 对象池
对象池其实就是一个集合，里面包含了我们需要的对象集合，当然这些对象都被池化了，也就是被对象池所管理，想要这样的对象，从池子里取个就行，但是用完得归还。对象池的对象最好是创建比较费时的大对象，如果是太简单的对象，再进入池化的时间比自己构建还多，就不划算了。可以理解对象池为单例模式的延展，多例模式，就那么几个对象实例，再多没有了。

书上说这个模式会用在数据库连接的管理上。比如，每个用户的连接数是有限的，这样每个连接就是一个池子里的一个对象，“连接池”类就可以控制连接数了。

### 自定义一个低质量的对象池
首先构造一个池化对象，也就是对实际对象封装下,为什么呢？当然是为了让对象池更好的管理

```
public  class PooledObject<T> {

 private T objection = null;// 外界使用的对象
 private boolean busy = false; // 此对象是否正在使用的标志，默认没有正在使用

 // 构造函数，池化对象
 public PooledObject(T objection) {
  this.objection = objection;
 }

 // 返回此对象中的对象
 public T getObject() {
  return objection;
 }

 // 设置此对象的，对象
 public void setObject(T objection) {
  this.objection = objection;
 }

 // 获得对象对象是否忙
 public boolean isBusy() {
  return busy;
 }

 // 设置对象的对象正在忙
 public void setBusy(boolean busy) {
  this.busy = busy;
 }
 
 
}
```

池化对象现在包括两个属性，一个是原始对象的引用，另外一个表示当前对象是否在使用

接下来把对象池写出来

```
import java.util.Enumeration;
import java.util.Vector;

public abstract class ObjectPool<T> {
    public static int numObjects = 10; // 对象池的大小
    public static int maxObjects = 50; // 对象池最大的大小
    protected Vector<PooledObject<T>> objects = null; // 存放对象池中对象的向量(PooledObject类型)

    public ObjectPool() {
    }

    /*** 创建一个对象池 ***/
    public synchronized void createPool() {
        // 确保对象池没有创建。如果创建了，保存对象的向量 objects 不会为空
        if (objects != null) {
            return; // 如果己经创建，则返回
        }
        // 创建保存对象的向量 , 初始时有 0 个元素
         objects = new Vector<PooledObject<T>>();
         for (int i = 0; i < numObjects; i++) {
                objects.addElement(create());
            }
    }

    public abstract PooledObject<T> create();

    public synchronized T getObject() {
        // 确保对象池己被创建
        if (objects == null) {
            return null; // 对象池还没创建，则返回 null
        }
        T t = getFreeObject(); // 获得一个可用的对象
        // 如果目前没有可以使用的对象，即所有的对象都在使用中
        while (t == null) {
            wait(250);
            t = getFreeObject(); // 重新再试，直到获得可用的对象，如果
            // getFreeObject() 返回的为 null，则表明创建一批对象后也不可获得可用对象
        }
        return t;// 返回获得的可用的对象
    }

    /**
     * 本函数从对象池对象 objects 中返回一个可用的的对象，如果 当前没有可用的对象，则创建几个对象，并放入对象池中。
     * 如果创建后，所有的对象都在使用中，则返回 null
     */
    private T getFreeObject() {
        // 从对象池中获得一个可用的对象
        T obj = findFreeObject();
        if (obj == null) {
            createObjects(10); // 如果目前对象池中没有可用的对象，创建一些对象
            // 重新从池中查找是否有可用对象
            obj = findFreeObject();
            // 如果创建对象后仍获得不到可用的对象，则返回 null
            if (obj == null) {
                return null;
            }
        }
        return obj;
    }

    public void createObjects(int increment){
        for (int i = 0; i < increment; i++) {
            if (objects.size() > maxObjects) {
                return;
            }
            objects.addElement(create());
        }
    }

    /**
     * 查找对象池中所有的对象，查找一个可用的对象， 如果没有可用的对象，返回 null
     */
    private T findFreeObject() {
        T obj = null;
        PooledObject<T> pObj = null;
        // 获得对象池向量中所有的对象
        Enumeration<PooledObject<T>> enumerate = objects.elements();
        // 遍历所有的对象，看是否有可用的对象
        while (enumerate.hasMoreElements()) {
            pObj = (PooledObject<T>) enumerate.nextElement();

            // 如果此对象不忙，则获得它的对象并把它设为忙
            if (!pObj.isBusy()) {
                obj = pObj.getObject();
                pObj.setBusy(true);
            }
        }
        return obj;// 返回找到到的可用对象
    }

    /**
     * 此函数返回一个对象到对象池中，并把此对象置为空闲。 所有使用对象池获得的对象均应在不使用此对象时返回它。
     */

    public void returnObject(T obj) {
        // 确保对象池存在，如果对象没有创建（不存在），直接返回
        if (objects == null) {
            return;
        }
        PooledObject<T> pObj = null;
        Enumeration<PooledObject<T>> enumerate = objects.elements();
        // 遍历对象池中的所有对象，找到这个要返回的对象对象
        while (enumerate.hasMoreElements()) {
            pObj = (PooledObject<T>) enumerate.nextElement();
            // 先找到对象池中的要返回的对象对象
            if (obj == pObj.getObject()) {
                // 找到了 , 设置此对象为空闲状态
                pObj.setBusy(false);
                break;
            }
        }
    }

    /**
     * 关闭对象池中所有的对象，并清空对象池。
     */
    public synchronized void closeObjectPool() {
        // 确保对象池存在，如果不存在，返回
        if (objects == null) {
            return;
        }
        PooledObject<T> pObj = null;
        Enumeration<PooledObject<T>> enumerate = objects.elements();
        while (enumerate.hasMoreElements()) {
            pObj = (PooledObject<T>) enumerate.nextElement();
            // 如果忙，等 0.5 秒
            if (pObj.isBusy()) {
                wait(500); // 等
            }
            // 从对象池向量中删除它
            objects.removeElement(pObj);
        }
        // 置对象池为空
        objects = null;
    }

    /**
     * 使程序等待给定的毫秒数
     */
    private void wait(int mSeconds) {
        try {
            Thread.sleep(mSeconds);
        } catch (InterruptedException e) {
        }
    }
}

为了泛化处理，这个对象池是个抽象类，接下来具体实现一个
public class DefaultObjectPool extends ObjectPool<String> {

    @Override
    public PooledObject<String> create(){
        return new PooledObject<String>(new String(""+1));
    }

}

```

最后测试下：

```
    public static void main(String[] args) {
        ObjectPool<String> objPool = new DefaultObjectPool();
        objPool.createPool();
        String obj = objPool.getObject();
        objPool.returnObject(obj);
        objPool.closeObjectPool();
    }
```

---
## 二面：

```
1、讲讲数据库存储引擎
2、介绍一下索引，索引设置的规则，聚簇索引和非聚簇索引的区别，索引的最左前缀原则
3、用过redis吗，redis支持哪些数据类型，redis与mysql的区别
4、了解垃圾收集器吗，分别介绍介绍
5、jvm调优做过没，-Xms和-Xmx分别指什么
6、算法题：输入两个字符串，输出它们合并排序后的结果
```

## 三面：

```
1、讲讲数据库的范式
2、Linux进程通信和线程通信
3、线程池的参数
4、什么是内部类，什么是匿名内部类
5、设计题：一个市有9个消防站，现在要新增3个消防站，这3个消防站应该放在哪里
```

---
### Java线程池实例解析

[Java线程池实例解析](https://blog.csdn.net/qq_33142257/article/details/75968791)

#### 线程池概念：

首先，要理解什么是线程池；还是先拿具体例子来说，这个例子可能比较偏了，因为现实生活中接触的少了，但是比较能形象的阐述线程池的含义；


>摆渡，在科技不发达的时候，没有能力造那种大桥，人们过河只能通过码头的船夫摆渡到对岸；为了更贴切，我说的这个码头就只做摆渡的生意，其他运输之类的不干；码头的船则是码头的老板创业时自己造的；

>理解上述的背景后，这样我们就可以拿两者来开始类比了；码头就相当于线程池，而码头里的船就是每一条线程；为什么这样说呢，船其实是一个载体，需要执行的任务其实是过河这个动作，线程也是这样，它也是个载体，完成具体的方法是任务；首先假想一个场景，一个书生到了河边要到对岸去（ps：不管他会不会游泳，还是会飞；这里限定他只能通过船这个途径）；那他只有两种选择，第一个是自己造船，第二个是坐码头里摆渡的船；这两种方式不管是哪个都是完成过河的任务，但是你会发现，码头的船很多，当书生坐上船走后，后面又来了几个人也要过河，他们能立马就载上这几个人；

>码头是船的集合，那么线程池就是线程的集合；为什么要弄出个线程池出来呢，差异就显而易见了，码头的船在客户来之前就已经造好放在那儿等待使用，而如果没有码头的话，客户来到这儿要过河只能自己造船，然后才能过河；这是其一，一个要建造船，一个不要，线程池也是这样，如果没有线程池的话，那么某个方法中要使用多线程的时候，需要new一个线程，而线程池则不一样了，当需要使用线程的时候直接去线程池中取一个，省去了创建线程这个环节，提高效率；

>还有就是多个人需要过河，码头有很多船则会大大的提高效率，不仅省去了造船的环节还省去了资源的占用，如果是每个人自己造船的话，岸边的树估计要被砍光了；多个任务需要执行的时候，手动创建线程会占用太多内存资源，而且每个都需要new，浪费了时间；


好了，其实上述的例子已经把线程池以及它的优点都基本表达出来了，但是还是要结合代码具体讲解下，才能更清楚理解；

#### 线程池

创建一个线程集合，池子的大小取决于内存数量；当需要执行一个任务的时候是重用一个等待的线程，而不是重新开启一个线程；当任务执行完成后继续回到池子中等待下一个任务
优点：

```
1、减少在创建和销毁线程上所花的时间和资源开销
2、与主线程隔离，实现异步执行
```
注意：池中的线程数不是越多越好，线程休眠同样也会占用资源，所以要合理的选择线程池大小

#### 线程池的几个实例
基础类：

```
import java.text.SimpleDateFormat;
import java.util.Date;
 
/**
 * Created by zelei.fan on 2017/6/13.
 */
public class ThreadHandle implements Runnable{
 
    private String index;
 
    ThreadHandle(String index){
        this.index = index;
    }
 
    @Override
    public void run() {
        SimpleDateFormat df = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        Date date = new Date();
        String time = df.format(date);
        System.out.println(Thread.currentThread().getName()+"Start Time"+time);
        /*中间一段处理时间*/
        try {
            Thread.sleep(4000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        Date date1 = new Date();
        String time1 = df.format(date1);
        System.out.println(Thread.currentThread().getName()+"End Time"+time1);
    }
}

```

* 1、Executors.newCachedThreadPool()；可缓存的线程池，当线程越多线程池规模也随之扩大,默认超时时间是60s，如果超过会自动终止该线程

```
public static void main(String[] args) {
        /*newCachedThreadPool可缓存线程池同时启动了5个线程来执行*/
        ExecutorService pool = Executors.newCachedThreadPool();
        for (int i = 0; i < 5; i ++){
            pool.execute(new ThreadHandle(String.valueOf(i)));
        }
    }

```

运行结果：

```
pool-1-thread-3Start Time2017-07-24 13:35:28
pool-1-thread-1Start Time2017-07-24 13:35:28
pool-1-thread-5Start Time2017-07-24 13:35:28
pool-1-thread-4Start Time2017-07-24 13:35:28
pool-1-thread-2Start Time2017-07-24 13:35:28
pool-1-thread-2End Time2017-07-24 13:35:32
pool-1-thread-3End Time2017-07-24 13:35:32
pool-1-thread-4End Time2017-07-24 13:35:32
pool-1-thread-1End Time2017-07-24 13:35:32
pool-1-thread-5End Time2017-07-24 13:35:32
```

可以看到线程池同时启动了5个线程来执行任务，理论上可开启的线程数是无限的，但是受cpu的影响，cpu越多的话开的越多；

* 2、Executors.newFixedThreadPool(2)；创建一个固定大小的线程池；当线程达到最大数时，大小不再变化，适用于固定的稳定的并发编程

```
public static void main(String[] args) {
        /*newFixedThreadPool固定线程数的线程池同一时刻最多只开启设定的5个线程，只有当前面的线程结束后才会继续执行后面等待的任务*/
        ExecutorService executorService = Executors.newFixedThreadPool(2);
        for (int i = 0; i < 6; i ++){
            executorService.execute(new ThreadHandle(String.valueOf(i)));
        }
    }

```

运行结果：

```
pool-1-thread-2Start Time2017-07-24 13:42:04
pool-1-thread-1Start Time2017-07-24 13:42:04
pool-1-thread-1End Time2017-07-24 13:42:08
pool-1-thread-2End Time2017-07-24 13:42:08
pool-1-thread-1Start Time2017-07-24 13:42:08
pool-1-thread-2Start Time2017-07-24 13:42:08
pool-1-thread-1End Time2017-07-24 13:42:12
pool-1-thread-2End Time2017-07-24 13:42:12
pool-1-thread-1Start Time2017-07-24 13:42:12
pool-1-thread-2Start Time2017-07-24 13:42:12
pool-1-thread-2End Time2017-07-24 13:42:16
pool-1-thread-1End Time2017-07-24 13:42:16
```

同时开启是个任务来执行，但是线程池大小只有2，一个时间点只能有两个线程并行，其余的任务则必须等待，直到上一个任务执行完成；

* 3、Executors.newSingleThreadExecutor()；创建一个单线程，串行执行

```
public static void main(String[] args) {
        /*newSingleThreadExecutor单线程,同一时刻只有一个线程实例，所有任务都用这个实例执行
        * 相当于Executors.newFixedThreadPool(1)；
        * */
        ExecutorService singleThreadExecutor = Executors.newSingleThreadExecutor();
        for (int i = 0; i < 5; i ++){
            singleThreadExecutor.execute(new ThreadHandle(String.valueOf(i)));
        }
    }

```

运行结果：

```
pool-1-thread-1Start Time2017-07-24 13:46:07
pool-1-thread-1End Time2017-07-24 13:46:11
pool-1-thread-1Start Time2017-07-24 13:46:11
pool-1-thread-1End Time2017-07-24 13:46:15
pool-1-thread-1Start Time2017-07-24 13:46:15
pool-1-thread-1End Time2017-07-24 13:46:19
pool-1-thread-1Start Time2017-07-24 13:46:19
pool-1-thread-1End Time2017-07-24 13:46:23
pool-1-thread-1Start Time2017-07-24 13:46:23
pool-1-thread-1End Time2017-07-24 13:46:27
```

上述结果中至始至终就只有一个线程thread-1在运行；

* 4、Executors.newScheduledThreadPool(5)；计划类线程池

1）、延时执行：

```
public static void main(String[] args) {
        /*计划类线程池*/
        ScheduledExecutorService scheduledExecutorService = Executors.newScheduledThreadPool(5);
        for (int i = 0; i < 5; i ++){
            /*延时10秒执行*/
            scheduledExecutorService.schedule(new ThreadHandle(String.valueOf(i)), 10, TimeUnit.SECONDS);
        }
        SimpleDateFormat df = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        Date date = new Date();
        String time = df.format(date);
        System.out.println(time);
    }

```

打印结果：

```
2017-07-24 13:54:10
pool-1-thread-2Start Time2017-07-24 13:54:20
pool-1-thread-3Start Time2017-07-24 13:54:20
pool-1-thread-1Start Time2017-07-24 13:54:20
pool-1-thread-4Start Time2017-07-24 13:54:20
pool-1-thread-5Start Time2017-07-24 13:54:20
pool-1-thread-3End Time2017-07-24 13:54:24
pool-1-thread-2End Time2017-07-24 13:54:24
pool-1-thread-4End Time2017-07-24 13:54:24
pool-1-thread-1End Time2017-07-24 13:54:24
pool-1-thread-5End Time2017-07-24 13:54:24
```

可以看到线程在十秒之后才开始执行；

2）、间断执行：

```
public static void main(String[] args) {
        /*计划类线程池*/
        ScheduledExecutorService scheduledExecutorService = Executors.newScheduledThreadPool(5);
        for (int i = 0; i < 5; i ++){
            /*从0ms开始每隔10秒执行一个任务，需要注意的是这个时间间隔是从上一个线程开始时计算的*/
            scheduledExecutorService.scheduleAtFixedRate(new ThreadHandle(String.valueOf(i)), 0, 10, TimeUnit.SECONDS);
        }
    }

```

打印结果：

```
pool-1-thread-1Start Time2017-07-24 13:59:17
pool-1-thread-5Start Time2017-07-24 13:59:17
pool-1-thread-2Start Time2017-07-24 13:59:17
pool-1-thread-4Start Time2017-07-24 13:59:17
pool-1-thread-3Start Time2017-07-24 13:59:17
pool-1-thread-1End Time2017-07-24 13:59:21
pool-1-thread-4End Time2017-07-24 13:59:21
pool-1-thread-5End Time2017-07-24 13:59:21
pool-1-thread-3End Time2017-07-24 13:59:21
pool-1-thread-2End Time2017-07-24 13:59:21
pool-1-thread-4Start Time2017-07-24 13:59:27
pool-1-thread-1Start Time2017-07-24 13:59:27
pool-1-thread-5Start Time2017-07-24 13:59:27
pool-1-thread-3Start Time2017-07-24 13:59:27
pool-1-thread-2Start Time2017-07-24 13:59:27
```

线程每次开始于上一次开始间隔都是10s，而且会无限的执行下去，类似于定时任务；

3）、间断执行:

```
public static void main(String[] args) {
        /*计划类线程池*/
        ScheduledExecutorService scheduledExecutorService = Executors.newScheduledThreadPool(5);
        for (int i = 0; i < 5; i ++){
            /*从0ms开始每隔10秒执行一个任务，需要注意的是这个时间间隔是从上一个线程结束后计算的*/
            scheduledExecutorService.scheduleWithFixedDelay(new ThreadHandle(String.valueOf(i)), 0, 10, TimeUnit.SECONDS);
        }
    }

```

打印结果：

```
pool-1-thread-5Start Time2017-07-24 14:02:49
pool-1-thread-3Start Time2017-07-24 14:02:49
pool-1-thread-2Start Time2017-07-24 14:02:49
pool-1-thread-4Start Time2017-07-24 14:02:49
pool-1-thread-1Start Time2017-07-24 14:02:49
pool-1-thread-3End Time2017-07-24 14:02:53
pool-1-thread-2End Time2017-07-24 14:02:53
pool-1-thread-5End Time2017-07-24 14:02:53
pool-1-thread-4End Time2017-07-24 14:02:53
pool-1-thread-1End Time2017-07-24 14:02:53
pool-1-thread-3Start Time2017-07-24 14:03:03
pool-1-thread-5Start Time2017-07-24 14:03:03
pool-1-thread-4Start Time2017-07-24 14:03:03
pool-1-thread-1Start Time2017-07-24 14:03:03
pool-1-thread-2Start Time2017-07-24 14:03:03
```

上面结果是每次线程和上一次线程执行结束后间隔10s；

#### 多线程回调：
基础类：

```
import java.util.concurrent.Callable;
 
/**
 * Created by zelei.fan on 2017/6/13.
 */
public class CallableTest implements Callable<String> {
 
    private int index;
 
    public CallableTest(int index){
        this.index = index;
    }
 
    @Override
    public String call() throws Exception {
        System.out.println("call()方法被自动调用, 开始*******" + Thread.currentThread().getName());
        if(index > 5){
            Thread.sleep(1000);
        }else {
            Thread.sleep(10000);
        }
        return "call()方法被自动调用，结束*******" + Thread.currentThread().getName();
    }
}

```

submit：将线程放入线程池中，除了使用execute，还可以使用submit,而且能够获取回调，submit适用于生产者-消费者模式，和Future一起使用起到没有返回结果就阻塞当前线程，等待线程池返回结果；

```
public static void main(String[] args) {
        ExecutorService pool1 = Executors.newCachedThreadPool();
        List<Future<String>> futureList = Lists.newArrayList();
        for (int i = 0; i < 5; i ++){
            Future<String> future = pool1.submit(new CallableTest(i));
            futureList.add(future);
        }
        futureList.forEach(new Consumer<Future<String>>() {
            @Override
            public void accept(Future<String> stringFuture) {
                try {
                    System.out.println(stringFuture.get());
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } catch (ExecutionException e) {
                    e.printStackTrace();
                }
            }
        });
    }

```

打印结果：

```
call()方法被自动调用, 开始*******pool-1-thread-1
call()方法被自动调用, 开始*******pool-1-thread-4
call()方法被自动调用, 开始*******pool-1-thread-5
call()方法被自动调用, 开始*******pool-1-thread-3
call()方法被自动调用, 开始*******pool-1-thread-2
call()方法被自动调用，结束*******pool-1-thread-1
call()方法被自动调用，结束*******pool-1-thread-2
call()方法被自动调用，结束*******pool-1-thread-3
call()方法被自动调用，结束*******pool-1-thread-4
call()方法被自动调用，结束*******pool-1-thread-5
```

调用结束打印的语句都是在run方法中返回出来的，通过future来接受返回参数，然后将future打印；

说到回调，还有一种就是CompletionService，区别是future是阻塞的，而CompletionService是异步非阻塞的；
看下具体例子：

```
public static void main(String[] args) {
        ExecutorService pool1 = Executors.newCachedThreadPool();
        CompletionService service = new ExecutorCompletionService(pool1);
        for (int i = 0; i < 10; i ++){
            service.submit(new CallableTest(i));
        }
        for(int i = 0; i < 10; i ++){
            try {
                SimpleDateFormat df = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
                Date date = new Date();
                String time = df.format(date);
                System.out.println(service.take().get() + time);
            } catch (InterruptedException e) {
                e.printStackTrace();
            } catch (ExecutionException e) {
                e.printStackTrace();
            }
        }
    }

```

打印结果：

```
call()方法被自动调用, 开始*******pool-1-thread-1
call()方法被自动调用, 开始*******pool-1-thread-5
call()方法被自动调用, 开始*******pool-1-thread-6
call()方法被自动调用, 开始*******pool-1-thread-2
call()方法被自动调用, 开始*******pool-1-thread-9
call()方法被自动调用, 开始*******pool-1-thread-10
call()方法被自动调用, 开始*******pool-1-thread-3
call()方法被自动调用, 开始*******pool-1-thread-7
call()方法被自动调用, 开始*******pool-1-thread-4
call()方法被自动调用, 开始*******pool-1-thread-8
call()方法被自动调用，结束*******pool-1-thread-72017-07-24 15:10:00
call()方法被自动调用，结束*******pool-1-thread-102017-07-24 15:10:01
call()方法被自动调用，结束*******pool-1-thread-92017-07-24 15:10:01
call()方法被自动调用，结束*******pool-1-thread-82017-07-24 15:10:01
call()方法被自动调用，结束*******pool-1-thread-62017-07-24 15:10:01
call()方法被自动调用，结束*******pool-1-thread-52017-07-24 15:10:10
call()方法被自动调用，结束*******pool-1-thread-22017-07-24 15:10:10
call()方法被自动调用，结束*******pool-1-thread-12017-07-24 15:10:10
call()方法被自动调用，结束*******pool-1-thread-32017-07-24 15:10:10
call()方法被自动调用，结束*******pool-1-thread-42017-07-24 15:10:10
```

通过上面一个例子可以知道Future是阻塞取出结果的，按顺序执行，如果说正常的前面的线程执行完成后面的线程还在执行中的话，前面线程的结果时可以直接返回的，但是如果后面的线程比前面的线程先执行完成，则后面线程的返回结果需要等待前面线程返回后才能取得结果； 而CompletionService是异步非阻塞的，哪个执行完成有回调了，哪个就能输出结果；

---

# 北京 快手 大数据研发技术面经
作者：LMagic
链接：https://www.nowcoder.com/discuss/148752?type=2&order=0&pos=92&page=1
来源：牛客网
## Java

```
1. HashMap的底层数据结构, 为什么JDK8要用红黑树. ConcurrentHashMap的底层数据结构, 如何保证线程安全
2. synchronized关键字的本质, 作用是什么. volatile关键字的作用, 哪些情况下会用它
3. Java线程的几大状态及转换. 线程可重入是什么概念, 可重入锁呢
4. 如果要设计一个线程池, 需要考虑哪些要素. Executors工厂类能创建哪些线程池, 用过哪些
5. 讲一讲熟悉的设计模式. 单例模式及工厂模式的实现方法. 装饰器模式是怎么一回事
6. 讲一讲熟悉的JVM GC算法, 常用的垃圾收集器. CMS有什么优缺点
7. 一个Java应用上线后, 关注哪些性能指标. 如果响应时间过长或者CPU占用过高, 如何排查, 用哪些工具或命令
```

## 大数据组件

```
1. 是否自己搭建的集群, 集群节点数及配置
2. Hadoop的XML配置文件有哪些, 改过哪些参数, 分别代表什么含义
3. HDFS NameNode高可用如何实现, 需要哪些角色. YARN有哪些组件, 如何分配资源
4. Spark RDD有哪些特点, 宽依赖和窄依赖. RDD的缓存级别
5. DAGScheduler及stage如何划分. 给一个比较复杂的RDD lineage, 手动划分stage和task
6. Spark Streaming以一定的时间窗口统计PV/UV, 如果窗口内数据量暴涨, 如何保证稳定性. 如果会延迟上报, 如何保证实时性
7. Kafka与Spark Streaming集成, 如何保证exactly once语义
8. Spark/Hive中大表join小表的优化方法. 数据倾斜和shuffle调优方法
9. 调整过Hive的哪些参数, 用什么执行引擎. Hive UDF怎么写, 写过哪些. HiveQL是怎样解析成MR/Spark job的
10. HBase的数据在HDFS上是怎样存储的, 写入数据的流程是怎样的. 为什么HBase适合写多读少业务
11. HBase的一个region由哪些东西组成. RegionServer宕机之后如何感知, 如何迁移数据
12. 为什么选用Kudu作为HBase和Hive的折中方案, 它有什么特点. 如果不用Kudu, HBase的二级索引能解决问题吗
13. Impala的查询及执行与Hive有什么不同 [PS. 我之前的项目里用了Kudu+Impala]
```

## 数据仓库设计

```
1. 之前业务中的数据仓库是如何分层的, 怎样建模, 主题如何划分
2. 从ODS到DW层的ETL, 做了哪些工作
3. 1~3NF的含义. 维度建模中星型模型和雪花模型的不同. 代理键是什么, 支架表是什么
4. 如何处理缓慢变化维. 怎样建设拉链表, 如何在拉链表中恢复最新数据
```

## 算法和应用题

```
1. 最长公共子序列(LCS)问题. 动态规划
2. 找出二叉树中任意两个节点的最低公共根节点, 如果树是BST呢. 深度优先搜索+二分查找树性质
3. 10亿条64B长的URL, 限定1G内存, 做计数, 如果要TopN的话呢. 哈希分桶+堆排序时间复杂度
4. 用户行为日志有UID和时间戳, 设定一个session间隔. 离线及在线地计算用户的平均session长度
5. 之前做过标签推荐系统, 详细讲一下架构和自己设计的算法. 算法流程是行为评分+指数衰减+线性归一化+余弦相似度/皮尔逊相关性+TF-IDF打压

```

# 头条
作者：Commando20180403011197

链接：https://www.nowcoder.com/discuss/142963?type=2&order=0&pos=5&page=1

来源：牛客网

* 面的公司并不多。拿到了头条和阿里的意向书，如果不出意外应该就是这俩选一个了。
没有实习，没有项目经历，什么都没有，上去就是硬怼。本科不是相关专业，研究生转方向但是是留学生，也不是特别厉害的学校。各方面都比较劣势。
优势就是特别能背。

## 一面

```
面岗位相关的基础，上来面试官直接发现我什么经历都没有，我直接说熟悉hadoop。挑了HDFS让我讲一下。
NN和DN。
HA的实现
zookeeper的原理，zk是如何保证一致性的，zk是如何判断session超时，connection超时的。如何触发回调。
client和HDFS文件的读写过程，延迟太高，怎么解决。我当时脑子一蒙，直接说了设计的就是高吞吐量的文件系统。
yarn的结构，RM和NM的交互，如何分配任务的。
yarn在什么层面调度，和k8s和mesos有什么区别，内存调度是什么怎么调度的，如果考虑CPU怎么调度的。如何实现隔离的，Control group 和Namespace是怎么回事。
手撕算法，链表排序。
人生中的第一次面试。。。。面的一团糟，多亏面试官使劲高抬贵手。。。
```

## 二面

```
面的计算机基础：
上来手撕，剑指原题，两个栈实现一个队列。
问了一下转专业的经历。
讲个简历的项目。
操作系统中的进程和线程的区别。
JVM的内存模型说一下，堆，栈，永久区，GC。
Java的多线程。
Hadoop的MR和Spark有什么区别，为什么Spark有优势。
TCP
用过什么数据库啊，然后就没往深了问了。
手推神经网络上的反向传播，把链式求导写出来，激活函数sigmoid。
介绍一下LSTM，和GRU的区别。
过。
```

## 三面

```
技术深度，问得特别特别细
看过源码对吧，hadoop的HDFS，Yarn，MapReduce源码讲讲，精确到方法和类。
客户端和NN的通信过程，和DN的通信过程。
HA中的选举过程，如何防止脑裂，为什么需要fencing，SSH连不上怎么办。
checkpoint的过程
yarn的状态机和epoll
yarn的公平调度器和容量调度器和FIFO
yarn抢占
MapReduce全过程，分片怎么读的，为什么用快排，换别的行不行，多路归并怎么实现的，环形缓冲区怎么实现的。
场景，很多牛逼的电脑，大CPU大内存，网卡超烂，如何优化？ 强制本地化，选高压缩的序列化格式，核心就是尽量减少网络IO。
场景，一个加载在内存里的HashMap，Key和Value全是int，从硬盘读进来只做查询不做修改，不考虑查询效率，尽可能提高空间效率，稍微考虑一下时间效率。从JVM调优到数据结构到GC到。。。。
手撕，实现一个线程池。
在spark和hadoop中如何处理数据倾斜。
spark的调度过程，DAGScheduler如何划分stage，TaskScheduler如何调度任务的。Spark的shuffle是什么样的，怎么优化的。
评价一下Hadoop和Spark的代码风格，我曹，我随便说了说，怕送命题。幸好我说完了他就自己说了，疯狂点头。
Java的多线程，讲讲锁。synchronized和reentrantlock的区别。讲讲阻塞队列，volatile
synchronized为啥是非公平的，这个我真不知道，回来一顿狠查，赶紧记住了。
Java的Obejct谈谈
Java的容器谈谈
Java的NIO用得咋样，不咋样。。。那就不聊了。
MPI聊聊
你Scala用得怎么样呀，Python怎么样啊
设计，设计一个RPC框架，我看你简历上做过，谈谈思路，观察者模式讲一下，并发容器。
设计，现在有一个RPC框架，需要使用线程池，多次复用socket，TCP，怎么传递命令。变相考hadoop，使用操作码。
结束。这一面的面试官超强，被压着打。

```

## 四面

```
Um.....和我这个岗没有一毛钱关系。
手写一个leetcode hard，就是两个数组，找全局中间数那个。
问问搜索。
如何构建倒排索引
BM25
如何加速查询，WAND算法细节。
倒排索引的log时间合并
如何评价一次query，设计一个机器学习模型，如何设计这样的模型，如何提取feature，用什么模型
如何做查询补全 Trie
设计一个查询缓存
如何对倒排索引进行空间压缩，我先说了OptPForDelta
如何选择最优分裂点，抽样，然后算。
手撕个代码实现一下
如果不抽样，你这样是全局最优吗？我说是啊，他说不是。。。。对每一个算一个。好吧，他说得对。
还有别的优化方式吗 Variable Byte
聊家常。。。。出了门感觉人生都灰暗了，跪

```

# 美团
作者：Commando20180403011197
链接：https://www.nowcoder.com/discuss/142963?type=2&order=0&pos=5&page=1
来源：牛客网

*数据开发，就是数据仓库开发，好多重复的我不写了。已经拒了
## 一面

```
基础：
讲讲项目
java基础
HTTP和TCP
写俩算法，可以用IDE。都是超简单的，有一个台阶，还有一个m的n次幂，自己写个测试试一下
写个sql
mysql的索引，如何实现的，何时失效，聚簇索引和非聚簇索引，B+树
写个单例，懒汉饿汉。
处理数据倾斜
Spring系列会吗？不会
```

## 二面

```
hadoop和spark简单讲讲，只说结构原理不说源码
spark的调优
JMM，全程不打断，我一口气说到了底。。。
数据仓库的星型模型和雪花模型，上卷下钻
Hive
还有啥忘了
spark sql，窝不会
```

## 三面

```
讲项目
HTTP，TCP
操作系统的进程与线程
Java多线程，线程池
爬虫讲讲原理（我项目里用了）
场景：实现一下chrome里那个历史记录这个功能，用啥数据结构怎么实现
python，MPI，数据仓库，你都会点什么都说说
问了项目里的数据清洗，补全和NLP，然而我的NLP一点深度学习没用，感觉对面可能有点失望。
问了推荐系统
问了flask，Restful API
tensorflow怎么实现的知道么，说了个大概，caffe会用么。不会
```

# 阿里
* 阿里在我投简历两个月之后捞我，而且面试简单得出奇，只考广度不考深度。。。。我还是犯了好多错误，提醒大家，如果面试这种面试官不深问的，一定要自己使劲说，不要说两句就停了，他觉得你只会这么多。

## 一面

```
这个面试官是个做算法的
说个项目
Java基础，说说容器
多线程，线程池
java的序列化方式，hadoop的序列化方式，Avro，parquet，transient关键字
spark的原理，我就说了个架子等他问，他不问了！
设计模式，观察者，hadoop用了啥，我说用了组合，等他问我第一第二关系的事，他不问了！
业务题，拿spark实现个业务逻辑，拿嘴说就行。map然后reducebykey然后。。。
一个白板代码，是他工作业务逻辑的抽象。
还问啥我给忘了
```

## 二面三面开始集中面试

```
连着面了我2小时，我一起写了。
说个项目，问我项目实现细节。工程细节，你这怎么加速，Geohash怎么用的。并对我的辣鸡项目表示了鄙视。
spark streaming和storm，flink的区别
各种分布式计算框架的区别
storm如何处理反压，如何保证流的可靠性的
flink会吗，不会
hbase的row key设计，我现在就要范围查询value怎么设计。
yarn里面机器崩了，怎么让任务接着算。。。我说了重启nodemanager重算这个分片，如果这个分片也不想重算呢，接着算，没这功能没说出来。回来想想其实还是应该能说个思路的。
说了AppMaster的故障怎么实现的HA
zookeeper是如何选举新的Active Namenode，没仔细说，说了个原理他又不继续问了，后悔。
大数算法：10亿个int查重，讲思路，布隆过滤，mapreduce，bitmap，算法的复杂度说说
机器学习竞赛跟我说说，讲了特征工程，提了GBDT，然而我觉得他并不知道GBDT是啥，讲完和我说你这就是java的hello world啊。主要也是自己讲的不好，我也很是哽咽

```

## HR面

```
阿里这个HR面是真的犀利，我也没经验，第一次面这种话里带枪的HR面。
中间委婉谈及了我的学历，我的水课，我的没实习没经历。。。被贬得一无是处，我也不敢顶她，只能避重就轻解释一下。现在回想可能表现得太没自信了更减分。
拿到了意向书。。。。没有谈薪资，没有加面，感觉要拿劝退价了。
```

---

# 2018大数据面试题总结

[2018大数据面试题总结](https://zhuanlan.zhihu.com/p/48624942)

* 1、RDD中reduceBykey与groupByKey哪个性能好，为什么

reduceByKey：

>reduceByKey会在结果发送至reducer之前会对每个mapper在本地进行merge，有点类似于在MapReduce中的combiner。这样做的好处在于，在map端进行一次reduce之后，数据量会大幅度减小，从而减小传输，保证reduce端能够更快的进行结果计算。

groupByKey：

>groupByKey会对每一个RDD中的value值进行聚合形成一个序列(Iterator)，此操作发生在reduce端，所以势必会将所有的数据通过网络进行传输，造成不必要的浪费。同时如果数据量十分大，可能还会造成OutOfMemoryError。

通过以上对比可以发现在进行大量数据的reduce操作时候建议使用reduceByKey。不仅可以提高速度，还是可以防止使用groupByKey造成的内存溢出问题。

* 2、讲述一下hdfs上传文件的流程。

答：这里描述的 是一个256M的文件上传过程

```
① 由客户端 向 NameNode节点节点 发出请求；

②NameNode 向Client返回可以可以存数据的 DataNode 这里遵循机架感应原则；

③客户端 首先 根据返回的信息 先将 文件分块（Hadoop2.X版本 每一个block为 128M 而之前的版本为 64M；

④然后通过NameNode返回的DataNode信息 直接发送给DataNode 并且是 流式写入同时会复制到其他两台机器；

⑤DataNode 向 Client通信 表示已经传完 数据块 同时向NameNode报告

⑥依照上面（④到⑤）的原理将 所有的数据块都上传结束 向 NameNode 报告 表明 已经传完所有的数据块 。
```

* 3、了解zookeeper吗？介绍一下它，它的选举机制和集群的搭建。

答：那当然是熟悉啦，ZooKeeper 是一个开源的分布式协调服务，是 Google Chubby 的开源实现。

> 分布式应用程序可以基于 ZooKeeper 实现诸如数据发布/订阅、负载均衡、命名服务、分布式协调/通知、集群管理、Master 选举、分布式锁和分布式队列等功能。

我们公司使用的flume集群，Kafka集群等等，都离不开ZooKeeper呀。每个节点上我们都要搭建ZooKeeper服务。

>首先我们要在每台pc上配置zookeeper环境变量，在cd到zookeeper下的conf文件夹下在zoo_simjle.cfg文件中添加datadir路径，再到zookeeper下新建data文件夹，创建myid，在文件里添加上server的ip地址。在启动zkserver.sh start便ok了。

* 4、spark streming在实时处理时会发生什么故障，如何停止，解决

答：和Kafka整合时消息无序：

修改Kafka的ack参数，当ack=1时，master确认收到消息就算投递成功。ack=0时，不需要收到消息便算成功，高效不准确。sck=all，master和server都要受到消息才算成功，准确不高效。

StreamingContext.stop会把关联的SparkContext对象也停止，如果不想把SparkContext对象也停止的话可以把StremingContext.stop的可选参数stopSparkContext设为flase。一个SparkContext对象可以和多个streamingcontext对象关联。只要对前一个stremingcontext.stop(stopsparkcontext=false),然后再创建新的stremingcontext对象就可以了。

* 5、说一下你对yarn的理解：

答：YARN是Hadoop2.0版本引进的资源管理系统，直接从MR1演化而来。

核心思想：

>将MR1中的JobTracker的资源管理和作业调度两个功能分开，分别由ResourceManager和ApplicationMaster进程实现。

ResourceManager：

>负责整个集群的资源管理和调度 ；	
>ApplicationMaster：负责应用程序相关事务，比如任务调度、任务监控和容错等。

YARN的出现，使得多个计算框架可以运行在同一个集群之中。 

```
1. 每一个应用程序对应一个ApplicationMaster。 
2. 目前可以支持多种计算框架运行在YARN上面，比如MapReduce、storm、Spark、Flink。
```

* 6、有一个1G大小的一个文件，里面每一行是一个词，词的大小不超过16字节，内存限制大小是1M，要求返回频数最高的100个词。

答：	
>Step1：顺序读文件中，对于每个词x，取hash(x)%5000，然后按照该值存到5000个小文件（记为f0 ,f1 ,... ,f4999）中，这样每个文件大概是200k左右，如果其中的有的文件超过了1M大小，还可以按照类似的方法继续往下分，直到分解得到的小文件的大小都不超过1M；

>Step2：对每个小文件，统计每个文件中出现的词以及相应的频率（可以采用trie树/hash_map等），并取出出现频率最大的100个词（可以用含100个结点的最小堆），并把100词及相应的频率存入文件，这样又得到了5000个文件；

>Step3：把这5000个文件进行归并（类似与归并排序）；

* 7、如何配置spark master的HA？

答：
>1)配置zookeeper

>2)修改spark_env.sh文件,spark的master参数不在指定，添加如下代码到各个master节点

```
ExportSPARK_DAEMON_JAVA_OPTS=-Dspark.deploy.recoveryMode=ZOOKEEPER-

Dspark.deploy.zookeeper.url=zk01:2181,zk02:2181,zk03:2181-Dspark.deploy.zookeeper.dir=/spark”
```

>3) 将spark_env.sh分发到各个节点

>4)找到一个master节点，执行./start-all.sh，会在这里启动主master,其他的master备节点，启动master命令: ./sbin/start-master.sh

>5)提交程序的时候指定master的时候要指定三台master，例如

```
./spark-shell –master spark://master01:7077,master02:7077,master03:7077
```

* 8、一个datanode 宕机,怎么一个流程恢复


答：Datanode宕机了后，如果是短暂的宕机，可以实现写好脚本监控，将它启动起来。如果是长时间宕机了，那么datanode上的数据应该已经被备份到其他机器了，那这台datanode就是一台新的datanode了，删除他的所有数据文件和状态文件，重新启动。

---

# Spark面试题(一)

## 1 Kafka 分布式的情况下，如何保证消息的顺序?
Kafka 分布式的单位是 Partition。如何保证消息有序，需要分几个情况讨论。

* 同一个 Partition 用一个 write ahead log 组织，所以可以保证 FIFO 的顺序。

* 不同 Partition 之间不能保证顺序。但是绝大多数用户都可以通过 message key 来定义，因为同一个 key 的 message 可以保证只发送到同一个 Partition。比如说 key 是 user id，table row id 等等，所以同一个 user 或者同一个 record 的消息永远只会发送到同一个 Partition上，保证了同一个 user 或 record 的顺序。

* 当然，如果你有 key skewness 就有些麻烦，需要特殊处理。

实际情况中: 

```
（1）不关注顺序的业务大量存在；
（2）队列无序不代表消息无序。
```

第（2）条的意思是说: 我们不保证队列的全局有序，但可以保证消息的局部有序。

举个例子: 保证来自同1个 order id 的消息，是有序的！

Kafka 中发送1条消息的时候，可以指定(topic, partition, key) 3个参数。partiton 和 key 是可选的。如果你指定了 partition，那就是所有消息发往同1个 partition，就是有序的。并且在消费端，Kafka 保证，1个 partition 只能被1个 consumer 消费。或者你指定 key（比如 order id），具有同1个 key 的所有消息，会发往同1个 partition。也是有序的。

## 2 对于 Spark 中的数据倾斜问题你有什么好的方案？

简单一句: 

>Spark 数据倾斜的几种场景以及对应的解决方案，包括避免数据源倾斜，调整并行度，使用自定义 Partitioner，使用 Map 侧 Join 代替 Reduce 侧 Join（内存表合并），给倾斜 Key 加上随机前缀等。

* 什么是数据倾斜 	

对 Spark/Hadoop 这样的大数据系统来讲，数据量大并不可怕，可怕的是数据倾斜。数据倾斜指的是，并行处理的数据集中，某一部分（如 Spark 或 Kafka 的一个 Partition）的数据显著多于其它部分，从而使得该部分的处理速度成为整个数据集处理的瓶颈（木桶效应）。

* 数据倾斜是如何造成的 

>在 Spark 中，同一个 Stage 的不同 Partition 可以并行处理，而具有依赖关系的不同 Stage 之间是串行处理的。假设某个 Spark Job 分为 Stage 0和 Stage 1两个 Stage，且 Stage 1依赖于 Stage 0，那 Stage 0完全处理结束之前不会处理Stage 1。而 Stage 0可能包含 N 个 Task，这 N 个 Task 可以并行进行。如果其中 N-1个 Task 都在10秒内完成，而另外一个 Task 却耗时1分钟，那该 Stage 的总时间至少为1分钟。换句话说，一个 Stage 所耗费的时间，主要由最慢的那个 Task 决定。由于同一个 Stage 内的所有 Task 执行相同的计算，在排除不同计算节点计算能力差异的前提下，不同 Task 之间耗时的差异主要由该 Task 所处理的数据量决定。

具体解决方案 

* 1. 调整并行度分散同一个 Task 的不同 Key: Spark 在做 Shuffle 时，默认使用 HashPartitioner（非 Hash Shuffle ???）对数据进行分区。如果并行度设置的不合适，可能造成大量不相同的 Key 对应的数据被分配到了同一个 Task 上，造成该 Task 所处理的数据远大于其它 Task，从而造成数据倾斜。如果调整 Shuffle 时的并行度，使得原本被分配到同一 Task 的不同 Key 发配到不同 Task 上处理，则可降低原 Task 所需处理的数据量，从而缓解数据倾斜问题造成的短板效应。图中左边绿色框表示 kv 样式的数据，key 可以理解成 name。可以看到 Task0 分配了许多的 key，调整并行度，多了几个 Task，那么每个 Task 处理的数据量就分散了。

![](https://pic2.zhimg.com/80/v2-c835c4e277645c663e04b355b124ecb5_hd.jpg)

* 2. 自定义Partitioner: 使用自定义的 Partitioner（默认为 HashPartitioner），将原本被分配到同一个 Task 的不同 Key 分配到不同 Task，可以拿上图继续想象一下，通过自定义 Partitioner 可以把原本分到 Task0 的 Key 分到 Task1，那么 Task0 的要处理的数据量就少了。

 * 3. 将 Reduce side（侧） Join 转变为 Map side（侧） Join: 通过 Spark 的 Broadcast 机制，将 Reduce 侧 Join 转化为 Map 侧 Join，避免 Shuffle 从而完全消除 Shuffle 带来的数据倾斜。可以看到 RDD2 被加载到内存中了。

![](https://pic2.zhimg.com/80/v2-673a656c08704b373fe44d247a22a5b5_hd.jpg)

* 4. 为 skew 的 key 增加随机前/后缀: 为数据量特别大的 Key 增加随机前/后缀，使得原来 Key 相同的数据变为 Key 不相同的数据，从而使倾斜的数据集分散到不同的 Task 中，彻底解决数据倾斜问题。Join 另一则的数据中，与倾斜 Key 对应的部分数据，与随机前缀集作笛卡尔乘积，从而保证无论数据倾斜侧倾斜 Key 如何加前缀，都能与之正常 Join。

* 5. 大表随机添加 N 种随机前缀，小表扩大 N 倍: 如果出现数据倾斜的 Key 比较多，上一种方法将这些大量的倾斜 Key 分拆出来，意义不大（很难一个 Key 一个 Key 都加上后缀）。此时更适合直接对存在数据倾斜的数据集全部加上随机前缀，然后对另外一个不存在严重数据倾斜的数据集整体与随机前缀集作笛卡尔乘积（即将数据量扩大 N 倍），可以看到 RDD2 扩大了 N 倍了，再和加完前缀的大数据做笛卡尔积。

![](https://pic3.zhimg.com/80/v2-95bd9d233cb7431864f47ce6a8f3149e_hd.jpg)

## 3 你所理解的 Spark 的 shuffle 过程？
Spark shuffle 处于一个宽依赖，可以实现类似混洗的功能，将相同的 Key 分发至同一个 Reducer上进行处理。

## 4 Spark有哪些聚合类的算子,我们应该尽量避免什么类型的算子？
在我们的开发过程中，能避免则尽可能避免使用 reduceByKey、join、distinct、repartition 等会进行 shuffle 的算子，尽量使用 map 类的非 shuffle 算子。这样的话，没有 shuffle 操作或者仅有较少 shuffle 操作的 Spark 作业，可以大大减少性能开销。

## 5 spark on yarn 作业执行流程，yarn-client 和 yarn cluster 有什么区别

Spark On Yarn 的优势 
>1. Spark 支持资源动态共享，运行于 Yarn 的框架都共享一个集中配置好的资源池 
2. 可以很方便的利用 Yarn 的资源调度特性来做分类·，隔离以及优先级控制负载，拥有更灵活的调度策略 
3. Yarn 可以自由地选择 executor 数量
4. Yarn 是唯一支持 Spark 安全的集群管理器（Mesos???），使用 Yarn，Spark 可以运行于 Kerberized Hadoop 之上，在它们进程之间进行安全认证

yarn-client 和 yarn cluster 的异同 

>1. 从广义上讲，yarn-cluster 适用于生产环境。而 yarn-client 适用于交互和调试，也就是希望快速地看到 application 的输出。 
2. 从深层次的含义讲，yarn-cluster 和 yarn-client 模式的区别其实就是 Application Master 进程的区别，yarn-cluster 模式下，driver 运行在 AM(Application Master)中，它负责向 YARN 申请资源，并监督作业的运行状况。当用户提交了作业之后，就可以关掉 Client，作业会继续在 YARN 上运行。然而 yarn-cluster 模式不适合运行交互类型的作业。而 yarn-client 模式下，Application Master 仅仅向 YARN 请求 executor，Client 会和请求的 container 通信来调度他们工作，也就是说 Client 不能离开。

![](https://pic1.zhimg.com/80/v2-a1530dc9ac0066a2926b99e4b2d7ae28_hd.jpg)

## 6 Spark为什么快，Spark SQL 一定比 Hive 快吗
Spark SQL 比 Hadoop Hive 快，是有一定条件的，而且不是 Spark SQL 的引擎比 Hive 的引擎快，相反，Hive 的 HQL 引擎还比 Spark SQL 的引擎更快。其实，关键还是在于 Spark 本身快。

* 消除了冗余的 HDFS 读写: Hadoop 每次 shuffle 操作后，必须写到磁盘，而 Spark 在 shuffle 后不一定落盘，可以 cache 到内存中，以便迭代时使用。如果操作复杂，很多的 shufle 操作，那么 Hadoop 的读写 IO 时间会大大增加，也是 Hive 更慢的主要原因了。
* 消除了冗余的 MapReduce 阶段: Hadoop 的 shuffle 操作一定连着完整的 MapReduce 操作，冗余繁琐。而 Spark 基于 RDD 提供了丰富的算子操作，且 reduce 操作产生 shuffle 数据，可以缓存在内存中。
* JVM 的优化: Hadoop 每次 MapReduce 操作，启动一个 Task 便会启动一次 JVM，基于进程的操作。而 Spark 每次 MapReduce 操作是基于线程的，只在启动 Executor 是启动一次 JVM，内存的 Task 操作是在线程复用的。每次启动 JVM 的时间可能就需要几秒甚至十几秒，那么当 Task 多了，这个时间 Hadoop 不知道比 Spark 慢了多少。

记住一种反例 考虑一种极端查询:

>Select month_id, sum(sales) from T group by month_id;

这个查询只有一次 shuffle 操作，此时，也许 Hive HQL 的运行时间也许比 Spark 还快，反正 shuffle 完了都会落一次盘，或者都不落盘。

结论 Spark 快不是绝对的，但是绝大多数，Spark 都比 Hadoop 计算要快。这主要得益于其对 mapreduce 操作的优化以及对 JVM 使用的优化。

## 7 容错方法
## 8 RDD, DAG, Stage怎么理解？

DAG Spark 中使用 DAG 对 RDD 的关系进行建模，描述了 RDD 的依赖关系，这种关系也被称之为 lineage（血缘），RDD 的依赖关系使用 Dependency 维护。DAG 在 Spark 中的对应的实现为 DAGScheduler。

RDD RDD 是 Spark 的灵魂，也称为弹性分布式数据集。一个 RDD 代表一个可以被分区的只读数据集。RDD 内部可以有许多分区(partitions)，每个分区又拥有大量的记录(records)。Rdd的五个特征： 1. dependencies: 建立 RDD 的依赖关系，主要 RDD 之间是宽窄依赖的关系，具有窄依赖关系的 RDD 可以在同一个 stage 中进行计算。 2. partition: 一个 RDD 会有若干个分区，分区的大小决定了对这个 RDD 计算的粒度，每个 RDD 的分区的计算都在一个单独的任务中进行。 3. preferedlocations: 按照“移动数据不如移动计算”原则，在 Spark 进行任务调度的时候，优先将任务分配到数据块存储的位置。 4. compute: Spark 中的计算都是以分区为基本单位的，compute 函数只是对迭代器进行复合，并不保存单次计算的结果。 5. partitioner: 只存在于（K,V）类型的 RDD 中，非（K,V）类型的 partitioner 的值就是 None。

RDD 的算子主要分成2类，action 和 transformation。这里的算子概念，可以理解成就是对数据集的变换。action 会触发真正的作业提交，而 transformation 算子是不会立即触发作业提交的。每一个 transformation 方法返回一个新的 RDD。只是某些 transformation 比较复杂，会包含多个子 transformation，因而会生成多个 RDD。这就是实际 RDD 个数比我们想象的多一些 的原因。通常是，当遇到 action 算子时会触发一个job的提交，然后反推回去看前面的 transformation 算子，进而形成一张有向无环图。

Stage 在 DAG 中又进行 stage 的划分，划分的依据是依赖是否是 shuffle 的，每个 stage 又可以划分成若干 task。接下来的事情就是 driver 发送 task 到 executor，executor 自己的线程池去执行这些 task，完成之后将结果返回给 driver。action 算子是划分不同 job 的依据。


---

# spark streaming ,预写日志（write-ahead logging）和checkpoint

[spark streaming ,预写日志（write-ahead logging）和checkpoint](https://blog.csdn.net/j904538808/article/details/80112805)

## （1）什么是Spark-Streaming？
spark steaming 是spark Core API的一种扩展，它可用于大规模、高吞吐量、容错的实时数据流处理。它支持从多种数据源中读取数据，如 kafka,flume,twitter,zeromq,kinesis 或者是tcp socket。并且能够使用类似高阶函数的复杂算法来进行数据处理，如 map(),reduce(),join(),window(）等。处理后的数据可以保存到文件系统、数据库等。

## （2）spark streaming的基本运行原理？
接收实时输入数据流，将数据流按照时间间隔拆分成多个batch,比如每收集5s的数据封装成一个batch,然后将每个batch交给spark的计算引擎进行处理，产生由一个一个的batch组成的结果数据流，输出。

## （3）spark streaming的高级抽象？
spark streaming提供的高级抽象叫做Dstream，即 Discretized Stream(离散流) 
代表了一个持续不断的数据流，Dstream可以利用数据源来创建，如kafka,flume,twitter,zeromq,kinesis，也可以通过其他的Dstream通过高阶函数来创建，如map(),reduce(),join(),window(）等，自我的理解是类似于RDD的创建，可以根据数据本身来创建，也可以根据RDD通过map(),reduce(),join()等来创建，Dstream类似于一个装满RDD元素的RDD列表的感觉。Dstream的内部其实是一系列持续不断产生的RDD，RDD是不可变的分布式的数据集，Dstream 中的每个RDD都包含了一个时间段内的数据。

## （4）spark streaming checkpoint的概述？
每一个spark streaming应用程序，都需要持续不断的进行运转计算，不可停歇，因此就必须有对与应用逻辑无关的失败的容错能力，spark streaming就要将错的信息checkpoint在容错的存储系统上，是应用程序运行时，能够从错败中恢复。

## （5）如何对Dstream checkpoint?
首先，设置还原点目录； 
其次，调用Dstream的checkpoint方法； 
Dstream的checkpoint周期一定要是产生batch的整数倍，官方建议设置至少10s,通常来说设置为窗口滑动间隔的5~10倍比较合适。

## （6）spark streaming过程中，什么数据要被checkpoint？

* （1）元数据信息。 

包括： 

```
（1.1）配置信息—创建Spark-Streaming应用程序的配置信息，比如SparkConf 
（1.2）DStream的操作信息—-定义了Spark-Stream应用程序的计算逻辑的DStream操作信息 
（1.3）未处理的batch信息—-哪些job正在排队，还没处理的batch信息。 
```

* （2）实时计算中产生的RDD数据checkpoint。

对于一些将多个batch的数据进行聚合的，有状态的transformation操作，这是非常有用的， 
在这种tranformation操作中，生成的RDD是依赖与之前的batch的，这会导致随着时间的推移，Rdd的依赖 
链条越来越长，要避免由于依赖链条越来越长，导致一起变得越来越长的失败恢复时间，有状态的transformation 
操作执行过程中间产生的RDD，会定期的被checkpoint到可靠的存储系统上,比如HDFS,从而削减RDD的依赖链条，进而缩短失败恢复时RDD的恢复时间。

## （8）预写日志是什么？其工作机制是什么？如何配置预写日志机制？

预写日志，简称WAL,从spark1.2版本开始，引入基于容错机制的文件系统的WAL机制，若启用该机制，receiver接收到的所有数据都会被写入配置的checkpoint目录中的预写日志这种机制可以让driver在恢复的时候，避免数据丢失，并且可以确保整个实时计算过程中，零数据丢失。 
要配置该机制： 

```
首先，调用StreamingContext的checkpoint()方法设置一个checkpoint目录； 
然后，将spark.streaming.receiver.writeAheadLog.enable参数设置为true。
```

WAL机制的缺点： 

```
会导致Receiver的吞吐量大幅度下降，因为单位时间内有相当一部分时间需要将数据写入预写日志； 
```

解决办法： 

>如果又希望开启预写日志机制，确保数据零损失，又不希望影响系统的吞吐量，那么可以创建多个输入DStream启动多个Reciver，然后将这些receiver接收到的数据使用ssc.union()方法将这些dstream中的数据进行合并 。此外在启用了预写日志机制之后，推荐将复制持久化机制禁用掉，因为所有数据已经保存在容错的文件系统中了，不需要再用复制机制进行持久化，保存一份副本了，只要将输入的DStream的持久化机制设置一下即可

---



























