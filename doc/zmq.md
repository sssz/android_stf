<h2>Zeromq库（初步）
</h2>



2019年9月18日 - xjf

12:42

**1. Zeromq库功能：**

 

Zeromq是一个网络套接字(socket)的优化库，简化了unix系统上网络编程的一些问题。

在这个项目中，除了用于前后端的socket传输，更多是作为消息队列进行进程间的通信。

 

Zeromq提供了很多通信的方式，包括pub-sub模式（项目中较多用这个）、push-pull模式等。



下面这张图是官方文档上对于pub-sub模式的一个简单例子

![img](file:///C:/Users/Bbbts/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image001.png)

 **2. STF项目中对于ZeroMQ的处理与应用：**

 

通过对**/lib/units**中文件的阅读，发现大部分的zmq应用都没有直接require ZMQ这个库，而是引用了**/lib/util/zmqutil.js**

在这个文件中，作者实际将zmq库提供的js对象进行了封装，并进行该封装的原因在文件的注释中提供了：

```js
// ISSUE-100 (https://github.com/openstf/stf/issues/100)

 

// In some networks TCP Connection dies if kept idle for long.

// Setting TCP_KEEPALIVE option true, to all the zmq sockets

// won't let it die
```

 

**3. 一些比较好的解释zmq与stf中zmq应用的博文：**

1. 1. https://www.cnblogs.com/neooelric/p/8978720.html
   2. https://www.cnblogs.com/neooelric/p/9020872.html
   3. http://zguide.zeromq.org/page:all（英文版官方教程，上面两篇是这个教程的部分翻译）
   4. https://zeromq.org/languages/nodejs/（官网）
   5. https://testerhome.com/topics/8519（STF项目讲解）