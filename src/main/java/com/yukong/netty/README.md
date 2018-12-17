用于记录我的学习过程

# netty
> 时间 2018年8月22日14:41:11

 学习netty，优点：
   - 用于屏蔽网络编程底层的复杂，提供应用层的api
   使得业务与网络逻辑解耦，
   - 提供高并发高性能网络编程支持
## 1.1 netty入门
   了解原生的java socket api
   通过`ServerSocket`作为服务器，发送socket到客户端`Socket`
   其中`accpet()`方法是阻塞方法.
   缺点：
   - 长时间等待，线程休眠，浪费资源
   - 不用于多个socket客户端。
  
  了解`netty`的核心组件
  - Channel
  - 回调
  - Future
  - 事件和ChannelHandler
   
 ## 1.2 编写第一个netty客户端与服务器
 >2018年8月23日10:42:27
 ### 1.2.1 服务端
   - 至少一个`ChannelHandler`---- 该组件实现了服务器对
   从客户端接受的数据的处理，即它就是业务逻辑处理器
   - 引导(`ServerBootsStrap`) ---- 这是配置服务器的启动代码，至少
   ，它会将服务器绑定到了它要监听的连接请求的端口。
  ### 1.2.2 客户端
   1、 连接服务端
   
   2、 发送一个或者多个消息
   
   3、 对于每个消息，等待并接受从服务端返回
   
   4、 关闭连接
   
   与服务端相同，一个`ChannelHandler`处理客户端业务逻辑
   ，一个引导客户端(`BootStrap`)。
   
   ## 1.3 Netty的组件与设计
   > 2018年8月28日17:22:49
   - Channel --- Socket
   - EventLoop --- 控制流、多线程处理、并发;
   - ChannelFuture --- 异步通知
   
   ### 1.3.1 Channel 接口
   在java网络编程中，其基本构造的是Socket，Netty的Channel提供的
   api大大的降低了直接使用Socket类的复杂性。
   
   ### 1.3.2 EventLoop 接口
   