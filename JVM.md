# 	 		JVM

对于一个算刚步入java编程的开发人员来说,对于JDK理解并不熟悉，其实JDK包括java 程序设计语言，java api 和java虚拟机 (摘自oracle 官网)

![1550762437192](.\img\1550762437192.png)

#### java内存区域与内存溢出异常

 	之前跟做C的老哥聊会了天，听他们说，他们对程序的内存的管理很严，用到的内存都需要手动去释放。我听到这个我就惊了，需要手动释放，那不是很麻烦，我们这些做Java怎么没有这说（难怪java是世界上最好的语言，再也不是排黄片。。。开句玩笑话）。为什么java程序不需要手动去释放程序，是因为jvm帮我干了。不说了直接上jvm的运行时数据区域图

![](.\img\1551020865.jpg)

**程序计数器：**

​	程序计数器，官方的解释是 *当前线程所执行的字节码的行号指示器* ，简单来讲，你的java程序之所以能一行一行的执行下去，就是通过这个东东来实现的。注意，程序计数器不是线程共有的 ，也就是说每个线程都有自己的线程计算器，互不影响。

**java虚拟机栈**

​	java虚拟机栈也是线程私有，他的生命周期和线程相同，主要描述的是方法的内存模型：主要的功能就是存储局部变量， 操作数栈，动态链接，方法出口等，每个方法从调用到完成对应的是虚拟机栈入栈到出栈的过程。

注意一点，long和double 需要两个变量空间 ，其他类型只需要一个，局域变量表在 编译期间就已经确定内存空间，不会改变