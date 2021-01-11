# JDK安装和环境配置(图文教程)

## 前言

>欢迎关注博主微信公众号 [CodeGuide](http://qlvju1a7q.hn-bkt.clouddn.com/jdk/codeguide.jpg) ，号内回复`资料`获取`学习资料`和`项目练习`大礼包。扫文末`二维码`赢好礼。
>
>梦想成为自由职业的社会打工人。努力改变想的多做的少的现状。

## Java为什么需要安装Jdk

- 这就好比你设计PPT需要安装Office一样，有了这工具你才可以干活。

- JDK是java软件开发包(Java Development Kit)的简称，要想开发java程序就必须安装JDK。没有JDK的话，无法编译运行Java程序。
  		因为JDK包含的基本组件包括以下文件：(安装完成后环境验证会用到)

  >​	javac.exe，用于编译java文件，将java文件编译成class文件。
  >
  >​	java.exe，用于运行class文件，将class文件运行出结果。

## Jdk和Jre的区别

- **JRE**：Java Runtime Environment（Java运行时环境）。面向Java程序的使用者，而不是开发者。（有时候你配置的tomcat本地启动报错可能会需要你去配置Jre的路径。）

  ① 运行Java程序程序所必须的环境集合。

  ② 包含了Java虚拟机（JVM）。	

  ③ Java基础类库。

- **JDK**：Java Development Kit（java开发工具包）。他提供了Java的开发环境（javac等工具）。开发者所写的Java程序计算机是看不懂的，但是经过Jdk的`javac`编译之后形成的class文件由JVM解释后形成机器语言给计算机。

- **总结：**JDK包含了JRE，同时还包括java源码的编译器javac、监控工具jconsole、分析工具jvisualvm等。

  

## Jdk在Win系统的安装

- ### 第一步：获取资源官网地址。

  > [JDK官网下载](https://www.oracle.com/java/technologies/javase-downloads.html)

  > 公众号回复     **JDK**

  >百度云链接
  >
  >链接：https://pan.baidu.com/s/1QshcH6TaMVQ8j0PxWWheTQ 
  >提取码：pc40 

- 下载完成后目录结构。（电脑是32位选择上面，64位选择上面）。

  ![jdk目录](../../%E5%9B%BE%E7%89%87/001/20201225_jdk01.png)
  
- 双击运行该程序安装JDK。这里可以修改安装路径，一定保存在英文目录下面，最好没有空格（建议保持默认）一直下一步就可以完成安装。

  ![JDK安装01](../../%E5%9B%BE%E7%89%87/001/02.png)

- 安装完成之后在C:\Program Files\Java。

  ![jdk安装路径](../../%E5%9B%BE%E7%89%87/001/03.png)

- ### 第二步：环境变量配置。**JAVA_HOME**、**Path**、**CLASSPATH**

  - 环境变量说白了就是一个变量，你可以简单的理解为计算机中的“全局变量”。

  - 我们运行java命令的时候win电脑是不知道这个是什么东西的，我们要通过配置这个解释器去告诉计算机他是什么，并解释执行。

  - 右键(此电脑)-->属性-->左侧(高级系统设置)-->环境变量配置

    ![jdk环境变量配置](../../%E5%9B%BE%E7%89%87/001/04.png)

  - 配置**JAVA_HOME**   ，java的安装路径以我的为例。

    `C:\Program Files\Java\jdk1.8.0_231`

    它指向Jdk的安装目录，电脑不知道你安装在哪里，唯一的办法就是规定一个JAVA_HOME 环境变量，需要用JDK的程序只要引用JAVA_HOME就可以搞定~，比如IDEA/Tomcat等软件就是通过搜索JAVA_HOME变量来找到并使用JDK的。

    ![JAVA_HOME](../../%E5%9B%BE%E7%89%87/001/05.png)

  - 配置PATH注意分号。（如果不生效建议移动到顶层）

    `%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin`

    你在写完一个Java程序之后是不是要javac一下来编译，然后再java一下来执行？问题就在这里，shell（命令解释器）在执行你输入的命令时，会到PATH变量所指定的路径中查找看是否能找到相应的命令程序，而javac和java这个命令本机一开始是没有的，他们存在于你安装的JDK的bin目录下（bin目录中包含经常要用到的可执行文件如javac/java/javadoc等），因此我们需要把 bin目录增加到现有的PATH变量中。

    ![PATH配置](../../%E5%9B%BE%E7%89%87/001/06.png)

  - 配置CLASSPATH。(注意最前面 .  不要忘记 ) 这里也可以直接使用 . 代替下面，整个路径。

    `.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar`

    作用是指定类搜索路径，要使用已经编写好的类，前提当然是能够找到它们了，JVM就是通过CLASSPTH来寻找类的。我们 需要把jdk安装目录下的lib子目录中的dt.jar和tools.jar设置到CLASSPATH中，当然，当前目录“.”也必须加入到该变量中。

    ![CLASSPATH路径](../../%E5%9B%BE%E7%89%87/001/07.png)

  - 第三步：测试安装成功。

    三个命令都可以：java -version(显示版本信息)   java 和javac显示一大长串不认识的东西就对了。

    ![java -version](../../%E5%9B%BE%E7%89%87/001/08.png)

## 资料部分截图

全部资料免费送给大家。（扫文末二维码关注回复  `资料`）如有失效请联系WX：Code_Guide

![资料1](../../%E5%9B%BE%E7%89%87/001/09.png)

![资料2](../../%E5%9B%BE%E7%89%87/001/010.png)

## 公众号

![公众号](../../%E5%9B%BE%E7%89%87/001/011.jpg)

